---
title: "Ipod and ubuntu 13.10, do I format before?"
date: 2014-01-09
forum: Apple Hardware Users
---

### Post by lizpy66 on 2014-01-09
I had to switch to ubuntu after windows 8 basically blocked itself out on christmas  day but since then I haven't able to add music to my ipod, it's even made some songs not play thought that might be cause it was plugged into my ps3?? Is there anyway to add music to my ipod? I've heard some say I need to format on windows which I can do on my sister's laptop but I want to know before I do that will work for sure. I'm on ubuntu 13.10 in case you didn't notice the title. I've tried banshee and rhythmbox

All help is appreciated :)

---

### Post by sandyd on 2014-01-10
What IPod model/generation is this?

Some models are supported in Ubuntu, some are not

---

### Post by ehsanoo on 2014-01-10
If you have a jailbroken iPod Touch, then you can add music to your iPod using  FTP or applications like iFile, and there are applications like Bridge(I  haven't had it myself) or even iFile itself that add music files to  your iPod music library. (they do always have problems with file tags,  tough! at least track number was always 1 as I remember!)

Some  old devices are supported by Banshee, Rhythmbox, gtkpod, but I could  never sync even my 2011 iPhone 4S with any application other than  iTunes! But If your device is even older, there might be a way :)

And BTW what iOS version are you running? Don't you have problems mounting your iPod on Ubuntu? and most importantly, as sandyd mentioned, what model and generation is it?

---

### Post by lizpy66 on 2014-01-10
5th generation I believe and its not ios thingy so it should work right? Even when I delete stuff off of it through ubuntu it will still show on my ipod but it will crash the ipod if I try to play that song unless those songs were already like that before and I didn't notice because I tried it on songs I haven't listened to in awhile

---

### Post by kostkon on 2014-01-10
> **lizpy66 said:**
> 5th generation I believe and its not ios thingy so it should work right? Even when I delete stuff off of it through ubuntu it will still show on my ipod but it will crash the ipod if I try to play that song unless those songs were already like that before and I didn't notice because I tried it on songs I haven't listened to in awhile
Yes, it should work, even if it is mac formatted. Could you provide some more information? For example, what happens when you try to add songs using Rhythmbox?

---

### Post by lizpy66 on 2014-01-10
So I need to format on windows or mac?  It just says its added but when I eject and look at my ipod they aren't on there

---

### Post by lizpy66 on 2014-01-11
oh and I re connect it, it acts as if no changes were ever made so it won't display the added songs when re connected after the eject.

---

### Post by kostkon on 2014-01-12
> **lizpy66 said:**
> So I need to format on windows or mac?  It just says its added but when I eject and look at my ipod they aren't on there
> **lizpy66 said:**
> oh and I re connect it, it acts as if no changes were ever made so it won't display the added songs when re connected after the eject.
I'm not sure why that happens.
Do you umount it (right clicking on its icon and selecting "umount" or "eject") before unplugging it?

There is also another option, [Floola]("http://floola.com/"), that's the one I use for my 5.5gen Ipod, because it supports adding videos.

---

### Post by lizpy66 on 2014-01-12
Yeah I always unmount it properly. I'll try Floola if it works then that would be awesome, if not still thanks for taking your time to answer :)

---

### Post by kostkon on 2014-01-13
> **lizpy66 said:**
> Yeah I always unmount it properly. I'll try Floola if it works then that would be awesome, if not still thanks for taking your time to answer :)
And don't forget there is [gtkpod]("https://apps.ubuntu.com/cat/applications/gtkpod/") in the repos.

---

### Post by PDA1 on 2014-01-13
For me Gtkpod only works on Ubuntu 10.04 and it works perfectly.

On 12.04 many have said it's "broken". It'll install but crashes and messes up file structure.

I'm using an iPod Classic 160g (with color video).

No one....let me repeat that...no one really knows how to get an iPod to work with Linux beyond Ubuntu 10.04 and those who say they do either can't or won't explain how they exactly did it.

Many suggest "PlayOnLinux" with Wine to use iTunes. Doesn't work for me or many other people and, yes, I've tried it with itunes 7, 10 and 11.

Most people suggest an iPod handling program with this caveat, "you can try program X...though I've never used it". So the best you'll get is hours of frustration.

There's a post on here where a guy says he's got Gtkpod to work for 12.04- [http://ubuntuforums.org/archive/index.php/t-2028977.html](http://ubuntuforums.org/archive/index.php/t-2028977.html)

So far I can't get his method to work.

Good luck

---

### Post by hansdown on 2014-01-13
Hi PDA1.

My 160 gb ipod classic auto mounts on xubuntu 13.10.

I can add files, play files, and do every thing on xubuntu 13.10.

---

### Post by lizpy66 on 2014-01-13
I tried gtkpod too and it didn't work, none seem work but interestingly enough artwork from an album I put on my ipod using one of the multiple applications, I'm thinking banshee, popped up on the ipod on a different band's album so it copied the artwork but not the music itself. It's not a space issue due to the fact I had deleted stuff to make room which didn't work either. I tried floola but didn't have enough room for that this time so I'm wondering if I format it on my friend's windows 7 computer then use it on ubuntu 13.10 will this work? I don't want to format it without knowing it for sure but unfortunately I might have to. Thanks again for all the help :)

---

### Post by PDA1 on 2014-01-15
The only way I got GtkPod to work beyond 10.04 is to use it with VirtualBox as mentioned here-

[http://ubuntuforums.org/showthread.php?t=2199542&highlight=gtkpod+virtualbox](http://ubuntuforums.org/showthread.php?t=2199542&highlight=gtkpod+virtualbox)

If someone on here says, "I've never done it before but try [name some program]...it should work." DO NOT waste your time- probably 99% of the time it won't work. My iPod Classic has over 4,000 songs and videos on it and messing up the file structure and creating many duplicates is what happened when I used Rhythmbox, Banshee etc. to try and manage my iPod. I've tried them all and they simply don't work and no one I've talked with knows how to make them work.

I hate windows and hate iTunes even more so using them isn't an option- unless my iPod is wrecked and needs all of the old files put back on it (which has happened only 2 times).

I wish the creator of GtkPod would fix the thing to work with no troubles on newer versions of Ubuntu. It really is (was) the easiest and best program for iPods.

---

### Post by PDA1 on 2014-01-15
Whoops...sorry folks. Double post.

---

### Post by PDA1 on 2014-01-15
> **hansdown said:**
> Hi PDA1.

My 160 gb ipod classic auto mounts on xubuntu 13.10.

I can add files, play files, and do every thing on xubuntu 13.10.

You got it working with Xubuntu?

Using what program and what configuration?

---

### Post by lizpy66 on 2014-01-15
I've thought about a virtualbox but worried about using that, not sure if there is a risk to using it or not haha I'm new to all of this

---

### Post by PDA1 on 2014-01-15
Installing VB for me was another huge pain-in-the-neck. But as I mentioned in my linked post that was how I did it. It (VB running Ubuntu 10.04) and GtkPod work perfectly. I like to use FFMPEG (another horrific program to install, learn how to use and understand) and have various codes I use to convert videos so that they'll play on my iPod.

I'm a computer user and not a programmer.

---

