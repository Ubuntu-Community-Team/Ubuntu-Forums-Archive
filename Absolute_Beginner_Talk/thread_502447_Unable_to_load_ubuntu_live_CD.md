---
title: "Unable to load ubuntu live CD"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by madlan on 2007-07-16
Hi, I would like to try the live CD, but it will not boot up on my system.
Have tried safe mode.

PC specs:
Intel Quad core QX6700 2.66 GHz CPU
EVGA 8800GTX Graphics
4GB CM2X1024-8500C5D RAM
2X 150GB 10K RPM Raptors RAID 0 Hard Drives
24" Dell 2407WFP Monitor

Any thing else I can try?

Vista is currently installed.

Thanks!

---

### Post by C.S.Cameron on 2007-07-16
Well you could try upgrading your system, it looks pretty minimal, (humor).
Is CD set to boot first in your BIOS?
Cork

---

### Post by jimbob on 2007-07-16
Is the BIOS set to boot from CD?   Does it appear to read it at all?  When you put the Vista CD in does it start to read that OK?
Did you burn the CD yourself?  If so, did the checksum read OK?

Just some thoughts.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by madlan on 2007-07-16
hehe, what would you suggest I upgrade?

I'm an advanced hardware/windows user, who would like to try ubuntu, so yes - cd is set to first boot device.
CD boots to menu fine, I select the first option (start/install) or safe vga mode, screen goes black and nothing further happens!

Regards.

---

### Post by madlan on 2007-07-16
CD checked for defects using menu option, BIOS boot options are fine.
CD is latest build - 64bit version.

> **jimbob said:**
> Is the BIOS set to boot from CD?   Does it appear to read it at all?  When you put the Vista CD in does it start to read that OK?
Did you burn the CD yourself?  If so, did the checksum read OK?

Just some thoughts.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by CautionaryX on 2007-07-16
In Windows put the CD in the drive and click on your CD drive in My Computer. You should see a bunch of folders and other stuff. If you only see 1 file you burned the CD wrong. You'll have to burn another CD making sure that your burner knows its burning from an image.

Also, I heard Vista has compatability issues when burning CDs and DVDs. Apparently MS made a disk format that is only readable from Win XP / Vista. But I don't think this is the problem.

---

### Post by C.S.Cameron on 2007-07-16
Does the CD work  in other machines?
Have you tried CTRL ALT F2 in your black screen?

---

### Post by theDaveTheRave on 2007-07-16
Have you confirmed that the disk has downloaded correctly using the MD5checksums?

Which version are you attmepting to run from live? 

I used Fiesty fine with my new Laptop (Vista installed).

if you do decide to go over to Ubuntu (it is considerably faster on boot and usability than my Vista partition) I would recomend sorting out the partitions first if you can, or you may have to play with the fstab to get a swap partition going.... although with 4GB of memory I'm not sure that  a swap partition is something that will ever be a problem for  you :lolflag:

good luck with the install.

Dave

ps. sorry to ask a silly question, as you are a self profesed hardware nut, don't you have a spare system that you could put together with all your old gear? then you can just go for it and have a dedicated linux system..... although I would say just go for it and get rid of Vista quick (so far I am not impresed with Vista, give me XPpro and day!).

have fun.

Dave

---

### Post by sancho panza on 2007-07-16
> **madlan said:**
> CD checked for defects using menu option, BIOS boot options are fine.
CD is latest build - 64bit version.

I am not sure if checking using menu options can catch checksum defects. Hope you made sure that the [checksum of the iso file that you burned was correct]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28checksum%29#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24"). 
If it still doesnt work, try booting the 32-bit version. Thats the most I can tell. :(

---

### Post by kyphi on 2007-07-16
Only last year I too had cutting edge equipment and experienced the same problems with booting from the live CD.  Now, of course, my equipment is superseded.

Try the suggestions on this link:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Good luck.

---

### Post by madlan on 2007-07-16
[LIST]
[*]MD5 of the x64 CD is: a2b159599b69cea51371eee1ec5feda6
[*]CD was burnt using Nero, have not just burnt the iso file! (ubuntu-7.04-desktop-amd64.iso)
[*]I donated my old hardware to a local school, so this is my only system.
[/LIST]

At a guess, I would say it’s the graphics card, I have read a few posts about people having problems booting up - but the details are another language to me!

Is my hardware unsupported? maybe I will need to wait for another build that supports the 8800?
Could the four cores be causing problems?

Thanks for the help guys.

---

### Post by kyphi on 2007-07-16
I just noticed that you are using the 64 bit version.  Why?  And why the AMD 64 to run on an Intel machine

The version you need is the 686 32 bit.

---

### Post by madlan on 2007-07-16
I read that the 64 bit version was the one to go for if you had a 64 bit cpu (+4GB ram)

---

### Post by kittyhawk63 on 2007-07-16
> **madlan said:**
> I read that the 64 bit version was the one to go for if you had a 64 bit cpu (+4GB ram)

Madlan,
Since using Ubuntu and being on this forum, I've noticed the most recommendations are to drop 64 bit and use 32 bit. There is lot less trouble. Later, as time permits those developing Ubuntu, the 64 bit versions will improve. For now, I highly suggest you download the 32 bit version, burn the image and give it a try.
kh

---

### Post by madlan on 2007-07-16
OK, I have downloaded, MD5ed and burnt the iso for the 32bit version.
Same problem, sits there for a few minutes at the loading screen and freezes (black screen)
Same with VGA safe mode.

Forgot to mention, I have a bluetooth mouse and keyboard. (Have replaced them with wired for testing)

How easy is it to install without the GUI installer?

---

### Post by sancho panza on 2007-07-16
Ok...sounds like it might be a problem with ur hardware. Try moving your post to the Installation/upgrade forum. The tougher issues stand a better chance of getting solved there.
Hope that helps... :)

---

### Post by ramjet_1953 on 2007-07-16
It sounds very much like it is a video issue.

I know it's a pain, but probably the next thing to try is what is called the alternate cd.

It is a text-based installer and overcomes video card issues as it just uses the legacy driver during the install.

After Ubuntu is installed, you can then load the video driver for your card.

Regards,
Roger :cool:

---

### Post by madlan on 2007-07-17
ok, installed using the alternative/Text based CD.
Everything works fine - untill its reboots for the last time before loading the GUI
Monitor switches off and nothing more!

Anything else I can try?

---

### Post by jimbob on 2007-07-17
I would scour the web for help with getting the 8800 working.

You may be stuck using the vesa driver until more support for the 8800 is forthcoming.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by C.S.Cameron on 2007-07-17
Have you tried ctrl alt f2 when in the black screen?
This might get you into a text window.
The live CD worked fine with my 8800.
Cork

---

