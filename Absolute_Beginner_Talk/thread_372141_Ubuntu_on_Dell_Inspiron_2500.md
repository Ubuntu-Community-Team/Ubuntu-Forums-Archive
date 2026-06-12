---
title: "Ubuntu on Dell Inspiron 2500"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by ss_mckinney on 2007-02-27
Hello all,

I have an old Dell Inspiron 2500 laptop that I'm trying to install ubuntu on.  At startup, I am always greeted with the same option of choosing Windows XP or 2000.  Even when I have a working 6.10 disk inserted into the drive.  I know it's not a faulty disk because I used the same disk to install it on an even older desktop that I have.  Installing it on the desktop was a breeze.  I guess I'm just wondering why the laptop isn't recognizing the disk at startup?

Any advice would be greatly appreciated.

Thanks
S

---

### Post by overdrank on 2007-02-27
> **ss_mckinney said:**
> Hello all,

I have an old Dell Inspiron 2500 laptop that I'm trying to install ubuntu on.  At startup, I am always greeted with the same option of choosing Windows XP or 2000.  Even when I have a working 6.10 disk inserted into the drive.  I know it's not a faulty disk because I used the same disk to install it on an even older desktop that I have.  Installing it on the desktop was a breeze.  I guess I'm just wondering why the laptop isn't recognizing the disk at startup?

Any advice would be greatly appreciated.

Thanks
S
Hi check your bios to set the boot to cd.

---

### Post by oilchangeguy on 2007-02-27
make sure the bios is set to boot from the cd drive.
arrg not fast enough. LOL!

---

### Post by overdrank on 2007-02-27
> **oilchangeguy said:**
> make sure the bios is set to boot from the cd drive.
arrg not fast enough. LOL!
I was thinking the same LMAO

---

### Post by ss_mckinney on 2007-02-27
OK...Thanks.  That seems to be working.

---

### Post by overdrank on 2007-02-27
> **ss_mckinney said:**
> OK...Thanks.  That seems to be working.

Glad WE could help. :)

---

### Post by ss_mckinney on 2007-02-27
Update:  There are a bunch of B/W static vertical lines and a few blinking dancing horizontal lines on the screen as it seems to be installing.  They've been there for several minutes.  Is this to be expected?  How long?

---

### Post by oilchangeguy on 2007-02-27
no it's not normal. sounds like a video card issue. please advise your computers specs. and is it on board video? or pci card? your computer probably won't run 6.10. you may need to consider xubuntu.

---

### Post by overdrank on 2007-02-27
> **ss_mckinney said:**
> Update:  There are a bunch of B/W static vertical lines and a few blinking dancing horizontal lines on the screen as it seems to be installing.  They've been there for several minutes.  Is this to be expected?  How long?
I just looked up the specs on that machine. How much memory do you have installed?

---

### Post by ss_mckinney on 2007-02-27
128 for memory I believe.

---

### Post by overdrank on 2007-02-27
> **ss_mckinney said:**
> 128 for memory I believe.
Then you have the min to do a install. You did say that you have used the cd before? Live dvd or the alternate?

---

### Post by oilchangeguy on 2007-02-27
if you've got on board video it's using system ram. so the computer has access to less than 128mb of ram.

---

### Post by ss_mckinney on 2007-02-27
Live CD.  It was on another machine though.  An old Micron PC.

---

### Post by overdrank on 2007-02-27
> **oilchangeguy said:**
> if you've got on board video it's using system ram. so the computer has access to less than 128mb of ram.

True did not consider that on the laptop, YOu are right!

---

### Post by overdrank on 2007-02-27
> **ss_mckinney said:**
> Live CD.  It was on another machine though.  An old Micron PC.

If you can check the bios again and turn down the shared video ram to 8mb then it might install!

---

### Post by ss_mckinney on 2007-02-27
OK, I'm in the Bios menu.  I'm not sure how to turn down the video memory or whatever.

Am I better off just trying xubuntu?

---

### Post by overdrank on 2007-02-27
> **ss_mckinney said:**
> OK, I'm in the Bios menu.  I'm not sure how to turn down the video memory or whatever.

Am I better off just trying xubuntu?

Well its should been seen as video shared memory. That about xubuntu I am unsure of the min requirements on that.

---

### Post by oilchangeguy on 2007-02-27
i'd just go with xubuntu. because 128 is the bare min. to run 6.10. so it will probably be very slow. whereas xubuntu is designed to run on older, low powered computers.

---

### Post by ss_mckinney on 2007-02-27
Alright, I'll try that tomorrow night.  Thanks, you guys!

---

### Post by igknighted on 2007-02-27
Make sure you download the alternate CD as well, the live CD requires 256 mb to load.

---

### Post by ss_mckinney on 2007-02-28
The alternate CD for Xubuntu?  Or Ubuntu?

