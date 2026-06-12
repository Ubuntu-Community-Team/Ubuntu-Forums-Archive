---
title: "Hoary on Mac Mini - From an Idiot's Perspective"
date: 2005-07-27
forum: Apple PPC Users
---

### Post by FuzzWuzzle on 2005-07-27
Completely and utterly new to the Linux world and having just barely broken myself in with Windows recently, I think I'm in over my head. Take in mind here that you're talking to a fifteen year old who has never opened his Terminal for anything beyond playing the occasional game of Nethack, vaguely knows how to install RAM, and only recently managed to master the keyboard without having to look at the keys. 

My problem is as follows. 

Using the Hoary Live CD, it seemingly 'Canot start the X Server (Your Graphical User Interface)' and that 'it is likely that it is not set up correctly'. It then throws me into various command lines, minus the cursor and the folders an idiot like me so desperately needs to do things like check his email and leaving me baffled.

My Hardware:
Mac Mini 1.25 GHz
256 megs stock RAM
hp pavilion f50 flat panel monitor
Generic Apple Keyboard
Generic Optical Logitech Mouse

It goes through the following steps: 
Detecting Hardware...
Loading Additional Components...  etc etc. all the way up to around...
Starting GNOME
Starting Message System Bus

Perhaps this error is exclusive to Live, but I wouldn't have a clue.

At this point it switches resolutions a few times and gives me the previously mentioned error. I need someone with a lot of time on their hands and a lot of patience to give me a step-by-step guide down to the smallest most insignificant detail (Think of a For Dummies book) if I can be expected to get through this. I'll learn. I just need a boost! If all else fails, can someone please give a kid some recommendations on where to get started with things like this?

---

### Post by ltmon on 2005-07-27
It seems that the Mac Mini is just a little to weird to have Ubuntu running perfectly out of the box.

It seems that to get it working you need to replace the file /etc/xorg.conf with a custom version (this will fix the graphics), and replace the kernel with a custom version (this will fix the sound).  Neither of these things are possible to do from the live CD, but can be done from the install version if you are willing to give it a try.  It actually isn't as hard as it sounds :)

You can get the customized files from this guy -> [http://ubuntuforums.org/showthread.php?t=22257](http://ubuntuforums.org/showthread.php?t=22257)

Cheers,

L.

---

### Post by FuzzWuzzle on 2005-07-27
I've looked into this and am not exactly clear on what to do. Am I replacing the files within Ubuntu itself, in which case I'll have to launch FireFox through command line alone or something of the sort, or am I replacing something within OS X? 

Sorry about all this.

---

### Post by ltmon on 2005-07-27
Ok, I'll see how much I can help .... sorry if you don't understand, some of this stuff is hard to word :)  I'm not too crash hot on all this stuff myself, especially on a Mac, but I'll see what I can do.

Quick answer: You are needing to replace a file in Ubuntu.  Since you are running off the live cd, you can't do this yet.

If you do install Ubuntu to your hard disk:

The file "/etc/X11/xorg.conf" (I got it wrong in my last post) is a file in Linux.  It is where Linux looks to start up it's graphical display.  Any file that is in the "/etc" directory is likely to be a system configuration file of some sort or another.

If this file does not contain the correct configuration for your system, you'll only get an error then a command line -- which is the error you got.  For most systems, you don't need to worry -- the installation process just autodetects everything for you.  Unfortunately for the Mac Mini it doesn't.

The live CD hardware detection is necessarily slightly different from the install cd hardware detection, so you may just be lucky to get it working if you install anyway.  It seems from various posts that this has worked for many people.

Now, if after all this you _do_ eventually need to get this guys xorg.conf file to help you out be sure to post back.  You can't actually launch firefox without this file being configured correctly.  It's easy enough to do, but there's way too much to digest in this post already.

CHeers,

L.

---

### Post by BSDDomi on 2005-08-02
[QUOTE=ltmon]It seems that the Mac Mini is just a little to weird to have Ubuntu running perfectly out of the box.

