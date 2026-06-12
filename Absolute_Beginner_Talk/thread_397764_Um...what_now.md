---
title: "Um...what now?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by HokkaidoHillbilly on 2007-03-31
Ok, I now have a working dual boot w/ WinXP Pro and Ubuntu 6.10 on my Dell XPS M1210, with wireless working out of the box and I'm tying this in Ubuntu Firefox.  So far, so good.

But, to tell the truth, I'm at a bit of an impasse.  I know that I need to update Ubuntu & what not, i.e. the little notification tag is lit up, but it says that I have 162 updates available.

First off, do I really need to download all 162 updates?  It seems like there's a ton of stuff there that I have either no use for or have no idea what it does.

Secondly, once I figure out what I need to update, what do I do then, and how the heck do I even install stuff?  I'd consider myself a Windows power user, but so far Ubuntu seem less than user friendly...


Thanks in advance for all your help!



Hokkaido Hillbilly
Tohma, Hokkaido
Japan

---

### Post by eljalill on 2007-03-31
Well, since a lot of the programs that come with ubunut are imbedded in the desktop, it might be a good idea to keep them and indeed to all the updates.

But you could always check. For this you open synaptics (I think it is in acessories), and look through what is installed. with a right click you can select to uninstall. But pay attention to whatever synaptic wants to uninstall together with the selected package! If there is anything like gnome-desktop or linux-modules in there, leave it be! Adn if in doubt, rather leave them in.

You can then get the updates through typing 
```
sudo apt-get update
sudo apt-get upgrade 
``` in a terminal, or through clicking "mark all upgrades" in synaptics, and the "apply".

And updating really isn't much of a hassle. Just click or type, go for a coffee, and when oyu come back it should be done.

---

### Post by hyper_ch on 2007-03-31
Ubuntu is not less user friendly than windows... it's different...

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

And I would recommend to do all updates.

---

### Post by v8YKxgHe on 2007-03-31
I'd suggest reading the [Working with your desktop]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html") guide, it's a really good guide and will teach you a lot about working with Ubuntu.

Also, you'll notice most guides will tell you to use the Terminal (Applications->Accessories->Terminal). This doesn't mean however that you have to use the terminal, it is just quicker for us to say:

```
sudo apt-get install program
```

You could enter that in terminal, or you could go to Synaptic (System->Admin->Synaptic Package Manager), search for "program", then once you've found it right click on it and go "Mark for installation" then hit "Apply" top-left of Synaptic. 

Use which ever feels better to you.

---

### Post by zvacet on 2007-03-31
I don´t belive that Ubuntu team gives updates because they feel like it.Probably you need it or otherwise you will not see them.So take them all,it is fir your own good.

---

### Post by hyper_ch on 2007-03-31
If you don't compile software on your own and exclusively use the repositories for getting software then I see no problem why not installing all updates... only if you do your own stuff... installing newer versions from source and compile them then you have to watch what you're going to update :)

---

### Post by Adramelech on 2007-03-31
I guess you are really new to linux, so be patient.

Do all updates, those are security update, so is better to secure programs specially when you dont know what program is used for, could be a critical one ;). 

btw In the update window, theres a description tab that says whats the program for.

---

### Post by mikesmith36 on 2007-03-31
I too am a new Ubuntu user, I replaced windows on my laptop with Ubuntu and must say I am very pleased with it so far - it just seems more stable then windows and less prone to crashes.
I used to accept all critical updates in windows and would recommend you do the same in Ubuntu.
My advice would be install them and don't get impatient, I rebooted when I thought the installation of updates had crashed and the system would no longer boot. I reinstalled and updated again but waited this time and on the same install (cant remember what the file/program was) the installation sits inactive for about 3 to 4 minutes and suddenly springs back into life.
I had 343 updates on my first install but when I reinstalled only 166 were mentioned, this was followed later by a similar amount so I can only assume they were divided up for some reason the second time. Now when I check it shows my system as up to date.

Best of luck - Michael :)

---

### Post by HokkaidoHillbilly on 2007-04-01
Hey everybody & thanks so much for all your help and advice!

As one of you mentioned...yeah, I'm a complete & total Ubuntu/Linux beginner, so thanks for putting up w/ me.  As far as my "not very user friendly" comment, my apologies.  I was tired and frustrated at the time, but feeling a whole lot better about my new toy now. :)

I went ahead & installed all of the updates per all your advice and everything seems to be working as it should, so cheers!

Thanks again & I'm sure I'll see all of you around soon,



Hokkaido Hillbilly ;)

---

### Post by hyper_ch on 2007-04-01
Just keep in mind: Linux is not Windows... some things are done differently and it seems to you user-unfriendly because you are not used to it :)

---

### Post by Alfdog on 2007-04-01
I would recommend downloading the new 7.04 beta, since the video, and wireless networking will work without having to do any installing/configuring.

---

### Post by dracomordag on 2007-04-01
of course, a fresh feisty install gives you some 300 program updates to get.

good thing it only takes about 20 minutes for it to auto-DL/install them anyway. :)

---

### Post by v8YKxgHe on 2007-04-01
Please do not recommended a beta release that will, can and has broken in the past. Something that may be stable in Beta today may not be stable in Beta tomorrow.

---

### Post by dracomordag on 2007-04-01
i'm sure it'll be fine in 18 days

:)

---

### Post by jvc26 on 2007-04-01
But between now and 18 days it might totally screw over your system ;) I've used the feisty beta now (and since herd4) with absolutely no problems, but it doesnt mean there arent any out there, and for a brand new user to start and hit problems from the word go would be 1/ demoralising and 2/would find them one hell of a lot harder to deal with than someone who has been using ubuntu for a while.
Il

---

### Post by HokkaidoHillbilly on 2007-04-13
Thanks for all the advice and encouragement, everybody.  Thanks to the help of the Ubuntu community, I've probably got my system about 90% to where I'd like it to be (i.e still tweaking Beryl & no cam or built in mic yet).

Learning Ubuntu over the course of the past 2 weeks has defo been an adventure and I know that the adventure's only just begun, so I'm gonna stick w/ it.  It sorta like learning to ride a bike all over again, and while it's frustrating as hell sometimes (i.e. it took me about 8 or 9 fresh installs to get this far ;) ), it sure is fun.  That, and it feels kinda old school to be using the terminal/command line again *grin* (ah, the good ol' days o' C=64 basic...)

Cheers to all of you! :)

---

