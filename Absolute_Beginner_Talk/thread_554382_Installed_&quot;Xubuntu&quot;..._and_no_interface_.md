---
title: "Installed &quot;Xubuntu&quot;... and no interface loads."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Peffse on 2007-09-18
Boy has this experiment been a mess.... I don't even know if this is the right place to ask these questions. If it's not, kindly redirect me to the right place.

I know this is a long read, but honestly I don't know what I did wrong so I've included everything I've done so far.

Anyhow, on to why I made this thread. I decided to experiment with Linux one day. Trouble being, the only spare machine I have is fairly old, specifically, it's an NEC GT100. Being an NEC machine, it's support is zilch, but I came up with basic specs just from it's BIOS. It's got an AMD K6-2 450MHz processor, with 384MB of PC133 and a 10GB HDD. Everything else is integrated into the motherboard.  The very first stupid thing I did was grab a Linspire CD from my work and installed it... It ran horribly. So I did some research on smaller Linux distributions and basically found only 2. One, of course, being Xubuntu... the other being DSL. Since I heard good things about Ubuntu, and saw that Xubuntu was basically a derivative, I downloaded a Live CD and burned it to a CD.

After formatting the HDD as FAT using a floppy disk, I then popped the CD in and booted from it. It showed it's splash screen, went through the text of loading and everything. But as soon as Xubuntu fully loaded, all I got were 5 icons. Those 5 icons were Install, Foppy, Home, Trash Can, and... uhh... Disk Drive I think. Nothing useful in other words. I knew there was more to it... I've seen screenshots of Xubuntu and it has taskbars and menus and stuff like that. All I had were those 5 icons, and that's all. Figuring I did something stupid, or maybe the disk was bad as a Live CD, I chose the install icon. It hangs at 75% install or something like that.

Ok, so I think to myself "It must be a bad CD". I redownload the image using bittorrent, then I burn another on a different CD brand, use a different burner on a different machine, and check off the Verify CD after burn option so that it double checks the burned CD. That CD passes all tests, but does the same exact thing. I put the CD in my main machine, a Pentium 4 with 1GB RAM and a somewhat modern Geforce FX video card... and it works fine as a live CD. Everything loads and runs at a perfect pace.

So the machine must not meet the requirements, right? I double checked on Xubuntu's page. It meets the requirements, but there is an option to use an alternate CD in this case anyhow. So I download that and burn it. It installs without the live CD portion just fine, loads everything, including the taskbars, and all my options are there. I go off on my merry way messing around and basically familiarizing myself with this new OS. I install a new wallpaper, create a new Abiword document, type up a bunch of stuff and when I was finished I initiate a shutdown. So the machine loads up the Xubuntu mouse splash screen again and shows it's little progress bar of shutting down... but doesn't shut down. The progress bar gets stuck at it's final point and sits there until I manually hold the power button in.

Figuring it was a fluke, and my luck couldn't really be that bad, I turn on the machine the next day. It loads up properly, I go about checking out tools and applications. When the time comes to shut down the machine again, it locks up once again at it's final shutdown point. "Maybe it needs to be updated" is my first thought. So the next day I find the tool to get updates and download and install all the updates. 

Here is where things get weird. Now the machine will not load the taskbars again. Leaving me with only 4 icons.... again. If I start the machine up, I cannot shut it down since I cannot find a shutdown command without the taskbar. The wallpaper is still there, and my document can be accessed and edited by double clicking on it. It will bring up Abiword just fine. But none of the taskbars work. Wait, are they even called taskbars in Linux?

I troubleshoot Windows at work all day, I know there are so many things that this could be... but with Linux being so different, I don't even know where to start. Should I scrap this install and try another distribution? Or is it some hardware in my machine doing this? Could a modern Linux distro even work on my Legacy machine? Maybe there is some silly checkbox that I have unchecked (I hope)?

---

### Post by moffa on 2007-09-18
When you load from a livecd everything is erased upon rebooting.  If you want your settings to save, you have to actually install it.

---

### Post by Peffse on 2007-09-19
> **moffa said:**
> When you load from a livecd everything is erased upon rebooting.  If you want your settings to save, you have to actually install it.
.....Did you even read my post? I already installed it from the alternate CD, that has no Live CD functions. Hence, the title "Installed "Xubuntu".... and no interface loads."

