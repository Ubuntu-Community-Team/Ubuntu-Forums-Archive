---
title: "Can't play .aiff audio files even in Banshee"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-09-11
I want to both listen to and burn to CD some aiff files. None of my players will do them. 

Gnomebaker says "The plugin to handle a file of type audio/x-aiff is not installed." 

Serpentine says "The following file was not added:" [the file I was trying's name] "If you're having problems opening certain files make sure you have the GStreamer plugins needed to decode them."

They still say that even when I used synaptic to install gstreamer0.8-audiofile
That is described like this "AudioFile plugin for GStreamer
This GStreamer plugin enables the processing of audio data from formats
supported by libaudiofile including AIFF, AIFF-C, WAVE, NeXT/Sun,
BICS, and raw data."

So why doesn't anything read these aiff files? Is there more altering I need to do inside each program or something? MPlayer doesn't play them, nor Kaffeine, Rythmbox.

I thought I might be in luck with Banshee so I downloaded that. It was after that that I installed the above mentioned Gstreamer thing (and I have several of those mysterious Gstreamer things now). Nothing works. Am I missing some vital step? I feel like a bear trying to cook an Irish stew.

Justin

---

### Post by bodhi.zazen on 2006-09-11
See here:

[Restricted Formats](https://help.ubuntu.com/community/RestrictedFormats)

8)

---

### Post by woodlandjustin on 2006-09-11
I think most of that should have happened when I got automatix, shouldn't it? I read somewhere that the thing I needed was the Gstreamer thing I said above. I cannot understand, and everywhere I turn I see a blur of strange letters and numbers I cannot understand, making me disorientated. Can someone suggest to me how I can do it, in a way that I can understand? I'm not so dim but this mess of computer speak is feeling like a solid impenetrable wall.
Thanks
Justin

---

### Post by bodhi.zazen on 2006-09-11
Clear you head.

---

### Post by woodlandjustin on 2006-09-11
> **bodhi.zazen said:**
> Clear you head.

Well, though my head is now somewhat clearer I feel no closer to the solution. The page you pointed me to appears to not even mention .aiff files. So I'm not sure how it is meant to help me.

On that page however are these instructions:
> 
How to Make Things Work in a Hurry

    *

      Ubuntu 6.06 LTS (Dapper Drake)
          o

            Install the following packages to play most proprietary formats using Totem and Rhythmbox, which both come with Ubuntu.
          o

            gstreamer0.10-ffmpeg
          o

            gstreamer0.10-pitfdll
          o

            gstreamer0.10-plugins-bad
          o

            gstreamer0.10-plugins-bad-multiverse
          o

            gstreamer0.10-plugins-ugly
          o

            gstreamer0.10-plugins-ugly-multiverse

            Since the version of Totem that comes with Ubuntu doesn't yet play DVDs, the list below also includes packages for the GXine player, which does. For playing encrypted DVDs, refer to DVD section
          o

            gxine
          o

            libxine-main1
          o

            libxine-extracodecs
          o

            w32codecs 

Every one of those things is *already installed* on my system (plus quite a few more of those gstreamer things), except for gxine. So I installed that too now, and it still doesn't make any difference.

Are .aiff files really so rare that no-one knows how to play them? They are common on macs right?

Justin

---

### Post by bodhi.zazen on 2006-09-11
Thank you.

I am sorry you are so frustrated, but it is difficult to read your posts.

Try sox. Install via synaptic or CLI:
```
sudo aptitude install sox
```

8)

---

### Post by woodlandjustin on 2006-09-12
> **bodhi.zazen said:**
> Thank you.

I am sorry you are so frustrated, but it is difficult to read your posts.

Try sox. Install via synaptic or CLI:
```
sudo aptitude install sox
```

8)

Okay so I just installed that but when I look up what it actually is, it says:
"SoX is a command line utility"
and that sounds not good for me. I want to be able to click files and they just open, or drag and drop them into a player, or open a CD burning program and just burn these things to CD. Surely there is a way to do that? The last thing I actually want to be doing is typing code into a terminal. I am not a programer or anything like that.

(By the way, why are my posts difficult to read? Too vague? If you tell me why I will try to improve.)
Thanks
Justin

---

### Post by bodhi.zazen on 2006-09-12
Well, I can read them.....

It is just than you sound a little frustrated and I find it difficult to communicate with frustrated people.

> ....read somewhere that the thing I needed was the Gstreamer thing I said above. I cannot understand, and everywhere I turn I see a blur of strange letters and numbers I cannot understand, making me disorientated.

This is not a description of a problem and makes it seem you are unwilling to read any potential solution. The "blur of strange letters and numbers" is what I need to understand to help you.

At any rate, water under the bridge, let's not dwell on it as this is not the task at hand.

You may also need libsndfile install via synaptic or 
```
sudo install libsndfile
```

You may also want to try installing xmms. It is an older, but very functional player....

Now try to play a file and let me know if you still get error messages. Keep in mind we may need to configure a few things yet....

---

### Post by bodhi.zazen on 2006-09-12
See if this helps

