---
title: "So...is there a working alternative to Windows Media Player?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by bigclaybear on 2007-07-14
I'm looking for something that will let me play streaming videos online that require either windows media or quicktime. Thus far I haven't been able to find one. I've found flash and Java for Ubuntu, which is good, but some of the sites I used to check with Windows XP just won't let me watch now, and that's just disappointing. Any help?

---

### Post by LinuxNathan on 2007-07-14
No. That's why it's called "Windows" media player. Usually the linux distribution has one installed for you. Like Mandriva linux gave me one that I can't remember. Roflz.


- Nathan:)

---

### Post by felicity on 2007-07-14
This may work for you:
```

sudo apt-get install totem-gstreamer-firefox-plugin

```

---

### Post by The Seeker on 2007-07-14
I'd recommend mozilla-mplayer.

```
sudo apt-get install mozilla-mplayer
```

---

### Post by crimesaucer on 2007-07-14
I like this one: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28xine-ui_with_DVD_menus_support.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28xine-ui_with_DVD_menus_support.29)

and for music: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Music_Manager_and_Player_.28Exaile.21.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Music_Manager_and_Player_.28Exaile.21.29)

---

### Post by Hendrixski on 2007-07-14
Rhythm box may play a lot of them if you have the right codecs installed.  By the way, Microsoft doesn't want you to have them, they want you to pay them to be able to watch video anywhere.  Installing the codecs is simple  just go to [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) and read the part about installed multimedia codecs.

---

### Post by Hendrixski on 2007-07-14
by the way, since you're new I thought I'd give you a propper welcome... from the heart.

**WELCOME TO THE COMMUNITY!**
We're all here to help new Ubuntu users because we love ubuntu, we love the freedom it gives us, and we want to share our joy with others. You'll love it too and before you know it you'll be here helping out other newcomers.

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too!  Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on these forums.  If dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by cytutchi on 2007-07-15
I have installed Mplayer but what i get is the sound but no video!
It is displaying information like connecting to the server n loading n stuff like that n then i get the sound but not the video! :/
Any suggestions?

---

### Post by arashiko28 on 2007-07-15
Install VLC and its mozilla plugin, it works fine for me.;-)

---

### Post by techno-mole on 2007-07-15
have you tried the multi media how to at the top of this forum ? i know its for fiesty, but it would probably work on other versions, i found that this was all i needed to do to get streaming and other stuff to work.
ive also found an application called songbird, which i think is really good.
cheers.

---

### Post by bns on 2007-07-19
I've tried about everything there is, and VLC works the best for me.  I've heard some other people say the same thing, so...

---

### Post by jimbob on 2007-07-19
Cytutchi: > I have installed Mplayer but what i get is the sound but no video!

Try right-clicking on the mplayer window while the audio is playing and select Preferences->Video and click on X11.   Stop mplayer and restart and see if you get any video.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by fourthdimension on 2007-08-06
> **bns said:**
> I've tried about everything there is, and VLC works the best for me.  I've heard some other people say the same thing, so...

So how do you install the VLC plugins for firefox?

---

### Post by Mr. Svinlesha on 2007-08-06
I've installed Songbird but don't really like it.

How do I unistall it?

---

### Post by Seisen on 2007-08-06
> **fourthdimension said:**
> So how do you install the VLC plugins for firefox?

```
sudo apt-get install mozilla-plugin-vlc
```

> I've installed Songbird but don't really like it.

How do I unistall it?

How did you install it?

---

### Post by Mr. Svinlesha on 2007-08-06
**Seisen**:

I downloaded it manually from the Songbird website, and then installed it with a terminal command:

> tar xzvf Songbird_0_2_5_linux-i686.tar.gz

Except that I installed it in a different folder.

---

### Post by fourthdimension on 2007-08-06
Thanks!

---

