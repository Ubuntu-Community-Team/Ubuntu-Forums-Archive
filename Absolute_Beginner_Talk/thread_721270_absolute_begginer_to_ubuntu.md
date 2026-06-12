---
title: "absolute begginer to ubuntu"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-11
hi! I'm an absolute beginner to ubuntu . Infact I haven't even installed it on my pc. All this while I have been using windows and i just thought it would be cool to try out linux. 
this is my questoin. 
suppose that i have downloaded and burned the installation CD.
I already have widows XP professional on my pc. and my hard drive is partitioned into two parts.
Can i install linux on the other partition without formatting my entire hard disk and without using another external hard disk. I dont want to uninstall windows. I want to have a so called "Dual boot system". 
can i achieve this without using an external hard drive or without formatting my disk?

---

### Post by PmDematagoda on 2008-03-11
Yes you can, just instruct the Ubuntu partitioner to use the second partition and the rest will be taken care of.

Just make sure that you select the right partition otherwise Windows along with your important files might get erased.

---

### Post by scragar on 2008-03-11
yes, during the installer it will ask where you want to install it offering a variaty of choices. One of them should offer to erase over your spare partition, if not do not fear, choose manual and set it's mount point to ```
/
``` and tick the little format box.

---

### Post by LeAstrale on 2008-03-11
unless the two partitions are the exact same size (which i highly doubt is likely) just make sure that you back up ALL important data before doing anything on partition level, because if you get it wrong it can be extremely hard to get the data back again. When all this is said it isn't that hard to do the install.


EDIT: if you have 2 computers available i can guide you through the partitioning on IRC. #ubuntuforums-beginners @ freenode.net (im available there for the next few hours)

/Astral-1

---

### Post by jan quark on 2008-03-11
check out this guide:

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by rockin_goliath on 2008-03-11
First of all, welcome to Ubuntu!

It is totally possible to do a dual boot with your current setup. When you click "Manual" on the partition selection window in the installer, make your partitions look similar to those shown in the screenshot i posted. Be sure that the "format" check next to your ntfs partition is UNCHECKED if you don't want to loose your data. You're swap partition should be about twice the size of your memory.

---

### Post by mahela007 on 2008-03-11
hey guys! Thanks for all those answers. really helpful. just one more question. what sort  of software comes with ubuntu 7.10 (hardy heron)?
I mean in windows I got ms word, excel, windows medial player ets...
what sort of software comes with ubuntu 7.10?

---

### Post by hyper_ch on 2008-03-11
> **mahela007 said:**
> I mean in windows I got ms word, excel, windows medial player ets...
what sort of software comes with ubuntu 7.10?
None of that what you paid for in Windows... you'll have instead OpenOffice Suite, quite a few different media players and you have repositories with over 20'000 different programs.

---

### Post by Tews on 2008-03-11
Any program that you have in Windows has a Linux program, or you can run most windows programs under wine.

---

### Post by forrestcupp on 2008-03-11
There is a lot of different software for anything you can imagine.  The only thing about it is that you can't expect to have exactly the same software that you did on Windows.  It's kind of like if you switched to Mac, you'd have to run Mac software.  But there are great alternatives to most things, and almost everything you get for Linux is going to be free.

Also, Ubuntu 7.10 is Gutsy Gibbon.  Hardy Heron is the next version that is still in testing stages.  It will be released the end of April.

Edit:
And wine works sometimes, but it's hit and miss.  Also there are varying degrees of difficulty in getting Windows programs to work.  It's great sometimes, but it's even better if you can find a native Linux alternative.

---

### Post by Sef on 2008-03-11
To Dual Boot and Information on Ubuntu, check out [Psychocat's Ubuntu web site]("http://www.psychocats.net/ubuntu/index.php").

---

### Post by mahela007 on 2008-03-11
but i will get some software right? like a web browser? and other stuff?

---

### Post by PmDematagoda on 2008-03-11
> **mahela007 said:**
> but i will get some software right? like a web browser? and other stuff?

What software do you need?

Firefox is also built-in, so there should not be much of a problem concerning what browser is to be obtained.

---

### Post by mahela007 on 2008-03-11
cool!
i also read in the documentation that ubuntu does not support certain formats like mp3 , real audio and some others.

can i play mp3 format videos by installing various media players?

---

### Post by Achetar on 2008-03-11
There are many applications on Ubuntu by default. And with a working internet connection, thousands more. Here is an incomplete list of apps default in ubuntu:

*OpenOffice.org Office Suite (almost seamless drop-in replacement for MS Office)
*The GIMP (GNU Image Manipulation Program - aka Photoshop for Free)
*Various Games
*Basic Text Editors
*Firefox Web Browser
*Terminal (Command Line)
*Synaptic (for downloading the aforementioned thousands of applications)

The easiest way to find out if Ubuntu has what you need is to boot from the disk, this will not damage your actual partitions. It will allow you to see and (slowly) use the applications. None of your changes will be saved though.

Also, media player *codecs* are available through Synaptic. These allow you to play proprietary formats like MP3 and AAC. There are also codecs for playing DVDs that are encrypted

Hope this helps!

---

### Post by forrestcupp on 2008-03-11
You're right that you can't play mp3's by default.  But they've made it so easy now that if you try to open an mp3 file from your file browser, it will ask you if you want to install the codecs, and it will automatically install it for you, then play the mp3.  So it's about as easy as if it were enabled by default.

I agree that the LiveCD will allow you to see what it's like before you install it.  That's the way to go for you.  I think you'll be pleased.

---

### Post by hyper_ch on 2008-03-11
mp3 codecs are proprietary and hence Canonical is not allowed to ship that into the whole world by default unlike M$ who pays for that... so you need to install some codecs afterwards... it is not a big issue... search for codecs on [https://wiki.ubuntu.com](https://wiki.ubuntu.com) --> you'll end up in the restricted formats section and it will tell you how to get that.

---

### Post by mahela007 on 2008-03-11
oh! And now.. just one final (and Childish) question.
Does linux come with any games? 
It doesnt really matter whether it has games or not.. (my minds made up.. I WANT LINUX)
i just wanna know what kind of  games there are..
more seriously though..  How will linux deal with my printer and other hardware? (eg joystick)

---

### Post by andredaflauta on 2008-03-11
I don't think tht's childish... I like games too :oops:
Ubuntu comes with some classic games (solitaire games and stuff like that) and a lot more   genres in the repositories.

---

### Post by PmDematagoda on 2008-03-11
About the games, while they are not very advanced as Windows ones, you could play some Windows games using Wine or play Linux games such as:-
[Urban Terror]("http://www.urbanterror.net/page.php?6")
Enemy Territory

Both of which are(in my opinion) really fun.

I am not entirely sure about the hardware.

---

### Post by mahela007 on 2008-03-11
How will linux deal with my printer and other hardware? (eg joystick)

---

### Post by PmDematagoda on 2008-03-11
Could you please post the specifications of the hardware.

---

### Post by EnergySamus on 2008-03-11
> **jan quark said:**
> check out this guide:

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

I used the vista version of that guide, and it worked like a charm!

EnergySamus

---

### Post by mahela007 on 2008-03-11
dunno much about the specs..
its a cannon pixma series model Ip6210d
the joysitck is a microsoft sidewinder

---

### Post by rockin_goliath on 2008-03-12
As far as mp3's and multimedia, I wrote a script a while ago that will install all the stuff you need for mp3s, flash in firefox, and commercial DVDs. 
[URL="http://ubuntuforums.org/showthread.php?t=650724"]
http://ubuntuforums.org/showthread.php?t=650724[/URL]

---

### Post by Achetar on 2008-03-22
> **mahela007 said:**
> dunno much about the specs..
its a cannon pixma series model Ip6210d
the joysitck is a microsoft sidewinder
I have the same joystick and it works great in Ubuntu

BTW, if you haven't already downloaded Ubuntu, I would recommend waiting until Hardy comes out, then you won't have to download everything twice

---

### Post by tvtech on 2008-03-22
ok on the games comment there are HUNDREDS if not thousands of games most of which don't show up in the standard repositories for ubuntu.  just go to

[http://sourceforge.net/softwaremap/trove_list.php?form_cat=80]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=80")

sometimes you have to do a little searching for a .deb  "debian compiled installer"  but a lot of games come with other multiplatform installers like jar

or if your willing to go a little deeper you can compile most of the programs yourself and waist countless hours playing games when you should be doing anything else.

---

