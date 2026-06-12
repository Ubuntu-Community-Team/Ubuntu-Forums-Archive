---
title: "Two Completely Different Questions"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Hydrargyri on 2006-08-09
Hello! I installed Ubuntu yesterday as my first Linux installation, and I have to say its very good, and I love the starting music. However, there are two things that I am rather confused about, despite my searchings online (including this forum).

The first is the resolution of the monitor. I have a widescreen, you see, but the best resolution I can get is not set for widescreen, it seems. Everything seems kinda chubby, so to speak. How can I set the resolution to, say, 1440 by 900 (the resolution I use for windows)? As a note, I did find where I can change the resolution, and the options are... 1280 X 1024, 1024 X 768, 800 X 600, and 640 X 480.

The second is the command line. To clarify, one of the spurs to get me to install Linux was that I need to install a program that's linux-only, and the installation involves some command line stuff. The installation guide starts out by saying "do this, that, and the next thing with the command line". It is a bit clearer than that, I'll admit, but the point is I don't know anything about it. Is the terminal program the one I want to use, and is there a brief tutorial on how to use a command line in general?

Thank you!

---

### Post by kaffelars on 2006-08-09
I don't really know the answer to your first question, at the moment I only have Ubuntu on a laptop where only one resolution is usable ;) 

But yes, the terminal program is what you want.
I did a quick search and found this tutorial:
[http://www.lowfatlinux.com/linux-basics.html]("http://www.lowfatlinux.com/linux-basics.html")

If you don't like it, Google a bit for "bash tutorial" (bash is the default shell in Ubuntu) or "linux shell commands" for instance :)

Good luck!

---

### Post by smile-its-smiley on 2006-08-09
what is your graphic card?

---

### Post by Hydrargyri on 2006-08-09
Its an onboard graphics chip, I believe its Geforce 6100.

Edit: I nearly forgot - Thank you for the link, Kaffelars!

---

### Post by daou on 2006-08-09
If you want to have more resolution options you need to edit your xorg.conf file located in /etc/X11/xorg.conf

In the file you need to find the section marked "Screen"
There should be SubSection "Display" parts for different bit-depths. You probably want to add resolutions for the 24 bit. This is from my xorg.conf:
```

SubSection "Display"
Depth		24
Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
```
Then simply add the resolutions to the Modes line that you want. 
Ex. "1440x900"

Then you need to restart you xserver. Press CTRL+ALT+BACKSPACE. Now you can change to the desired resolution in your screen settings.
That should do it.

---

### Post by daou on 2006-08-09
And you might want to backup your xorg.conf file before doing any changes. XServer will fail to start if you make a mistake. This is nothing to worry about. It will give you an error after which you are taken to the command line. There you can replace the faulty xorg.conf file with your backup (or look for mistakes and fix them). Then you can restart the Graphics Display Manager with the command

```
sudo /etc/init.d/gdm start
```

or if it says gdm is already running type:

```
sudo /etc/inid.d/gdm restart
```

This will take you to the Ubuntu login screen.

---

### Post by Spinelli on 2006-08-09
Here are some great command line guides.

[http://tldp.org/LDP/intro-linux/html/]("http://tldp.org/LDP/intro-linux/html/")
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/]("http://www.tldp.org/LDP/Bash-Beginners-Guide/html/")
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
[http://www.linux.org/lessons/]("http://www.linux.org/lessons/")
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")
[http://linux.org.mt/article/terminal]("http://linux.org.mt/article/terminal")
[http://freeengineer.org/learnUNIXin10minutes.html]("http://freeengineer.org/learnUNIXin10minutes.html")
[http://www.ctssn.com/]("http://www.ctssn.com/")
[http://www.ahinc.com/linux101/toc.html]("http://www.ahinc.com/linux101/toc.html")
[http://www.tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html#toc1]("http://www.tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html#toc1")
[http://www.gnu.org/software/bash/manual/bashref.html]("http://www.gnu.org/software/bash/manual/bashref.html")
[http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html")
[https://help.ubuntu.com/community/BasicCommands]("https://help.ubuntu.com/community/BasicCommands")

I hope some of these help.

---

### Post by kaffelars on 2006-08-10
No problem, Hydragyri!
Happy to help :)

---

### Post by Hydrargyri on 2006-08-11
Well, a few more things have developed, I guess you could say.

Firstly, thank you Spinelli for all those links. They have been quite informative. :D

Secondly, I changed the xorg.conf file to say 1440x900, my ideal monitor resolution, but it simply didn't take. I had saved the file and everything (not just the backup, but the changed one too - only the changed one is in the X11 directory). Is there anything else I can do?

Thirdly, at some point a message popped up saying that there were a lot of updates for my programs (seeing as they were all the ones installed with the OS), so after getting the 160 files, I closed up for the night. Lo and behold, the next day the grub had two new options - ubuntu, and ubuntu safe mode. Essentially, the options were ubunut, ubuntu safe mode, ubuntu, ubuntu safe mode, and windows. That there were four ubuntu items, each paired with an evil twin, is worrying. Should I be concerned?

Thank you all again! :)

---

### Post by RRS on 2006-08-11
Don't worry about the changes to Grub.

One of the updates was to the latest kernal. The old one is still available in case the new one has/creates problems with your setup.

Leave it for now so you can boot into it if need be. Later on you can delete it when you're confident you won't need to run it.

As for you Xorg problem, try editing again, it might work with the upgrades. Otherwise check the laptop support and sound/video sections of the forums, someone with a similar problem may have already found a solution.

---

### Post by UltraMathMan on 2006-08-11
I fixed my widescreen resolution by following [this guide]("http://www.ubuntuforums.org/showthread.php?t=83973&highlight=adding+resolutions")

-Hope this helps :)

---

### Post by daou on 2006-08-13
If you suspect xserver is not using the edited xorg.conf file, you can check which one it is using by looking at /var/log/Xorg.0.log file. Near the top it will say which xorg.conf file is currently in use. 
At some point during 4 days of trying to make the impossible happen with xserver and NVIDIA's TwinView I somehow managed (or xserver/nVidia drivers did it independently) to change the default xorg.conf location from the /etc/X11 folder to my home folder.

---

### Post by Drakkor on 2006-08-13
May I ask the program that you are trying to install ? I guess my point is that a lot of new people think that you need to use the command line to install everything,at least that was my opinion on other linux distros I had come across,but Synaptic or Automatix has tons of programs to easily install or uninstall in Ubuntu. :)

---

