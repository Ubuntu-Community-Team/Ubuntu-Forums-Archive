---
title: "[SOLVED] gutsy installation problems"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-11-09
Gutsy doesn't finish the installation process - I tried 3 times using 2 different CD's and it just gets stuck at 82% "Configuring apt... Scanning the mirror".
I did the md5sum check on the iso, burned it onto 2 separate CD's just in case, and did integrity checks for each CD.
What could be the problem and how do I fix it?
It's the regular desktop version of Gutsy, 250 GB SATA hard disk. Feisty works ok.
Please do help.
Thanks.

---

### Post by Joakim Stokland on 2007-11-09
What language are you installing? I tried several times to install Norwegian Gutsy, but my installation got stuck too, Some times at 87% as far as I recall, and some times a bit earlier. I don't know why, but installing the English version worked flawlessly. I added Norwegian when setup was complete without any trouble.

Joakim

---

### Post by Paul820 on 2007-11-09
Is your internet connection working when you start the install? It's getting stuck while trying to update the sources.list if you have no connection. You should try and get the connection working before installing or skip that process on the install and update the sources when it's finished. There should be an option somewhere on the install screen to skip it.

---

### Post by kleo skywalker on 2007-11-10
I'm installing English.
How do I get the internet connection working before I install?? My internet connection doesn't work unless I reboot after configuring it. And there was no option to skip.
(Because the install stopped incomplete, I had to install Feisty again, and that got stuck at 83% - the point you mentioned - updating source lists, and I had the option to skip that. But this gutsy install stops at "configuring apt... scanning mirror" and there is no option to skip.)
Please help.

---

### Post by kleo skywalker on 2007-11-10
hello? anyone?

---

### Post by koma77 on 2007-11-10
Remove the network cable first and then install.
It won't get stuck then, it will automatically skip the network part.

When it is installed you can configure your network alright.

---

### Post by kleo skywalker on 2007-11-10
> **koma77 said:**
> Remove the network cable first and then install.
It won't get stuck then, it will automatically skip the network part.

When it is installed you can configure your network alright.

Ok. Are you sure the gutsy install is getting stuck because of the network cable? (Excuse me for asking, but I'm a bit weary coz I've had to install some 5 times in the last couple of days!)

---

### Post by kleo skywalker on 2007-11-10
And it won't be very good if I unplug the network cable, try installing again (and in the process lose my current feisty install) and then get stuck and have to do everything again.
So please, any more ideas on why this might be happening and what I could do about it would be appreciated.

---

### Post by matthewcraig on 2007-11-10
Sounded like you got a pretty good explaination (install looking for Internet) and a resolution (disconnect your network cable from your computer).  Give it a try and write up what happened when you are done.

---

### Post by bulldog on 2007-11-10
Or better maybe,install Gutsy next to your Feisty,create a new 10Gb partiton somewere and install Gutsy.
So you have always a working copy of ubuntu.
I have 4 distro's installed,I'll  never upgrade,always a fresh install and in case of malfunctioning,I have always a good working copy left.

Tip:
Create a minimum of two 10GB partitons for /
Create one swap partition,this can be used for all distro's
Create a /home as big as you like.

If you install a new copy,use the second 10GB partition,choose another logon name and use the same swap and /home.
If the new copy is working well,you can format the old copy if you like,so you have space when another new copy comes along.
In case of troubles with the new copy,you can go back to the 'old one'

I do this for over two years and it serves me very well,just think about it,never lose your preferences because they are in /home,always a working copy,and you can try out other distro's as well,without any danger to lose your data.

---

### Post by matthewcraig on 2007-11-10
This is a great idea, bulldog.  I was starting to come around to this way of thinking during my fight with my last upgrade, but I had never heard of anyone doing it before.  Glad to know it's S.O.P. for you!

---

### Post by kleo skywalker on 2007-11-10
> **bulldog said:**
> Or better maybe,install Gutsy next to your Feisty,create a new 10Gb partiton somewere and install Gutsy.
So you have always a working copy of ubuntu.
I have 4 distro's installed,I'll  never upgrade,always a fresh install and in case of malfunctioning,I have always a good working copy left.

Tip:
Create a minimum of two 10GB partitons for /
Create one swap partition,this can be used for all distro's
Create a /home as big as you like.

If you install a new copy,use the second 10GB partition,choose another logon name and use the same swap and /home.
If the new copy is working well,you can format the old copy if you like,so you have space when another new copy comes along.
In case of troubles with the new copy,you can go back to the 'old one'

I do this for over two years and it serves me very well,just think about it,never lose your preferences because they are in /home,always a working copy,and you can try out other distro's as well,without any danger to lose your data.

