---
title: "Disable boot up sound / dong with no OS/X"
date: 2010-02-04
forum: Apple Hardware Users
---

### Post by stu31 on 2010-02-04
Hello,
  I just successfully installed ubuntu on a old (~2006) macbook pro. 

Things seem to be working OK so far, BUT I can't figure out how to turn off the annoying DONG at boot up. 

This is not the same as the ubuntu login sound that troubles people as well. 

This happens at boot (via EFI?). There's various solutions on mac forums, none of which work with ubuntu installed:

- hold F3 (mute) when booting up. Still makes sound.

- install proprietary app for OS/X - obviously not going to work.

- mute sound before turning off - doesn't work.

- just suspend, never turn off - ubuntu can't wake up from suspend, and it's a laptop (battery life).

I would think the next step would be to try fiddling around with rEFIt, but I'm not too sure about that route.. I haven't seen anything about rEFIt controlling the volume on boot online.

I'd like to use this in a fairly quiet office environment, but this sound is horribly loud and annoying.

-stu

---

### Post by linuxopjemac on 2010-02-05
I am not sure, just an idea, to boot from a MacOSX CD, to turn off the volume and to then boot into Ubuntu ?

---

### Post by tom4everitt on 2010-02-05
That sound is basically hardwired into the firmware (don't make go into detail on this, its all I know) so I don't think anyone outside apple knows how to disable it. 

When OS X is installed its usually very easy to turn it off, you just mute the sound before shutting it down (or find an app that does it for you). So I would say your easiest option is to make a partition for os x, install it on that partition, mute the sound, shut down, remove the os x partition. Not that it is an easy option, and neither is it guaranteed to work :D

---

### Post by oswaldkelso on 2010-02-06
You could probably turn it off in open-firmware. Not a good idea as it informs you of hardware problems.

1 beep = no RAM installed
2 beeps = incompatible RAM types
3 beeps = no good banks
4 beeps = no good boot images in the boot ROM (and/or bad sys config block)
5 beeps = processor is not usable.

[http://www.computing.net/answers/mac/beeping-soundopen-firmware/10279.html](http://www.computing.net/answers/mac/beeping-soundopen-firmware/10279.html)

---

### Post by tom4everitt on 2010-02-07
> **oswaldkelso said:**
> You could probably turn it off in open-firmware. Not a good idea as it informs you of hardware problems.

1 beep = no RAM installed
2 beeps = incompatible RAM types
3 beeps = no good banks
4 beeps = no good boot images in the boot ROM (and/or bad sys config block)
5 beeps = processor is not usable.

[http://www.computing.net/answers/mac/beeping-soundopen-firmware/10279.html](http://www.computing.net/answers/mac/beeping-soundopen-firmware/10279.html)

Interesting. And I assume the "beep" sound is different from the "dong" sound? Don't think I've ever heard it.

---

### Post by oswaldkelso on 2010-02-07
Now that is a good question. I was refering to the boing sound :)

---

### Post by stu31 on 2010-02-14
Hello!

  Just wanted to thank everyone for their replies, and post what I eventually ended up doing: re-installing OS\X and using the sound prefPane application that is posted about on numerous Mac forums.

This does appear to be the only way: I looked into rEFIt, but it didn't seem promising as a way to adjust the sound. 

And this is a dong or a boing, but not a beep :)

I am aware that it tells you about how far EFI got: just like the old POST beeps, but the benefit just isn't worth the cost of annoying everybody around me.. It would make more sense to me if it would only make noises when something was wrong.. Or print out E-F-I like GRUB.

Thanks again! 

Now to re-install Ubuntu the right way... instructions first ;)

take care,
  -stu

---

### Post by JackMahon on 2010-02-15
> **tom4everitt said:**
> That sound is basically hardwired into the firmware (don't make go into detail on this, its all I know) so I don't think anyone outside apple knows how to disable it. 

When OS X is installed its usually very easy to turn it off, you just mute the sound before shutting it down (or find an app that does it for you). So I would say your easiest option is to make a partition for os x, install it on that partition, mute the sound, shut down, remove the os x partition. Not that it is an easy option, and neither is it guaranteed to work :D


There is free software available on VersionTracker.com which allows you to disable the Mac startup chime.

---

### Post by tom4everitt on 2010-02-15
> **JackMahon said:**
> There is free software available on VersionTracker.com which allows you to disable the Mac startup chime.

Really? I believe you when I see a link :)

---

### Post by linuxopjemac on 2010-02-15
he probably means osx....

[http://www.versiontracker.com/php/qs.php?mode=basic&action=search&str=startup+chime&srchArea=macosx&submit=Go](http://www.versiontracker.com/php/qs.php?mode=basic&action=search&str=startup+chime&srchArea=macosx&submit=Go)

---

### Post by tom4everitt on 2010-02-15
Allright.. If people were actually to read the thread before they post we would save ourself a lot of confusion :) (The OP obviously knew about those.)

---

### Post by brteag00 on 2011-08-17
I know this thread has pretty much died out, but I found an answer on the ArchLinux Wiki at [https://wiki.archlinux.org/index.php/MacBook](https://wiki.archlinux.org/index.php/MacBook) --

1.  Reboot with an OSX installation disc
2.  Start the Terminal
3.  Issue the command "# /usr/sbin/nvram SystemAudioVolume=%01"

I can confirm that this works on a late-2010 Macbook Air and Snow Leopard.

---

