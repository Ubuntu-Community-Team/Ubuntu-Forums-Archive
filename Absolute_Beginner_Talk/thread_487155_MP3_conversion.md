---
title: "MP3 conversion"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by kolhoznik on 2007-06-28
The second problem I am having is getting Sound Juicer to rip an convert to MP3 format.  Surely there is an easy fix that I am overlooking.

---

### Post by kpkeerthi on 2007-06-28
> 
The latest version of Sound Juicer tells you how to encode mp3's in its help menu. A few clicks and you should be away!


For more information [see here]("http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html")

---

### Post by kolhoznik on 2007-06-29
As I was looking at the above link the author mentioned the first step was to install gstreamer8.0-mad does this come with Ubuntu or do I need to find this somewhere.

---

### Post by swisscow on 2007-06-29
For gstreamer, look in Synaptic - the package is "gstreamer0.8-mad"

---

### Post by kolhoznik on 2007-06-29
I have followed the above directions in the link, but under Sound Juicer Preferences-Output it does not give my new mp3 profile as an audio out put option.  Thanks for all the help

---

### Post by lintoon on 2007-06-29
I'm no expert but you could try installing LAME.  Hopefully someone can confirm or correct this advice.

---

### Post by buuntuu! on 2007-06-29
gstreamer0.8-mad was for mp3 playback under ubuntu - release 5.10, 
what you would need to install can be found[here]("https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58").
happy ripping! (you know that .ogg is better, don't you?)

---

### Post by Bluecube on 2007-06-30
I've done all the above, followed all the instructions, etc but still can't choose to encode as MP3. I'm puzzled! There doesn't seem to be any reason why!

---

### Post by RomeReactor on 2007-06-30
Hi. **Bluecube**, you can try installing **soundconverter**; I think when you go into it's preferences, it has a blue prompt asking if you want to enable ripping to mp3. You can find soundconverter through **Add/Remove** or **Synaptic**.

---

### Post by dkaddict on 2007-06-30
You can try Automatix. It has an option to install all of the restricted format stuff one needs. Well it did the last time I tried it.
[http://www.getautomatix.com/](http://www.getautomatix.com/)
Is where it's at. I haven't used it for a while now but it helped me out when I first tried to get mp3 etc going.
I was a bit sceptical around .ogg to begin with (cheers MS) but will always rip tunes as .ogg now. Mucho better quality than mp3.

Persistence helps solve most problems.

peace

dk

Just had a gander at the automatix I have and it looks like those codecs are still on their server. I found the mp3 option had been installed in Sound Juicer for me so only had to select it from the drop down context menu to rip some trax.

Install 'AUD-DVD Codecs' and 'Multimedia Codecs' (doh). There are other goodies on there like the streamripper and streamtuner. I had never managed to record a stream before I used Ubuntu. Still working on recording 'real audio' streams. I have read that it can be done.

---

### Post by dkaddict on 2007-06-30
Sorry m8. I don't mean to hijack your thread or nothing.

I was just looking at the info about 'Rubyripper'.

Is 'Rubyripper' any good? What is the difference between 'Rubyripper' and 'Soundjuicer'? Surely a rip is a rip is a rip?

???????????????

dk

---

### Post by RomeReactor on 2007-06-30
> **RomeReactor said:**
> Hi. **Bluecube**, you can try installing **soundconverter**; I think when you go into it's preferences, it has a blue prompt asking if you want to enable ripping to mp3. You can find soundconverter through **Add/Remove** or **Synaptic**.

I just remembered that soundconverter (as its name implies) only converts between different formats, but doesn't rip audio from a CD. Sorry about that (I don't know what I was thinking then).

---

### Post by wallacetheweasel on 2007-07-04
Rubyripper does indeed encode into mp3, though you should be able to do that with Sound Juicer too.

The thing with Rubyripper is its sophisticated error detection mechanism.  Basically, it guarantees a good rip to the extent that audiophiles often demand.

To find out more: [http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

**Edit:**

I know you apologized for it, but you still are pretty much hijacking the thread.  I didn't realize that that question is unrelated to the original query.  My apologies for responding to that here.  In the future, dkaddict, if you have a question like that you should start a new thread, not just apologize for hijacking this thread.

---