Thanks, this sounds like a good idea. Except, I'm not very good with this kind of stuff - I can manage partitioning for one OS, but I've never done it for 2.
I'm not sure if I'm getting this right, but you're saying I have one swap partition, one "/home" where all my data stays and can be accessed from both feisty and gutsy, and 2 "/" partitions - one for gutsy, one for feisty. Is that right?
If yes, how do I go about doing this? And how do I choose which one to boot?
Thanks!

---

### Post by bulldog on 2007-11-10
> **kleo skywalker said:**
> Thanks, this sounds like a good idea. Except, I'm not very good with this kind of stuff - I can manage partitioning for one OS, but I've never done it for 2.
I'm not sure if I'm getting this right, but you're saying I have one swap partition, one "/home" where all my data stays and can be accessed from both feisty and gutsy, and 2 "/" partitions - one for gutsy, one for feisty. Is that right?
If yes, how do I go about doing this? And how do I choose which one to boot?
Thanks!

First you have to prepare a hdd with the right partiitons.
If you have a second hdd this would be easy,if you have just one with windows it will be a little harder,it all depends on how large is your hdd.
You can imagine you can't do this on a 20GB hdd can you?

So if you have just one hdd with windows,say 200GB do as follows.
Let windows be on the first primary,this is important!!

Set the windows partition say 40GB
Set a windows data for backup say 60GB

Now create an extended partition which is the rest of the hdd.
In this extended partition create 2x10GB partitions for different / partitions
Create one swap depending on installed RAM it should be 1or2GB max.
Make the rest of the space one partition for your /home.

Now when you install feisty,choose one of the 10GB partitions as /
Swap as swap and /home as /home
Install and your done.
Now comes Gutsy.
Install it on the other 10GB partition use the same swap and same /home
Only choose another logon as you did in feisty,so there will be a new folder created for gutsy in your /home.
And your done.
Comes a new linux you want to try,mount your feisty as / and format it,use the same swap and /home ,choose another logon as you had in feisty and gutsy and your done.

You can start either OS from grub because every time you install another linux,your grub and menu.lst will be over written with the new option,leaving the old one there.

Looks simple and it is.:)

---

### Post by kleo skywalker on 2007-11-10
> **bulldog said:**
> First you have to prepare a hdd with the right partiitons.
If you have a second hdd this would be easy,if you have just one with windows it will be a little harder,it all depends on how large is your hdd.
You can imagine you can't do this on a 20GB hdd can you?

So if you have just one hdd with windows,say 200GB do as follows.
Let windows be on the first primary,this is important!!

Set the windows partition say 40GB
Set a windows data for backup say 60GB

Now create an extended partition which is the rest of the hdd.
In this extended partition create 2x10GB partitions for different / partitions
Create one swap depending on installed RAM it should be 1or2GB max.
Make the rest of the space one partition for your /home.

Now when you install feisty,choose one of the 10GB partitions as /
Swap as swap and /home as /home
Install and your done.
Now comes Gutsy.
Install it on the other 10GB partition use the same swap and same /home
Only choose another logon as you did in feisty,so there will be a new folder created for gutsy in your /home.
And your done.
Comes a new linux you want to try,mount your feisty as / and format it,use the same swap and /home ,choose another logon as you had in feisty and gutsy and your done.

You can start either OS from grub because every time you install another linux,your grub and menu.lst will be over written with the new option,leaving the old one there.

Looks simple and it is.:)

Thanks very much. I don't have windows though - right now I have a clean 250 GB hard drive with feisty installed.

---

### Post by bulldog on 2007-11-10
> **kleo skywalker said:**
> Thanks very much. I don't have windows though - right now I have a clean 250 GB hard drive with feisty installed.
Well shrink the feisty to it's minimum create the other partitions and you're done.
You can move the /home in feisty to your new /home so all your data and preferences from feisty are safe when you do a reinstall of feisty that is.

Better way is ,if your data isn't valuable ofcourse,otherwise back it up first,to sweep the whole hdd and start from scratch.
You need reinstalling feisty,but that's only half an hour.

---

### Post by kleo skywalker on 2007-11-10
I removed the network cable and then installed - it installed but told me that security something couldn't be accessed from security.ubuntu.something. How do I get that?
Also the screen resolution is wrong - it's 1280x1024, and there isn't an option for 1024x768 at all!

---

### Post by Da King on 2007-11-10
did u download OS from the ubunty site and ISO and burned it? if so check for errors before u try any installing..if u want to check for errors just insert ur cd as the pc starts and choose the :CHECK THE CD FOR DEFECTS" if it says its 100% working then i think u shod get another CD/DVD ROM if possible and try again. might be a scratch...

---

### Post by Joakim Stokland on 2007-11-10
I'm not quite sure about the resolution thing. It may involve xorg.conf, and I'm not too steady about that. But the security thing is simply a matter of running an update :)