[Getting the Most from XMMS with Plugins](http://www.linuxjournal.com/article/7273)

---

### Post by woodlandjustin on 2006-09-12
Just checked that in synaptics and it says libsndfile1  version 1.0.12-3 is already installed. I don't understand what it is. Does it tell you enough that it was always there already?

By the way Audacity can play these files fine (I just found that out). Of course that doesn't really help. What actually is going on is that a friend recorded 20 lps to his Mac. As he has no CD burner I put all that data, as .aiff files, onto my computer. So I need to burn it. So I need a CD burning program that can do that. Actually playing the files is of secondary importance. I need to make audio CDs. I thought I just need a "plugin" as that is what the players and burners said as an error message. I thought maybe the one I already did was meant to do it:

>  gstreamer0.8-audiofile
That is described like this "AudioFile plugin for GStreamer
This GStreamer plugin enables the processing of audio data from formats
supported by libaudiofile including AIFF, AIFF-C, WAVE, NeXT/Sun,
BICS, and raw data."


But it didn't. Was I wrong to think that? Or, was I wrong to simply get synaptics to instal it? Was it meant to be a more complicated procedure? (I have never done something like this before by the way.)

Thanks
Justin

---

### Post by bodhi.zazen on 2006-09-12
LOL :lol:

Now I understand the title of this thread at last "**Can't play .aiff audio files** even in Banshee" LOL :lol:

What, not satisfied you can now play, just have to burn also.

Well I am in a god mood and will try to help. I use K3b.

"Making a music CD is exactly the same, except you choose "Audio CD Project," and instead of selecting a whole folder at once, place each music file (mp3, wav, aiff, ogg) individually on it so you can set the order in which they'll play on the finished CD. To move files around within the "Project" listing, "drag" them with the mouse while holding the left mouse button and release the button where you decide they best fit in your custom-made playlist."

Try this:
[K3b](http://www.novell.com/coolsolutions/feature/2746.html)
[K3b Second site](http://harmonyservice.com/content/view/23/40/)

When K3b starts you will get an error message
"cdrecord will be run without root privileges
It is highly recommended to configure cdrecord to run with root privileges. Only then cdrecord runs with high priority which increases the overall stability of the burning process. Apart from that it allows changing the size of the used burning buffer. A lot of user problems could be solved this way. This is also true when using SuSE's resmgr.
Solution: Use K3bSetup to solve this problem."

**Ignore it** (click "Don't show again box and then "Close").

Let me know if you need further assistance,

---

### Post by woodlandjustin on 2006-09-12
> **bodhi.zazen said:**
> LOL :lol:

Now I understand the title of this thread at last "**Can't play .aiff audio files** even in Banshee" LOL :lol:

What, not satisfied you can now play, just have to burn also.


Well, the first sentance of my first post was "I want to both listen to and burn to CD some aiff files." ...
Actually I had thought of the playing and burning issues as two manifestations of the same problem. But when it comes down to it, burning is more important for me (though it would be nice if my machine could play them too!!) Sorry for any confusion.

> **bodhi.zazen said:**
> 
Well I am in a god mood and will try to help. I use K3b.

"Making a music CD is exactly the same, except you choose "Audio CD Project," and instead of selecting a whole folder at once, place each music file (mp3, wav, aiff, ogg) individually on it so you can set the order in which they'll play on the finished CD.

I had already installed K3b, and it gives this message when I try to add even a single track:
"Unable to handle the following files due to an unsupported format:"

> **bodhi.zazen said:**
> 
When K3b starts you will get an error message
"cdrecord will be run without root privileges[...]

I have no error message when I start K3b. Or is it only the first time you start it? If so can't remember what happened the first time.

By the way I still cannot play these files! Only with Audacity, but that is an editor not a player right? No play list, and each track takes a whole minute about, to load, etc. Not a solution.
Thank you
Justin

---

### Post by bodhi.zazen on 2006-09-12
Sorry my friend. You seem to have all the dependencies required to burn.

The only other thought I have, although I am not hopeful it will work, is to re-boot.

The only other link i could find was this:

[Build K3b from source](http://ubuntuforums.org/showthread.php?t=86698).

---

### Post by woodlandjustin on 2006-09-12
> **bodhi.zazen said:**
> Sorry my friend. You seem to have all the dependencies required to burn.

The only other thought I have, although I am not hopeful it will work, is to re-boot.

The only other link i could find was this:

[Build K3b from source](http://ubuntuforums.org/showthread.php?t=86698).

I restarted my system and still, doesn't work. I have these players:

MPlayer
Kaffeine
Rythmbox
Banshee
Gxine

and these burners:

Gnomebaker
Serpentine
K3b

I have not had problems with WAV or mp3.
Anyone?
Justin

---

### Post by 3rdalbum on 2006-09-13
```
sudo apt-get install sox
```

Or install Sox in Synaptic Package Manager. Then:

```
sox infile.aif outfile.wav
```

Where infile.aif is your input file, and outfile.wav is the file you want to be created. When you've got your AIFFs converted to WAVs, Serpentine or K3B should recognise them.

I'm afraid, unless you want to open and convert using Audacity (slow), the command-line is the only way. But don't be scared of the terminal; the command I've given you is easy, and very quick.

Sox definately works. I've tried it myself.

---

