---
title: "fuzzy rainbow title"
date: 2008-01-28
forum: Apple PPC Users
---

### Post by brymway on 2008-01-28
sigh

I hate being a newbie but I really want this ubuntu to load on my emac G4.  I press c with ubuntu 7.10 or 6.10 and it comes up to the yaboot.  I press enter, it goes white, then black then the ubuntu title and the nightrider car like cursor going back and forth comes up only it's fuzzy and rainbow colors, then it freezes.  I'm new so I don't know what all the commands are that you tell us to type in are.  Can anyone suggest something?

---

### Post by stream303 on 2008-01-29
You might get a lot farther using one of the "alternate" install disks rather than the live-cd.  However, nothing's perfect, and you may end up having to edit some configuration files manually without the aid of a gui to fix something.

Do you still have OSX available for booting?  You might want to get a little bit of practice by calling up the terminal and editing some poems or whatever with the nano editor, since unix shells and the nano editor are also available with ubuntu by default.

So give the alternate install a shot - but beware that you may end up blowing out whatever you already have on your hard drive and starting from scratch, so back up what is important to you.  If you have a working OSX on it, be sure you have the OSX installation disks, if it is important that you get back to it.

I'm not trying to put you off trying, and we'll certainly do what we can, but I'm just being honest if you are totally new to configuring your own system via text files.

If you are interested in learning the command line, you picked a good project!

---

### Post by jeffus_il on 2008-01-29
Here is a good page to help you select boot options when you have a problem installing.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by VidiotGeek on 2008-01-29
Ditto what everyone has already said. I'm new myself so I can't offer much command line expertise to assist but I did want to reply to this to say that I have the same issue with the boot graphic. I think it's refereed to in the system as the "usplash" screen. 

My instal works fine but the splash always looks jacked up. I've also installed several different packages that change the usplash, from the original Ubuntu to Edubuntu & most recently Ubuntu SE. All of them share the same strange color errors. So just know that it's not an uncommon problem. Maybe we'll have a fix on the forum soon.

---

### Post by simplebeep on 2008-02-02
It seems from what I've read that eMac's are notorious for graphics problems in Linux.  I myself have tried three different distributions, and all of them have given up upon trying to load a GUI.  On my eMac, the screen goes white-and-black again, as described above.  It shows the little Ubuntu splash screen with the bouncing orange square...  then I get the dreaded busybox :( .  From what I can tell, the graphical boot options menu doesn't load because it can't find my monitor/graphics card :confused: .  It falls back on the little dinky shell called Busybox.  I can't really get past it except by holding the power button until my computer shuts off.

Unfortunately, I can't give any help.  I'm here to find a solution.  I'm an absolute newb too; I suspect we're not alone in that respect.

Maybe for you, the liveCD found your monitor but couldn't send proper data to it (hence the rainbow fuzzies).  On mine, it can't find the monitor at all.  Different internal setups were used throughout all five-or-so generation of eMac's; that makes it all the more confusing.

--
Simple Beep
eMac, early 2003
Ubuntu 7.10

---

### Post by stream303 on 2008-02-02
> **simplebeep said:**
> It seems from what I've read that eMac's are notorious for graphics problems in Linux.

They need just a quick edit or two.  Check out what OswaldKelso wrote in this thread about Emacs and follow his link:

[http://ubuntuforums.org/showthread.php?t=650778&highlight=emac](http://ubuntuforums.org/showthread.php?t=650778&highlight=emac)

Personally, I'd download and run the "alternate" install rather than the live-cd.  Burn the iso image at the slowest speed possible on good media.  It's worth it to burn at 1x or 2x.

Use "nano" as a text editor if you are new to editing on the commandline.  Lets see how far this gets you and let us know!

---

### Post by simplebeep on 2008-02-03
Well, I'm not exactly sure what the problem is.  But I do know that my live cd has difficulty getting to a full shell; the minimal one has no *nano*, text editor, or even *sudo*!

In any case, I got it to work.  Or rather, I got a different distribution to work.  opensuse.org has a great gnome distribution.  It's not quite as good as Ubuntu, but it works just fine.

-- Simple Beep
an original Macintosh Sound

---

