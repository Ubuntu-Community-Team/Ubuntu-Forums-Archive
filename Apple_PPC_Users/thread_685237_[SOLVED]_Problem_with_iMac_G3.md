---
title: "[SOLVED] Problem with iMac G3"
date: 2008-02-02
forum: Apple PPC Users
---

### Post by Yochanan on 2008-02-02
I just installed Ubuntu 7.10 Gutsy Gibbon PPC Alternative on an iMac G3 400 MHz 64 MB RAM 10 GB HDD. After the installation it popped the CD out and I rebooted. It says, "Loading, please wait..." for quite a while, then it dumps me to a Busyboot prompt. I read a FAQ that said to type "modprobe ide-core" then "exit", and it continues to boot and goes to the login screen. After I login, it loads a background and the top and bottom bars are white. Then finally I get a dialog box that says there was an error loading Gnome Settings Daemon. I can click close, but nothing happens after that. I tried hitting Ctrl+Alt+Backspace, and it doesn't help, the same thing happens. I'm using a Dell USB keyboard and a Microsoft USB optical mouse by the way, I don't have a Mac keyboard or mouse. Mac OS 8.6 was originally on it, and the date was 1904. I read somewhere that resetting the clock could help, but I have no idea how to do this. Anyone have any ideas?

---

### Post by Midwest-Linux on 2008-02-02
64 MB isn't enough Ram for Ubuntu, If you have a slot loader...the Ram is located on the bottom of the computer in a small hatch. If you have a older tray loader, your RAM is located internally and much more complicated to replace. 



Replacing memory in a older tray loader

[http://docs.info.apple.com/article.html?artnum=43012](http://docs.info.apple.com/article.html?artnum=43012)

[http://docs.info.apple.com/article.html?artnum=43013](http://docs.info.apple.com/article.html?artnum=43013)


Replacing memory in a slot loader

[http://docs.info.apple.com/article.html?artnum=95144](http://docs.info.apple.com/article.html?artnum=95144)

---

### Post by Yochanan on 2008-02-02
Can anyone suggest a Linux distro that will work on this? (see specs in first post).

---

### Post by Midwest-Linux on 2008-02-02
> **Yochanan said:**
> Can anyone suggest a Linux distro that will work on this? (see specs in first post).


 Do you have the slot loader? The CD slides right in as opposed to the older tray loader IMAC.


If so there should be a hatch on the bottom of the computer...(turn it upside down)... It uses PC 100 Ram -Non ECC -SDRAM which is selling on E-Bay for about $7 for 128 MB RAM...I recommend at least 256 MB RAM or better.

---

### Post by Yochanan on 2008-02-02
It's a slot loader. But what about this bug?
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

I tried to open the panel, but it won't open. The lock symbol is on the left, unlock on the right. The screw thing in the middle can turn all the way to the left toward the lock symbol. When I turn it to the right toward the unlock symbol, the screw thing stops halfway with the notch vertical. I can't turn it to the right any farther than that. I've looked at the manual but it's opposite and shows turning it left opens it. What the...?

---

### Post by stream303 on 2008-02-02
With really low memory systems, you CAN get something going, so don't trash those low memory systems just yet. :)

What you do basically is install a text-mode only system as a start, and then add xorg and a simple window manager after install.  I have done this a few times with Debian net installer on my PPC's.  I really liked Fluxbox as my window manager, but there are plenty others.

The following should help, even though it seems pc-based, it applies to ppc just as well:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Once you get your text-based Ubuntu system loaded, and your /etc/apt/sources.list properly uncommented for your area, you are a "sudo apt-get install xxxx" away from putting it all together.

Look for text-based alternatives that can also run in a graphical terminal, such as HTOP, or download vorbis-tools and listen to streaming ogg audio with a terminal command such as:

```
ogg123 http://radio.hbr1.com:19800/ambient.ogg 
```

Sure, you could download movie player and it might work for streaming audio as well, but might tax your resources.  Htop will show you.  You get the idea.

You don't always need more ram to make a rockin' ppc box! :)

---

### Post by Yochanan on 2008-02-02
Turns out it Gnome wasn't loading because of having only 64 MB of RAM. I wrestled the stupid panel off and added another 64 MB stick. I booted back up, and Gnome loaded. I still got the error message, but the taskbar actually loaded this time. I found two 128 MB sticks, so I'll try those after it's done updating. Thanks guys for the advice.

---

### Post by stream303 on 2008-02-02
At this stage, I'd be tempted just to reinstall fresh now that you have the new ram.  Might save yourself a lot of trouble later.  Or so I've heard.  Avoid the pain and reinstall. :)

---

### Post by Yochanan on 2008-02-02
I'm not sure what you're getting at. What have you heard?

---

### Post by stream303 on 2008-02-02
Well, the swap partition must be changed to reflect the new amount of ram, typically 1 to 1.5 to 2 times ram.  Ooops, gotta break out fdisk, parted, or gparted to resize your swap partition.  It can be done of course.

I can only imagine that some auto-configured config files assume that all they get is what the amount of ram was at initial install, and will continue to use that old value unless you go in and manually check and edit them.

I'm just saying at this early stage of the game where you have nothing to lose, just reinstall  if you change your ram, especially if you let Ubuntu do the guided partitioning and auto configuration.

My crystal ball says that this is the easiest way to go.. :)