---

### Post by aninaiian on 2007-09-19
So if I understand your post correctly, the panel doesn't load.

Does the Xfce right click menu still work (right click the desktop)?

---

### Post by Peffse on 2007-09-19
Yup, the right-click works and it will let me change a couple of options for the monitor.

---

### Post by aninaiian on 2007-09-19
From the menu, can you launch applications, like the terminal (Accessories -> Terminal)?

If you can, can you run xfce4-panel in the terminal (type xfce4-panel and hit enter in the terminal)?  Hopefully, you'll get a panel.  If you don't, you might get an error which might point you to the problem...

Also does the menu have quit at the bottom?  If it does, you should be able to shutdown from there.

---

### Post by Peffse on 2007-09-19
Nope, I get no options to access anything but those 4 icons and change a couple of monitor settings. I can't shutdown, I can't access the terminal, I can't do anything... well, at least anything intuitive.

---

### Post by aninaiian on 2007-09-19
Okay that makes things a bit harder...

Hit Ctrl+Alt+F2 (F1-F6 should work, but I like F2).  This should throw you into the console.
Login and try to run this
> xfce4-panel --display=:0
This command should launch the panel.

Hit Alt+F7.  This should send you back to the GUI.  You should see the panel.

EDIT: I changed display=:1 to display=:0 as that's more common

---

### Post by aninaiian on 2007-09-19
Oh I forgot there's xfrun.  I'm not sure what the hotkey on Xfce is, but my guess is it's Alt+F2.  From there type xfce4-panel and click run, you should get a panel.  If that hotkey works ignore the prior post.

---

### Post by Peffse on 2007-09-19
> **aninaiian said:**
> Oh I forgot there's xfrun.  I'm not sure what the hotkey on Xfce is, but my guess is it's Alt+F2.  From there type xfce4-panel and click run, you should get a panel.  If that hotkey works ignore the prior post.

using this method, I am able to get the Xfce interface back, but now when I click the shutdown button, it quits Xfce.

---

### Post by Peffse on 2007-09-19
Oops, let me clarify my last statement. 

Running "xfce4-panel" makes the Xfce interface show up, but when it comes time to shut the machine down, the button that normally shuts it down now quits Xfce, and goes back to my blank desktop. Leaving me with no way to safely shut down the computer.

---

### Post by gn2 on 2007-09-19
Seems to be a bug: [https://bugs.launchpad.net/ubuntu/+source/xfce/+bug/94182](https://bugs.launchpad.net/ubuntu/+source/xfce/+bug/94182)
.
Maybe consider Sam Linux if you can't fix it: [http://sam.hipsurfer.com/](http://sam.hipsurfer.com/)

---

### Post by Peffse on 2007-09-19
So it's not something I've done?


Also, what makes Sam Linux any better suited to my machine?

---

### Post by aninaiian on 2007-09-19
I can't comment on Sam Linux as I've never tried it...

However, I can tell you how to shutdown the computer from the terminal...

Hit Alt+F2 and type in xfce4-terminal
In the terminal type this
> sudo shutdown -h now
to shutdown the computer with sudo allowing you to issue the command as root (kind of like a Windows admin), shutdown being the command used to turn off, halt, or reboot the computer, the -h being halt or power down (the system's choice), and now telling the computer when to start to the shutdown process.

If you'd like to reboot then
> sudo shutdown -r now
with the r flag (-r) being reboot (for more on shutdown just type man shutdown in a terminal)

It should ask you for a password which should be your user password.

Also could you try this
> rm ~/.cache/sessions/xfce4-session*
This will remove (rm) all files in the directory /home/youruser'sname/.cache/sessions/ (the ~/ part is a short way of writing your home folder) whose name begins with xfce4-session.

Then you could hit Ctrl+Alt+Backspace which will kill X (what all of the GUI apps on Linux run on top of),  GDM, the login manager, should auto restart itself and X (I think, haven't used stock Xubuntu in awhile).  You should be able to login and hopefully you'll have fully functional panels.  If X doesn't reload just login at one of the terminals and issue the command startx.

---

