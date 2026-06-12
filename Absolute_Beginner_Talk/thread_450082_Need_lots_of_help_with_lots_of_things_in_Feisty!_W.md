---
title: "Need lots of help with lots of things in Feisty! WiFi, !partitioning!, Beryl"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by pHreaksYcle on 2007-05-20
This is going to be long whether I like it or not, so I will TRY to keep it short...thanks for your time in advance whoever is brave enough to help! (and yes, I did try Google for all this stuff first!) Any questions about this, please respond here or to dknoll {[at]} sjci DOT (((COM)))

I am using a:
Dell Inspiron 1501 LAPTOP (WXGA wide screen)
AMD Turion 65 (2.0GHz/512KB)
80GB Hdrive
ATI RADEON Xpress1150 w/ 256MB of RAM
Came with Image Restore on Disk
Windows Version=Vista

Have Intermediate to Advanced knowledge across the board. I know lots of stuff, but have little things missing here and there. (That is what G00gle is for right?)

I installed Ubuntu Feisty Fawn, using it for school for about one month/month and half, works great for taking notes etc. One problem, NO WiFi, just wired, which=pain in ****. No matter what I do, no matter how many guides I follow, programs/firmwares I install (ie: ndiswrapper) it just wouldn't work. (Still doesn't)

I also wanted to get Beryl to work. No good there either, followed all of the steps, tried every guide I could follow, nothing.

I have been using this site [http://www.ubuntu1501.blogger.com]("http://www.ubuntu1501.blogger.com")
and it's guides, no good. (Did mail out for the free sticker though!) :D
[B]
My question is how to get WiFi working and Beryl or Compiz or whatever the hell it is! The jigglyz and the desktop cube! That is all I ask![/B]

IN ADDITION, to these problems, while trying to get these two problems to work, WiFi and Beryl (jigglyz :D), I installed Uberyl. This is a not-very-known Spanish distro and it is supposed to have Beryl and WiFi on laptops working "out-of-the-box". (Or off the CD I suppose...) Needless to say, since I am posting this, none of this crap worked! Trying countless re-installs of Feisty and Uberyl (which is Ubuntu version Edgy), and not knowing ANYTHING about partitioning except where Windows is located, I have ended up with FOUR OS's ON MY LAPTOP! That is a secondary issue, but one I would like to take care of if possible. I do not want to screw up my Vista installation, but if that is part of someones grand scheme to make these things work, I'm down! I have no qualms about wiping the slate clean if that is what it will take and I have instructions on how. I am trying to **at least** wipe all Ubuntu from my system and start over with just Vista.

BTW, this is the output from GRUB on boot-up if it helps (or even if it doesn't, I guess...)

[I]Ubuntu Kernel 2.6.20-15-generic
"SAME THING" recovery mode
then the Ubuntu memtest option
Other:
M$ Vista (loader)
Ubuntu 2.6.17-11-generic (on /dev/sda5)
Ubuntu 2.6.17-11-generic revovery mode on (/dev/sda5)
Ubuntu 2.6.17-10-generic (on /dev/sda5)
then the Ubuntu memtest option.[/I]

I assume the -10 is Uberyl because Uberyl is Edgy and that is an older verions which=older number...
Sorry if I rambled a little bit, but it's late and I am strung out about this.
I would like to stay with Linux (specifically Ubuntu, cuz it has a very strong community it seems), but this is starting to discourage me lots... Thanks SO MUCH for your help in advance if any is available!!!

---

### Post by lamalex on 2007-05-20
did you try this [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643) for beryl? It's worked for a lot of people with ATI cards.

---

### Post by pHreaksYcle on 2007-05-21
[B][U]Thanks for responding so quick!!
[/U][/B]
Although this looks kinda similar to the guide I found on ubuntu1501.blogger.com, it has a few changes that I think will make a difference. But, first I need to get a fresh install without all the rest of those copies of Ubuntu!! Know anything about partitioning? :D

EDIT!!! The link to the site I was using is really this:
[http://www.ubuntu1501.blogspot.com]("http://www.ubuntu1501.blogspot.com")

---

### Post by Noahod on 2007-05-21
Doesn't 

[http://ubuntuforums.org/showthread.php?t=450117&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=450117&highlight=restore+grub)
[http://ubuntuforums.org/showthread.php?t=450114&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=450114&highlight=restore+grub)
[http://ubuntuforums.org/showthread.php?t=450082&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=450082&highlight=restore+grub)

sort of count as double, err triple posting?

---

### Post by pHreaksYcle on 2007-05-21
yes it does but I really didn't know where the best place to post was...sorry!
Oh, and thanks for your help Noahod, that really was useful for my issue.

---

### Post by lamalex on 2007-05-21
for wifi, what kind of card do you have, in a terminal type lspci and post the results (assuming it's not a usb wifi adapter). Also, be specific as to what you want to do with partitioning and I will help you accomplish it

---

### Post by pHreaksYcle on 2007-05-21
thanks to you guys for all your help!
if you look at the links the last guy put up, you can see what I ended up doing.

---