It seems that to get it working you need to replace the file /etc/xorg.conf with a custom version (this will fix the graphics), and replace the kernel with a custom version (this will fix the sound).  Neither of these things are possible to do from the live CD, but can be done from the install version if you are willing to give it a try.  It actually isn't as hard as it sounds :)

You can get the customized files from this guy -> [http://ubuntuforums.org/showthread.php?t=22257](http://ubuntuforums.org/showthread.php?t=22257)

Cheers,

L.[/QUOTE]

I cant complain...
I got the kernel and everything is working just fine now...sound works, firewire works, graphics ok, i can mount my hfs+ formatted ext. firewire drive, i have mac os x on a 80gb drive and ubuntu on the 40gb in a mac mini...the video performance could be better but oh well

 :grin: 

[http://www.dominique-werner.com/img/ubuntu_on_mac.jpg](http://www.dominique-werner.com/img/ubuntu_on_mac.jpg)

this screenshot shows an Ubuntu installation on a Mac Mini 1.25 GHz, 1 GB of ram with ext. firewire drive and iPod attached...

---

### Post by ltmon on 2005-08-02
Well done.... glad you persisted.

I guess video performance is always going to be a bummer until ATI ever releases a set of drivers for linux on PPC (or releases decent technical info on their cards, but now I'm really in fantasy land).

L.

---

### Post by marcosscriven on 2005-08-09
Hi

I've trawled the internet on how to get Ubuntu running on my Mac Mini.

All looked good until right at the end of the process it said 'registering documents'- then the screen went blank.

I rebooted the machine, and it looks like it's trying to boot into the graphical interface. From what I can gather, there's some issue either with the Mac Mini or the Apple Cinema 23" (1920x1200)

I tried booting from CD again, and typing 'rescue' - but ended up with a blank screen. I tried rescue video=ofonly, and found an option to mount a partition (4 in my case) and got a shell!

Then tried copying a working xorg.conf file but this is where it gets annoying!

When I type 'vi xorg.conf' I get a message saying the terminal is not found, defaulting to ANSI. No matter which terminal I set (out of the 'builtin' list it shows) I can't get a NEW LINE!!!! I've tried 'return' Ctrl-I, Ctrl-J - all sorts.

Tried 'o' and 'O'

Anyway - how do I just get the necessary files onto their? Do I have to mount a USB stick or something, and copy accross? I'm not sure how to do that.

complete n00b help much appreciated.

Marcos

---

### Post by ltmon on 2005-08-09
Try booting from your hard disk again, then when the screen goes blank hit ctrl-alt-f1.  

This should get you a text prompt that is more functional than the rescue prompt and allow you to edit the xorg.conf file.

Before you edit it type:

> sudo /etc/init.d/gdm stop

if using Ubuntu OR

> sudo /etc/init.d/kdm stop

if using Kubuntu

Once you've played with xorg.conf you can then do

> sudo /etc/init.d/gdm start

To test if it worked.

L.

---

### Post by marcosscriven on 2005-08-10
Thanks ltmon - I will try this tonight

The thing is, I feel a bit dumb for not finding out about this 'ctrl-alt-f1' option - where could I have found out this information myself?

Thanks

Marcos

---

### Post by ltmon on 2005-08-10
[QUOTE=marcosscriven]Thanks ltmon - I will try this tonight

The thing is, I feel a bit dumb for not finding out about this 'ctrl-alt-f1' option - where could I have found out this information myself?

Thanks

Marcos[/QUOTE]

I don't know... I think Ubuntu docs don't mention it specifically because the hope is that the graphical display will work first time for everyone.

I know about it because I used Linux from > 5 years back, when it was rare that anything would be autodetected properly :)  I still find it useful when Enemy Territory locks up hard on me, but other than that I've never used it in (K)ubuntu.

Ctrl-Alt-F1 to F6 are all different virtual terminals (a different login prompt for each one).  Ctrl-alt-F7 and above are your graphical displays (of which you have only one on F7 unless you manually start another one on a seperate display).

L.

---

