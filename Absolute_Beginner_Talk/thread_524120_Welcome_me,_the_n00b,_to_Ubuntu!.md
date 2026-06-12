---
title: "Welcome me, the n00b, to Ubuntu!"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by martialartist81 on 2007-08-12
Well now.... that's quite optimistic of me, isn't it!

Here's the nitty gritty!

Avid Windoze user for many years (cuz I know how it works and I know it well), and I do a tremendous amount of gaming (turns out, most of my games won't run in Cedega, Wine or any other of the variants, I've done the research that far).

So, here's where I am:  Just downloaded and burned my 7.04 Ubuntu and I've played with the LiveCD a little (longer story short, I at one time had a dual boot of Dapper running, but I have long since gotten rid of that old computer to upgrade to the new).  

My goal is to have another dual boot operational so I can still do all my gaming (the hardcore stuff) in Win, but use Ubuntu for all the rest of my stuff (i.e. internet, e-mail, minor games, and learning/tinkering).  My quandry is that I only have one HDD, a SATAII (which I love).  I've already partitioned out 21GB of space to open it up for Ubuntu to install onto.  Now, I know about the HDD0,0 and HDD0,1 and the differences there, so that's no trouble.  But I'm concerned about is loosing what I have on the main partition.  Not expecting an overwrite, but if HD0,1 goes down and out for some reason, will I expect to have to reinstall everything from scratch?

The other question that I would like to ask all you Ubuntu Beano's out there is any one know a really good link where I can find out how to install things (not just the packages, but how to aptget)?  I want to definately install Wine and start tinkering with that, and the Wine page didn't seem to have a tremendous amount of info on it.  So if anyone knows any good links for a good solid walkthrough (I don't want to just cheat the answer, but learn what I'm doing and why), I would most certainly appreciate the help.

Thanks again folks, and Cheers!

---

### Post by por100pre1 on 2007-08-12
Welcome! This is a [basic start ]("https://help.ubuntu.com/7.04/add-applications/C/index.html")on installing.

---

### Post by SoloSalsa on 2007-08-12
I tried Wine, but gave up on it within a day.  This is not discouragement; I just gave up because the program I wanted was not important.
Anyway, installing Wine is quite easy.  Just open the 'Add/Remove' tool, find Wine, and install!
As for the hard disk, Ubuntu will virtually never harm Windows.  If it works live, then it should work installed.  And even if something goes awry, I believe you can recover your current Windows environment by using the Windows installation medium.  That is, if you have the disc that Windows comes on.  I think there are ways to recover without it, but I am not sure of what to do...
Anyway, there is a near-zero chance of anything happening to Windows.  But if this is your only computer, with **extremely** important things, and no backup, then I would advise not to put anything else on it.  Always be aware, that nothing is perfect, and Ubuntu comes with no warranty.  In my experience, though, Windows was more likely to ruin Linux than Linux cum Windows.

---

### Post by benx009 on 2007-08-12
setting up a dual-boot system is pretty straight-forward during the ubuntu install, and you can install all the packages you need (including wine) through synaptic.  if one of your hard drives ever goes down, you will never lose any data on the other.  to boot it, you will just have to reinstall grub again, which really is no big deal

btw welcome to the ubuntu community:)

---

### Post by Ptero-4 on 2007-08-12
You don't have to worry about partitioning, the LiveCD partitioner does a good job in resizing your Windoze partition and letting space for ubuntu, also I recommend you to give more space to ubuntu and less to windoze, this is b/c you'll surelly find yourself adding lots of apps and creating lots of documents in ubuntu.

---

### Post by martialartist81 on 2007-08-12
Thanks all for the suggestions!

One last quick question, when I begin to install, is there any way that the Ubuntu installation has a way to partition the HDD a little differently?

Here's what I'm really asking:  I have 126GB set to Windows, and an additional 21GB set to (or something to that effect) Ubuntu.  So my hard drive is "maxed" out.  But what I want to see is if using Linux, I can increase the "Linux" side and decrease the "Windoze" side.

Can I?  Huh, huh?  Can I?  Can I?

Cheers!

---

### Post by Skidpad on 2007-08-12
Yes, you can do that via GParted.  I would suggest downloading it and creating a live/boot cd, rather than using it from within Ubuntu, but it'll work either way.  If you do it from within Ubuntu, you must first unmount your Linux partition first - there's an easy checkbox in the partition editor to do this.

---

### Post by HermanAB on 2007-08-12
I used to dual boot Linux/Windows, but I invariably found myself wishing I booted the other system.  The solution is to install the free VMware Server (from the VMware web site) or VMware Player (which is in Synaptic) and install Windoze Xp in that.  This way, you can run Windows in a window without having to reboot.

---

### Post by martialartist81 on 2007-08-13
Thanks all.  I'll give it a shot tonight and I'll repost with results.

Thanks again!

---

### Post by martialartist81 on 2007-08-14
Thanks all.  I just used the partitioning in Ubuntu's install.  I was having problems with my LiveCD of gparted, but the Ubuntu version worked like a charm!

Thanks again to everyone for their thoughts and advice!  I do appreciate it.

Cheers!

---

