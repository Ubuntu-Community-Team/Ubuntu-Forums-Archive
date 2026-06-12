---
title: "installing ubuntu on g4 powerbook - HELP?!?!?"
date: 2009-04-12
forum: Apple Hardware Users
---

### Post by ghostofzuul on 2009-04-12
i've read a ton of posts on this topic and my eyes hurt and nothing i've tried works. 

i've got the ubuntu 8.04 disc. 

i've got a mac g4 867mhz powerbook and i'm trying to do a CLEAN INSTALL of ubuntu. i don't want 2 operating systems, and i don't want 10.3 or 10.4 on it anymore... i don't want to dual boot. i just want to run ubuntu on it... when i wipe the hard drive and install the install disc and try the various yboot tricks it still won't recognize and intstall from the cdrom.  i know i'm doing something wrong just can't figure it out. any help would be appreciated... 

thanks!

---

### Post by bug67 on 2009-04-12
I wish I could help.  I have the exact machine you have.  It took an act of god just to finally get to boot from the Live-CD.  After I finally did get it to boot, things were really messed up and I just gave up.

Like I said, I wish I could help.  But, I'd kinda like to have a dual boot on mine as I still need OS X to run Logic.

---

### Post by sms0611 on 2009-04-12
Hi Guys,

  Im running a PowerMac G4. One thing I noticed during a recent re-install of 8.04 on my machine was that I had to disconnect all external equipment (except keyboard and mouse (via USB)) in order for the install CD to boot.

If you have external drives, DVD ROM, Printers attached try booting with them unplugged.

For some reason the external drives (via USB) are seen as SCSI devices and, don't ask me why, this confuses the install.

---

### Post by stream303 on 2009-04-12
> **ghostofzuul said:**
> i've got the ubuntu 8.04 disc.

Because we often run into graphic-card issues right off the bat that need to be taken care of later, I always recommend the "alternate" installer, which is solely text based for installation then a gui when the system comes up.  8.04.1 LTS alternate is a good choice.  8.10 Intrepid is very problematic, so for now stick to 8.04 or perhaps try Jaunty 9.04 when it arrives or run the beta "alternate". 

> i've got a mac g4 867mhz powerbook and i'm trying to do a CLEAN INSTALL of ubuntu.

Even easier!  When installing, just be sure to let guided partitioning "use the whole disk" and it will dutifully wipe out osx and set up automatically for you.  (G3 iMacs with larger than oem drives are the exception with their 8gb root partitioning limitations).

So if you let guided partitioning use the whole disk you should be good to go.  The other op is correct that you should disconnect all external drives first.

Now that the bits are on the disk, you can tackle the usual ppc issues.  If you come across the dreaded black screen right away, at the second-stage yaboot boot: prompt, try hitting TAB to stop the countdown.  Then enter

```
Linux video=ofonly
```
(You may have to apply this right at the start of installation if your screen is black too)

If you can now see the system boot, you can add this kernel paramater to your /etc/yaboot.conf in the image stanzas to make it permanent:

```
append="video=ofonly"
```
or just add this to the end of what is already there in those append= lines.  Be sure to let the system know of your modifications to yaboot.conf with:

```
sudo ybin -v
```

The next task might be to custom modify your /etc/X11/xorg.conf file, as xorg sometimes does not correctly identify the graphics card or its capabilities.  This is due to the hardware not communicating properly as it was designed to talk only to osx.

At this point, check out the wikis or other threads for xorg.conf details specific to your machine.

Take it slow and easy and don't take it out on the powerbook. :)

---

