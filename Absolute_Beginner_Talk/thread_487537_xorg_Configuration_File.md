---
title: "xorg Configuration File"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2007-06-29
Good day All,  and Thanks In Advance
I have a problem that stops me from booting into Ubuntu (Windows XP works), the error message received: “Failed to start the X Server (your Graphical interface)” I caused this problem when I tried to change the monitor Display Resolution and I failed.  I have read many post on this subject/problem, the more I read the more confused I get.
I used the command “sudo dpkg-reconfigure xserver.org” leaving mosts of the selections as shown  as the defaults except for Monitor and Graphics details.
When I re-booted the computer after the above changes, everything appeared normal until nearly through the Ubuntu Splash screen load bar when it bombed out.
I logged in as kevin@kevin-FunCo: entered my password: and tried to edit the xorg.conf file after reading the reasons why the boot failed.   The command I used to try and correct the display errors in the xorg.conf file was:
sudo gedit /etc/X11/xorg.conf  - received the following errors
“cannot open display”
“run 'gedit –help' to see ...........”

What I need is help to rectify the error:
How do I edit the xorg.conf file from the command-line or how can I use the backup file to replace this xorg.conf file.   Both of these files are in the /X11 directory.
System Specs:
Computer Intel P4,  1Gb Ram
Dual Boot:   Ubuntu kernel 2.6.20-16-generic and Windows XP Home on separate hard drives.
2 x 80Gb drives partitioned for Operating System and data storage
Both Operating System are current with the latest updates.
Monitor:  BenQ FP92W LCD
Graphic card:  Nvidia Geforce2 MX/MX400

This is where I think I stuffed-up with my selection when using the “sudo dpkg-reconfigure xserver.org”  whether I should of entered the Graphics card name in full or  NV00/NV11  or just NVIDIA or something else.

Thanks,
Old Kevin

---

### Post by hyper_ch on 2007-06-29
> 
sudo nano /etc/X11/xorg.conf


Exit nano with
```

ctrl+x

```

You will then be asked if you want to save the altered file and if you want to give it a new name.

Or replace it with a backupfile:

```

sudo cp /path/to/backup/xorg.conf /etc/X11/xorg.conf

```

---

### Post by NilsE on 2007-06-29
NANO is a good editor for the terminal since it emulates a full screen but you still have to cursor to the line you are editing but works well. Gedit did not work because it is a gui which you don't have with the xorg failure.

As far as which monitor try either nvidia or just nv . If one does not help try the other.

If you want to try the reconfigure again try it this way:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then try both in it also.  Make sure you select one or more resolutions that your monitor supports.

By the way, the -phigh is added so you only have to go through the display related questions.

---

### Post by molly_001 on 2007-06-29
Note:  The "priority high" switch on the command given in the previous post often causes xorg to lock up on older machines.  I don't know why.  Just remove it if it gives you grief as typed above.

---

### Post by Kevin Funnell on 2007-06-30
Thank for the help, I am now online using Ubuntu and a good display resolution.

As far as I am concerned My Post is Resolved.

Thanks again,

Old Kevin

---

### Post by NilsE on 2007-06-30
> **Kevin Funnell said:**
> ar as I am concerned My Post is Resolved.

Thanks again,

Old Kevin

Cool

Do you know which fixed it? It would help others to know.

---

### Post by Kevin Funnell on 2007-07-01
Hi All that Help me,

I used the code suggested by hyper_ch:  [COLOR="Blue"] sudo nano /etc/X11/xorg.conf[/COLOR] and corrected areas were I had errors,  I keep going back to the xorg.conf.20070629162813 (backup file) and used this file in correcting the errors, re booting after each change I made.   

When I was happy with the chances I used NilsE suggestion [COLOR="Blue"] sudo dpkg-reconfigure -phigh xserver-org [/COLOR] answered the prompts,  followed the on-screen prompts, save etc.   

After re-boot I had many more Display Resolution options than I though I had highlighted.  Tried one (1440 x 1024) above my monitor maximum (1440 x 900) recommended it worked except I had to scroll up & down to see all displayed info.  I happy now and don't intend changing anything.

Thanks again & how this answered the question.

Old Kevin

---