Since you already got Ubuntu installed, you don't have to worry about the CD being defective.

Good luck!
Joakim

---

### Post by kleo skywalker on 2007-11-10
Thanks a lot for the help, everyone. I've installed and updated, though I'm still working on that resolution problem.
Also, I think a clean install should not depend on anything other than a correctly downloaded and burned live cd.

---

### Post by Joakim Stokland on 2007-11-10
What brand and model is your graphics card? (If you don't know, you can find a complete list of your hardware by clicking System - Preferences - Hardware information)

If you have a common graphics card, I'm sure you can find some information about your problem here at the forums by searching for make and model.

Good luck!
Joakim

---

### Post by bulldog on 2007-11-10
> **kleo skywalker said:**
> Thanks a lot for the help, everyone. I've installed and updated, though I'm still working on that resolution problem.
Also, I think a clean install should not depend on anything other than a correctly downloaded and burned live cd.

About the install,sorry,but you're terrible wrong here.
If you have only programs installed which came from the official ubuntu repo's,it should work,but if you have enabled any other non official repo and more important,you installed software from it,you're heading for a little disaster.


The screen thingy,did you tried in console or a terminal```
sudo dpkg-reconfigure xserver-xorg
```
This will give you a change to choose the right driver and resolution.

It should be better though to install any driver for the graphics,you can install ATI and nVidia drivers with the build in restricted drivers,or you can choose to use envy for the latest propietary drivers.

---

### Post by Joakim Stokland on 2007-11-10
Please, ALWAYS backup your xorg.conf before trying that! If you look around on the forums there are too many examples of computers not able to boot the GUI after doing that!

Backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Now you can do the dpkg-reconfigure-thing.

IF this screws up your system, type:
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

Then you should be back where you started.

Now, you may go ahead and try
```
sudo dpkg-reconfigure xserver-xorg
```

But I recommend searching the forums for similar problems with the exact graphics card first.

Good luck!
Joakim

---

### Post by kleo skywalker on 2007-11-10
> **bulldog said:**
> About the install,sorry,but you're terrible wrong here.
If you have only programs installed which came from the official ubuntu repo's,it should work,but if you have enabled any other non official repo and more important,you installed software from it,you're heading for a little disaster.

Er... I downloaded Gutsy from Ubuntu's website, checked and burned it exactly as the website says. And then I booted to the LiveCD and double clicked install - where do official and unofficial repositories come into the picture here?
The problem I was facing (which you'd know if you'd read my first post) was that the installation process didn't go beyond a particular point (83% "configuring apt... scanning mirrors"). Some of the responses told me that absence of a working internet connection was the problem, and I should unplug the network cable and then try installing - which I did. Since this worked, it seems clear that the installation looked for a working internet connection, didn't find one, and therefore stopped. This is why I said that once you have the LiveCD, you should be able to at least install without an internet connection. Unauthorized software has no role to play whatsoever.
I use and like Ubuntu too, but I know it is not flawless. Maybe you could consider comprehending someone's problem and view before telling them they're 'terribly wrong' and 'heading for disaster'?

---

### Post by kleo skywalker on 2007-11-10
> **Joakim Stokland said:**
> Please, ALWAYS backup your xorg.conf before trying that! If you look around on the forums there are too many examples of computers not able to boot the GUI after doing that!

Backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Now you can do the dpkg-reconfigure-thing.

IF this screws up your system, type:
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

Then you should be back where you started.

Now, you may go ahead and try
```
sudo dpkg-reconfigure xserver-xorg
```

But I recommend searching the forums for similar problems with the exact graphics card first.

Good luck!
Joakim

Thank you very much for your time and response. I'd started a new thread about this problem and it has now been solved.

---

### Post by bulldog on 2007-11-10
> **Joakim Stokland said:**
> Please, ALWAYS backup your xorg.conf before trying that! If you look around on the forums there are too many examples of computers not able to boot the GUI after doing that!

Good luck!
Joakim

For your information,when you reconfigure the xserver with this command,it will make a copy of the xorg.conf with a date and time stamp on it,so manual backing up is some what un necessary.

---

### Post by Joakim Stokland on 2007-11-10
> **kleo skywalker said:**
> Thank you very much for your time and response. I'd started a new thread about this problem and it has now been solved.

Great! I'm happy for you :)

Joakim

---

### Post by jagwah on 2007-11-16
I know it's a bit late, but for future reference, and for anyone else who comes across the problem of the install hanging at "Scanning the mirrors", an easier way to do it than disconnecting your network cable, is to just go up to the network icon, upper right of screen, right click, and uncheck "Enable Networking", and the install will continue immediately. 

This is of course assuming you are running the Ubuntu Live, and installing to the Hard Drive from that, and not installing via any other method.

---

