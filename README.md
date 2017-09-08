# Xamarin-Plugins
Cross-platform Plugins for Xamarin and Xamarin.Forms

This branch by Olivier Dahan try to solve 2 problems with Android and the package author does not seem to react to those issues :
1- The plugin does not work and Android 4.x
2- With Android player stop to work after around the 15th/20th times

Plan for this fork : solve problem 2 in priority. Then solve problem 1 if possible.
There is a proposition by a user for solving problem 1 but it seems to kill a player once playback is finished, this is not the good solution. I'll try to find something else.

At this times I just forked the project, there is no difference with original. Once modification will have been pushed to Git I'll modidy this text.

Of course if you have any idea or proposal to solve these problems you're welcome !

## SimpleAudioPlayer
SimpleAudioPlayer plays audio data as a stream. This allows you to store audio data in a portable class library and play it on all supported platforms.

### Public Properties

**Duration**: length of audio in seconds

**CurrentPosition**: current playpack position in seconds

**Volume**: volume of audio between 0 and 1

**Balance**: balance between left and right as as double, -1 is left only, 0 is both, +1 is right only

**IsPlaying**: is the audio currently playing

**CanSeek**: can the playback position be updated

### Public Methods

**Load(Stream audioStream)**: load a compatible (wav, mp3, etc) audio from a stream

**Load(string fileName)**: load a compatible audio file stored in the executing platform project

**Play()**: play the currently loaded audio 

**Stop()**: stop playback and reset current position to start (0)

**Pause()**: pause playback (use Play() to resume)

**Seek(double position)**: seek to a specific location in the audio (in seconds)


### Example
Coded in the shared PCL using the Xamarin.Forms dependancy service
with **mysound.wav** stored in the PCL as an **Embedded Resource**
```
ISimpleAudioPlayer player = Plugin.SimpleAudioPlayer.CrossSimpleAudioPlayer.Current;
player.Load(GetStreamFromFile("mysound.wav"));
player.Play();
```

Or to load multiple instances
```
var player1 = Plugin.SimpleAudioPlayer.CrossSimpleAudioPlayer.CreateSimpleAudioPlayer();
var player2 = Plugin.SimpleAudioPlayer.CrossSimpleAudioPlayer.CreateSimpleAudioPlayer();
...
```

For more examples see the **Samples** folder or check out
https://github.com/adrianstevens/Xamarin-Forms/tree/master/DrumPad2
