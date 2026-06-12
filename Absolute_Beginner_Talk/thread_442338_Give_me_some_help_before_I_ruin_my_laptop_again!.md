---
title: "Give me some help before I ruin my laptop again!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-05-13
I tried Ubuntu 7.04 when it came out and im using a ATI Radeon Xpress 200M graphics card which as you will know dosen't work with 7.04 without editing some file, which as I'm a complete n00b to Linux didn't have a clue how to do so I removed linux and couldn't get rid of GRUB and had to re-install XP AGAIN which I've had to do twice and now my graphics look horrible (I don't know why) so how (before I go again as I want to run beryl) can I fix this before I install 7.04?

Please give n00b step by step guide!

Thanks

Intel Celeron M 410 Processor 1.46 GHz
512 MB RAM
SuperMulti Optical Drive Dual Layer
128 MB ATI Radeon Xpress 200M
55 GB HDD

---

### Post by Ek0nomik on 2007-05-13
What exactly is the problem?

Can you install Feisty with the Live CD?  How about the Alternate CD?  Do you get an error upon installation?  Try to give some more information.  ;)

---

### Post by SamTyson92 on 2007-05-13
> **Ek0nomik said:**
> What exactly is the problem?

Can you install Feisty with the Live CD?  How about the Alternate CD?  Do you get an error upon installation?  Try to give some more information.  ;)

I can run Feisty on the live cd but after I install and re-boot it comes up with the error screen which is due to a bug in ubuntu with the ATI X**** Graphics cards and it says you must edit something in a config file to fix it.

---

### Post by nickpaton on 2007-05-13
Hi Sam

A bit more information - are you using 32 or 64bit Ubuntu?

I  too have a laptop with the same built in graphics and it is quite configurable providing I use 32bit x86 Desktop installation.

Re the error message - what is it exactly.

Finally... what is the make and model of the lappy.

---

### Post by SamTyson92 on 2007-05-14
> **nickpaton said:**
> Hi Sam

A bit more information - are you using 32 or 64bit Ubuntu?

I  too have a laptop with the same built in graphics and it is quite configurable providing I use 32bit x86 Desktop installation.

Re the error message - what is it exactly.

Finally... what is the make and model of the lappy.

Im using 32 bit and I dont know what the error message is as its way too long to remeber but theres a sticky about it on this forum (at the top) and Im using a Toshiba Satellite A110-162

---

### Post by nickpaton on 2007-05-15
Just been re reading your posts.

To sort out the problem of grub being present when you remove Ubuntu, read [this]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console") article.

At the part where you are asked to enter an Administrator password, simply press enter key.

Hopefully that will stop you having to reload XP each time.

Regarding the ATI card problem we need to refer to [this]("http://ubuntuforums.org/showthread.php?t=414194") post.

The first thing you will need to do is to install using the x86 32bit Alternative disc, which typically can be downloaded from[ here]("http://www.mirrorservice.org/sites/releases.ubuntu.com/feisty/").

This is using a UK mirror, but if you are from elsewhere, start [here]("http://www.ubuntu.com/getubuntu/downloadmirrors"), then select your country, then a mirror within your country, Click on Feisty, and finally select ubuntu-7.04-alternate-i386.iso

Note that you MUST install using text install mode.

When you have installed Feisty using the above method, allow it to fully update. (Hopefully you will be able to reboot successfully into Feisty using this method, but if not can you post back exactly how far you do get and whether you can get into a Terminal as described just below to carry out the fix).

Then you must open a Terminal.  This is done by Applications > Accessories > Terminal.

Then one at a time copy each command into the terminal and hit the enter key - ie:

Copy and paste the following line into the Terminal:

```
sudo apt-get update
```

Enter Key and let it run.  Then copy and paste the following into the terminal again

```
sudo apt-get dist-upgrade 
```

And hit the enter key.

And so on for each of the commands.

I'm off to bed now but hope this helps some.  Get back with any problems, or hopefully sucess!

Nick

---

### Post by SamTyson92 on 2007-05-17
> **nickpaton said:**
> Just been re reading your posts.

To sort out the problem of grub being present when you remove Ubuntu, read [this]("http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console") article.

At the part where you are asked to enter an Administrator password, simply press enter key.

Hopefully that will stop you having to reload XP each time.

Regarding the ATI card problem we need to refer to [this]("http://ubuntuforums.org/showthread.php?t=414194") post.

The first thing you will need to do is to install using the x86 32bit Alternative disc, which typically can be downloaded from[ here]("http://www.mirrorservice.org/sites/releases.ubuntu.com/feisty/").

This is using a UK mirror, but if you are from elsewhere, start [here]("http://www.ubuntu.com/getubuntu/downloadmirrors"), then select your country, then a mirror within your country, Click on Feisty, and finally select ubuntu-7.04-alternate-i386.iso

Note that you MUST install using text install mode.

When you have installed Feisty using the above method, allow it to fully update. (Hopefully you will be able to reboot successfully into Feisty using this method, but if not can you post back exactly how far you do get and whether you can get into a Terminal as described just below to carry out the fix).

Then you must open a Terminal.  This is done by Applications > Accessories > Terminal.

Then one at a time copy each command into the terminal and hit the enter key - ie:

Copy and paste the following line into the Terminal:

```
sudo apt-get update
```

Enter Key and let it run.  Then copy and paste the following into the terminal again

```
sudo apt-get dist-upgrade 
```

And hit the enter key.

And so on for each of the commands.

I'm off to bed now but hope this helps some.  Get back with any problems, or hopefully sucess!

Nick


Whats the diffrence in the discs?

---

### Post by Happy_Man on 2007-05-17
The LIVeCD allows you to install using a happy GUI, and the text installl has no real GUI. That's the only difference.

---

### Post by nickpaton on 2007-05-17
The important difference is also that the alternative CD requires less PC resources than the LiveCD version.

---

### Post by SamTyson92 on 2007-05-17
> **nickpaton said:**
> The important difference is also that the alternative CD requires less PC resources than the LiveCD version.

So how will this fix my problem?
of the error in the config file for the xorg thingy

---

### Post by nickpaton on 2007-05-18
> **SamTyson92 said:**
> So how will this fix my problem?
of the error in the config file for the xorg thingy

Because hopefully it's going to correctly install the base components, and from there you can install the ATI drivers etc.

---