---

### Post by Frak on 2007-02-28
> **ss_mckinney said:**
> Update:  There are a bunch of B/W static vertical lines and a few blinking dancing horizontal lines on the screen as it seems to be installing.  They've been there for several minutes.  Is this to be expected?  How long?
Yes that happens on my Inspiron 2500 also, the Intel Video cards that shipped with it aren't Fully supported in Edgy, also your loading bars will be invisible...

Normal

EDIT
And did you think about trying Fluxbuntu, it runs on VERY LITTLE RAM! Almost none at all IMO.

---

### Post by frisket on 2007-03-07
> **oilchangeguy said:**
> no it's not normal. sounds like a video card issue. please advise your computers specs. and is it on board video? or pci card? your computer probably won't run 6.10. you may need to consider xubuntu.

I have exactly the same problem (strobing bands) while Edgy tries to load from the CD before it can start installing (the initial splash screen comes up OK and I tried to pick VGA but it's not clear if that worked or not).

Are there any boot parameters that I can give to force the system into lowest-common-denominator state?

It's an Inspiron 2500 with (according to the installed XP details) an Intel 82815 and an 800x600 LCD.

///Peter

---

### Post by frisket on 2007-03-07
No need -- the Alternative CD has a text-mode installer which is running fine.
A pity about the network card not being recognised though.

---

### Post by frisket on 2007-03-08
> **Frak said:**
> Yes that happens on my Inspiron 2500 also, the Intel Video cards that shipped with it aren't Fully supported in Edgy, also your loading bars will be invisible...

Is the 82815 fully supported in *any* Linux distro? I'd prefer Ubuntu, but I'll install whatever it takes...

[/QUOTE]And did you think about trying Fluxbuntu, it runs on VERY LITTLE RAM! Almost none at all IMO.[/QUOTE]

If that doesn't solve the video card problem then it's not an option...

///Peter

---

### Post by Frak on 2007-03-08
> **frisket said:**
> Is the 82815 fully supported in *any* Linux distro? I'd prefer Ubuntu, but I'll install whatever it takes...

> And did you think about trying Fluxbuntu, it runs on VERY LITTLE RAM! Almost none at all IMO.

If that doesn't solve the video card problem then it's not an option...

///Peter
Yeah, but Inspiron 2500's come with little RAM in the first place, mine came with 256MB, lowest is 126, and highest is 256. Just a suggestion.

And, no, the video card is not fully supported in any linux distribution at the moment.

---

### Post by rbo83 on 2008-02-02
It works fine with the live knoppix cd if you add the following parameters to the boot options :

vga=0 screen=800x600

---

### Post by boltorg on 2008-05-30
Fix for 1024x768

_[Thread]("http://ubuntuforums.org/showthread.php?t=750372")_

---

### Post by alan tait on 2008-05-30
Don't know if this is any help, but on my Dell Latitude D505, at bootup, the login screen is always slightly offset upwards with random green colours below. I just close and re-open the screen and it's all back to normal. Not worth fixing, really.

---

### Post by grw on 2008-06-12
Just thought I'd share my experiences running Ubuntu on my Inspiron 2500. Been doing so for several years - I started with 5.10 and now I am running 8.04 (fresh install - though I have upgraded in the past without difficulties).

On the whole I have had few problems. The biggest one was due to insufficient RAM. When I first converted to linux (Suse actually) I only had 128mb of RAM and the computer ran extremely slowly. I added another 256 and this solved the problem.

I have had recurring trouble with the computer shutting off suddenly. Turning off ACPI seems to fix it. I added &#8220;acpi=off&#8221; between the &#8220;ro&#8221; and the &#8220;quiet&#8221; in /boot/grub/menu.lst

With 8.04 I was initially only able to get a screen resolution of 800x600. There&#8217;s a fix above to get it up to 1024x768, although I copied the monitor and screen section from the first post here: [http://ubuntuforums.org/showthread.php?t=159118](http://ubuntuforums.org/showthread.php?t=159118)  pasting them into /etc/X11/xorg.conf. DefaultDepth of 16.
I also tried "gksudo displayconfig-gtk" in a terminal. It will open up a gui that edits your xorg.conf file. Try selecting generic 1024x768 panel monitor. Under graphics card, manually select Intel 815.
Control ALT Backspace will restart X, go to &#8216;Monitor resolution&#8217; in the preferences and select 1024x768.

Apart from that, I have had very few problems with Ubuntu on my machine.
Insprion 2500 specs are here: [http://www.webmadeeasy.net/ComputerDocs/Dell/Insprion/2500/ServiceManual/specs.htm#1000450](http://www.webmadeeasy.net/ComputerDocs/Dell/Insprion/2500/ServiceManual/specs.htm#1000450)

---

