---
title: "Unable to Boot Ubuntu 7.04 Live CD"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by doomlord289 on 2007-09-05
My problem started out at the apparently common "/bin/sh: can't access tty; job control turned off" error. I read [this]("http://ubuntuforums.org/showthread.php?t=421588") thread and got the CD to boot...sort of.
Ubuntu started booting again, but then X said it couldn't find a screen.
Does anyone know how I can get Ubuntu working? I really need a real OS. Computer specs below.

Specs:
Dell Inspiron 1720 - Black
Intel Core 2 Duo T7300 (2.0GHz, 800MHz FSB, 4MB L2 Cache)
2GB (2 x 1GB) DDR2 667MHz RAM
2x250GB 5400RPM SATA HDDs
17'' WUXGA (1920 x 1200) screen
256MB nVidia GeForce Go 8600
8x DVD+/-RW DL Drive
Intel 4965AGN Wireless-N Mini Card
Integrated Sound Blaster Audigy
Dell Wireless 355 Bluetooth Mod
85 WHr 9-cell Li Ion Battery
Vista Home Premium
2.0MP Webcam
USB TV tuner + remote

---

### Post by rsambuca on 2007-09-05
Did you check the md5sum prior to burning the cd?  did you run the cd check (if you can get that far?)  What speed did you burn the cd at?

---

### Post by doomlord289 on 2007-09-05
Well I had used the CD on my old computer, a Dell Dimension E310, and it worked just fine.
The md5sum was good
Didn't run the CD check.
Burned at (i think) 48x

---

### Post by rsambuca on 2007-09-05
I know this doesn't make sense, but some of the iso's burned at high speeds contain errors that cause problems on some systems and not others.  I would try burning another CD at a much lower burn rate.

---

### Post by Usbman on 2007-09-05
> **rsambuca said:**
> I know this doesn't make sense, but some of the iso's burned at high speeds contain errors that cause problems on some systems and not others.  I would try burning another CD at a much lower burn rate.

That's exactly what I observed with mine. 

I just burned the cd again at 24x and it installed first time.

---

### Post by o3rat on 2007-09-05
> **doomlord289 said:**
> My problem started out at the apparently common "/bin/sh: can't access tty; job control turned off" error. I read [this]("http://ubuntuforums.org/showthread.php?t=421588") thread and got the CD to boot...sort of.
Ubuntu started booting again, but then X said it couldn't find a screen.
Does anyone know how I can get Ubuntu working? I really need a real OS. Computer specs below.


I just got a new dell too, i couldnt load the Live CD. Instead I used the alternate CD and it booted fine and detected/installed everything fine.

---

### Post by doomlord289 on 2007-09-06
rsambuca: I'll try a lower burn rate, but I haven't had much success burning stuff in Vista. Most (~90%) of my disks error somewhere in the recording process. That includes ISOs, audio CDs, and DVD backups.

o3rat: I want to see how well Ubuntu performs on my laptop before I actually install it, so I need the Live CD.


EDIT:
Well I burned the disk at a lower rate and the same thing happened. This time I wrote down what info I could.

This is what happened after Ubuntu finished loading drivers or whatever it does when you boot it.
A screen with a blue background and a gray dialog box came up saying: "Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
I hit yes.
It gave me a bunch of garbled stuff with some information in it, but I scrolled down and saw this: "Fatal server error: no screens found."
Then I hit OK and it asked me if I wanted to see the detailed output, but after looking at it, it was too long to copy and I had no idea what it meant.
Then after hitting OK this is the message I got: "The X server is now disabled. Restart GDM when it is configured correctly."
Then it shoots me back to a terminal prompt, which is where I shut down and rebooted Windows so I could post this.

Also, when it was loading drivers something relating to video display or something didn't load, but it flew past before I could read or copy it down.

So now what should I do?

---

### Post by doomlord289 on 2007-09-07
bump

---

### Post by philinux on 2007-09-07
burn the alternative live cd which is ,text based .without the graphics then you can sort out the graphics stuff after. probably a problem with your graphics driver

---

### Post by rsambuca on 2007-09-07
For some reason your xorg file is not configuring properly.  Try booting up again, and when it boots you to a terminal, try entering this:```
sudo dpkg-reconfigure xserver-xorg
```you will then go through the configuration manually.  Most of the stuff you can probably just go for the default prompts.

---

### Post by doomlord289 on 2007-09-07
philinux: I want to try Ubntu on this computer before I install it, therefore I need the Live CD. I have the alternative CD, but I can't try anything with it, only install.

rsambuca: trying now, will report back shortly

EDIT:
Reporting back:
I entered the command you told me to and the configuration wizard came up. I selected defaults for everything, then at the end, after I selected my color depth, I got shot back to a CLI saying that it couldn't overwrite the configuration file. Please remember this is still the Live CD.

I also managed to get a quick snapshot of the errors when I booted the disk. I don't think I got the full messages, but I'll post what I have.
> 108.372000] uvcvideo: Failed to query (135) UVC control 1 (unit 0): -32
108.372000] uvcvideo: Failed to initialize the device (-5).
111.164000] hda_intel: azx_get_responce timeout, switching to single_cmd
Then farther down under "*Checking file systems..." I got this (again, probably not the full message):
> at: /var/lib/acpi-support/system-manufacturer: No such file or directory
at: /var/lib/acpi-support/system-product-name: No such file or directory
at: /var/lib/acpi-support/system-version: No such file or directory
at: /var/lib/acpi-support/bios-version: No such file or directory
Those were the only things that looked out of place.

---