---

### Post by Yochanan on 2008-02-03
I reinstalled with 256 MB RAM, and it works a lot better. However, after I login, I get the Gnome Settings Daemon error. It says it failed to start because it restarted too many times. I've searched the forums and tried a couple things, but it still happens. I can't open the Sound Preferences, Add/Remove, Totem or Rhythmbox. Themes don't work quite right, either. Any ideas?

---

### Post by stream303 on 2008-02-04
> **Yochanan said:**
> However, after I login, I get the Gnome Settings Daemon error. 

Hmm. take a look here:

[https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)

Solutions seem to go all over the place from disabling ESD in sound prefs, to reconfiguring your networking?  wow.  Maybe???

---

### Post by Yochanan on 2008-02-08
Is there a way to disable ESD via the terminal? Sound Preferences won't load and the tray icon doesn't appear, so maybe the cause has somethig to do with that?

---

### Post by guidop on 2008-02-08
If the date at power on says 1904, then your iMac may also need a new PRAM battery.

See this post and associated thread:

[http://ubuntuforums.org/showpost.php?p=3555423&highlight=PRAM+battery](http://ubuntuforums.org/showpost.php?p=3555423&highlight=PRAM+battery)

---

### Post by Yochanan on 2008-02-09
I was able to change the date. I just formatted and installed Feisty, and all was well after installation. I applied all the updates and rebooted, and now after logging in nothing happens. I just have a tan background. I thought updates were supposed to fix things, not break things. Of course Gutsy is an upgrade, and that didn't work well, either. Any ideas?

---

### Post by stream303 on 2008-02-09
I'd check that date again in another terminal just to be sure..

From the KnownIssues Wiki:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

```
Gnome wont load
Date wrong

If the system clock is set before 1970 Gnome will not start. See UbuntuDateBug
Sound problems

There is a kernel bug that causes processes play sounds to hang. When Gnome plays its startup sound it hangs. You may hear the first fraction of a second of the sound.

Press CTRL+ALT+F1. Log in at the text terminal, if needed. Type

killall esd

and press enter. Press CTRL+ALT+F7 to return to the desktop. Go to Gnome's Sound Prefs and uncheck the 'ESD' box, this will allow stop the hang in future log ins.
```

Anything?

---

### Post by VCF on 2008-02-09
> **Yochanan said:**
> I was able to change the date. I just formatted and installed Feisty, and all was well after installation. I applied all the updates and rebooted, and now after logging in nothing happens. I just have a tan background. I thought updates were supposed to fix things, not break things. Of course Gutsy is an upgrade, and that didn't work well, either. Any ideas?

I'm now trying to skip ahead a version to Hardy, since the update button to Gutsy has been poison to my system.  Since we have almost exactly the same systems, whatever get fixed for one of us should work for the other.  I'll be watching your thread and stream303's Hardy on a G5 thread.

---

### Post by Lokesh731 on 2008-02-11
> **VCF said:**
> I'm now trying to skip ahead a version to Hardy, since the update button to Gutsy has been poison to my system.  Since we have almost exactly the same systems, whatever get fixed for one of us should work for the other.  I'll be watching your thread and stream303's Hardy on a G5 thread.

Did you reset the PRAM? In my experience, once trouble starts with an empty battery or RAM, fixing it is not sufficient. Try alt-apple-P-R and wait for three consecutive startup chimes.

---

### Post by Yochanan on 2008-02-11
Everything is working fine now, don't ask me why. I turned it off after what happened in my last post. The next time I turned it on, I got no Nautilus error and everyhing worked perfectly. Thanks everyone who added to this thread. This is one of the reasons I keep trying to learn Linux (namely Ubuntu). This wonderful forum! :D

---

### Post by VCF on 2008-02-12
> **Lokesh731 said:**
> Did you reset the PRAM? In my experience, once trouble starts with an empty battery or RAM, fixing it is not sufficient. Try alt-apple-P-R and wait for three consecutive startup chimes.

Yup I tired that trick on your suggestion but it didn't help at all, same problems (freezing at Gnome with some error message that never shows the text).

---

### Post by VCF on 2008-02-12
> **Yochanan said:**
> Everything is working fine now, don't ask me why. I turned it off after what happened in my last post. The next time I turned it on, I got no Nautilus error and everyhing worked perfectly. Thanks everyone who added to this thread. This is one of the reasons I keep trying to learn Linux (namely Ubuntu). This wonderful forum! :D

Wow, some magic fairy must have come by and blessed it! 
 I must be getting the same problem as you as I (last night again!) installed Feisty (everthing OK) upgraded with the button after doing all the updates.  

Got a frozen screen with the blank (undrawn text) error message.  And gee I thought our machines were identical so what happens to yours should happen to mine.
ARRGH!

---

### Post by Yochanan on 2008-02-12
> **Lokesh731 said:**
> Did you reset the PRAM? In my experience, once trouble starts with an empty battery or RAM, fixing it is not sufficient. Try alt-apple-P-R and wait for three consecutive startup chimes.

I'm glad I didn't have to, as I don't have a Mac keyboard or mouse. I'm using a Dell USB keyboard and a Microsoft optical USB mouse. I changed the date with the command: ```
date -s "12 feb 2008 20:49:00"
```

---

### Post by VCF on 2008-02-13
> **Yochanan said:**
> I'm glad I didn't have to, as I don't have a Mac keyboard or mouse. I'm using a Dell USB keyboard and a Microsoft optical USB mouse. I changed the date with the command: ```
date -s "12 feb 2008 20:49:00"
```

Hmmm...maybe I'll swap the keyboard and mouse to some PC stuff.  

Although I think it is in the video our respective machines use.  My iMac (Summer 2001 Indigo) has a Rage 128 Ultra chip in it.  Your iMac 400 would have either a Rage 128 Pro or Rage 128 VR (I think the GL was just in the Powermac G3??).

Can you tell me which model of iMac 400 (there were 4) you have?

Many thanx!

---

### Post by Yochanan on 2008-02-13
See my sig. ;)

---

### Post by stream303 on 2008-02-14
Have you guys tried some of the ATI tweaks for PPC in the faq:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

I think you both have an AGP 2X capable card...  R128 driver vs ATI, frambuffer false etc...

---