### Post by rsambuca on 2007-09-07
Sorry, I forgot that this was still the live CD we were trying to boot up.  The uvc video has something to do with your webcam, and the hda_intel is a sound module, but those shouldnt stop you from getting a display, which means...  most likely a graphics card issue.  It is a newer card and *should* work, but to be honest I have no idea how to do anything with it on the live CD.  Hopefully someone else around here can help you out.  I'll keep looking to see what I can find out, though.

---

### Post by doomlord289 on 2007-09-07
Thanks anyway rsambuca. I'll keep an eye on this thread in case you find something. I'll be looking around as well, so hopefully I can find something.

I was really hoping I could get Ubuntu working because I simply despise Vista and its numerous incompatablities.

---

### Post by GuitarRocker2562 on 2007-09-07
If I were you I would download and burn a gutsy tribe 5 CD and try that, it may work. It is worth noting that it is still not stable, so something could happen, but there is only like a .5% chance of this. Good luck!

---

### Post by doomlord289 on 2007-09-07
I had an idea: try Ubntu 6.06 Live CD (this one I had delivered via ShipIt). I still had the same problem. I guess an older version and professionally made CD still won't get around the problem I'm having, which as rsambuca thinks, is a graphics card issue, and I'm starting to think that too.

---

### Post by cnschulz on 2007-09-08
same here, my screen resolution is not supported 1680x1050.

surely there is a fix!!??

i too want to see what its like before installing.

c.

---

### Post by philinux on 2007-09-08
Ok try booting the live cd in safe graphics mode, its the second boot option I think.

---

### Post by multi-os-guy on 2007-09-08
I have an issue that all I get when booting either of my Ubuntu discs on my Compap Presario F500 is a grey screen that slowly corrupts down to black at the bottom and white at the top.  It's good to watch for a freakout (saves movie-ticket money :) ), but I'd really love to run Ubuntu on it.  Currenly I run OpenSUSE (like others, I despise Vista for program-incompatibility) because it works.  

I'll be looking forward to some kind of fix if it's found!!!  Best of luck, I have too much to work on in my desktop at the moment.  Keep up the fantastic support!

NOTE: I posted here because I think the issues are the same.

---

### Post by doomlord289 on 2007-09-08
philinux: I am posting this from Ubuntu, thanks to your help. There must be something wrong with nVidea cards because my dad's computer has an nVidea card in it and when I tried booting the Live CD I had to use safe graphics mode.  The only difference was that on that computer it told me I had to use safe graphics mode, and I'm using the same CD.
I'm not really taking advantage of my 1920x1200 screen right now because I can only go up to 800x600, which it VERY low for my tastes, but at least I have the Live CD working.
Thank you again.

To anyone else having this problem:
Boot the live cd
when the menu comes up, arrow down to boot safe graphics mode and hit F6
type break=top and hit enter
when the command line interface comes up type modprobe piix and hit enter
then type exit and hit enter
it should boot to the desktop

That was the steps I had to go through to get the Live CD working, but hopefully after I try it for a few weeks I'll install it and be able to deal with all these problems the right and permanent way.


EDIT: Found at least one incompatibility: my speakers don't work, but my headphone port works just fine. I guess that's not too big of an issue, considering my headphones sound better than my speakers. Just thought I'd let people know.

EDIT2: Another incompatibility: microphone isn't working.

---

### Post by doomlord289 on 2007-09-08
I just had an idea: I could install Ubuntu onto my NAS in my dorm room and net boot it whenever I had the urge to play around in Linux. The only problem is I don't know if I can install it to a network share. Does anyone have any ideas on this? I have a SimpleTech SimpleShare STI-NAS/500 500GB NAS in case that's relevant.

---

### Post by magnusbe on 2007-09-08
I tired to do what doomlord wrote, but I've not been able to get to the desktop. I only end up at a command line, and I thought I'm maybe to impatient. How long should I wait for the desktop?

---

### Post by doomlord289 on 2007-09-09
bump
Still wondering if anyone knows how to install Ubuntu to a network share (on a NAS without a CD drive) and then net boot it, or if this is even possible.

---

### Post by rsambuca on 2007-09-09
I assume it is possible.  There is a section in the documentation on server and network installations.  I am sure one of those will work for you.  You can find the instructions [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Installation").

You will find a wealth of information in the documents on all ranges of topics.

---

### Post by lespaul_rentals on 2007-09-09
Just curious, but did you download the Live CD from a mirror such as a university or the like?  Because sometimes it will give you a corrupted download, just enough to cause a problem.

I always download my .iso files as torrents from a tracker like Demonoid.  Not only is it somewhat faster, but when I use uTorrent it verifies that the MD5 hash is correct (I think Azeurus does this too).  Plus I get to help out the community by seeding.  :)

But I think you've got that problem resolved so this might be old news.

---

### Post by doomlord289 on 2007-09-09
magnusbe: are you sure that you arrowed down to safe graphics mode first? Right after you hit enter after typing exit you should load the GUI.

rsambuca: thanks for the link. I'll do more looking around before I post again.

lespaul_rentals: the original disk I downloaded via a university, but the new disk I burned for this thread I got from a torrent on the ubuntu.com website.

EDIT:
I just looked at the link rsambuca posted, and I don't think that's what I'm looking for. I need to boot the CD on my Dell Inspiron and then install it to a network share on a NAS with no CD or floppy drive.

---

### Post by magnusbe on 2007-09-09
doomlord: i did exactly what you wrote, again, but no gui...

---

### Post by doomlord289 on 2007-09-09
well I'm as new to linux as you so all I can suggest is start your own thead and post your computer specs like I did. I'm sorry I couldn't be of any more help.

---

