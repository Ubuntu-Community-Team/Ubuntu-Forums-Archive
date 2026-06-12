---
title: "Ubuntu not starting anymore!?!?!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-06-20
Hello,

I got quite a lot of important stuff in ubuntu now. I was working in windows for about a week (had no choice) but wanted to go back to ubuntu again to work. The last time when I worked in ubuntu everything worked fine. But now when I start up it says something that the X-server is not configured well and whether I want to see the detailed output. 

After clicking yes and ok a couple times I get some text which says: Timidity is not yet configured. Enable alsa sequencer first by editing /etc/default/timidity.

And after this I get a black line. It's not a terminal window or any option to put in commands in the command line. It just ends with that timidity message. I can type stuff, but when I hit enter I just get another black line. Nothing happens!!

I booted up with the (dapper) live cd, but how can I fix this now? From this live cd I don't think I can change anything on the x-server of the system which is already installed right?

Today I still need to answer some emails!!   Please help!!

---

### Post by atria on 2007-06-20
I'm not exactly sure how it happened automagically, but heres a method to reconfigure your xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

Enter it into your computer's terminal (ctrl-alt-f1)

---

### Post by Happy_Man on 2007-06-20
It says you have to edit /etc/default/timidity. I'm not sure what you need to edit in it, but to access the file, put these commands into the terminal:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/<insert file partition here> /media/ubuntu
```

Then you will be able to access your install.

---

### Post by nikhilpatel on 2007-08-01
I have the same problem.  I just installed Ubuntu last week so I am very new to Linux.  I was tinkering around with adding icons to the "quick launch bar" (I forgot the Linux term for it), and as I inserted one in the black screen showed up and said:

Timidity is not yet configured. Enable alsa sequencer first by editing /etc/default/timidity.

I tried reconfiguring my X server, but that did not get rid of the problem.  It actually changed my resolution since I did not know exactly what I was changing in the settings.  I tried to execute the second suggestion, but I don't understand what the <insert file partition here> means. I'm sorry, but I have trouble understanding the file system in Ubuntu, and I would greatly appreciate some help on this matter.  If I can't fix this problem, I am willing to reinstall, as long as I can backup some of my files to a CD (I only need to save documents and spreadsheets).  However, I don't know how to do that with the terminal since I can't access the GUI.  Any help on any of the issues I'm having would be appreciated.  Thanks!

---

### Post by Happy_Man on 2007-08-02
> **nikhilpatel said:**
> I have the same problem.  I just installed Ubuntu last week so I am very new to Linux.  I was tinkering around with adding icons to the "quick launch bar" (I forgot the Linux term for it), and as I inserted one in the black screen showed up and said:

Timidity is not yet configured. Enable alsa sequencer first by editing /etc/default/timidity.

I tried reconfiguring my X server, but that did not get rid of the problem.  It actually changed my resolution since I did not know exactly what I was changing in the settings.  I tried to execute the second suggestion, but I don't understand what the <insert file partition here> means. I'm sorry, but I have trouble understanding the file system in Ubuntu, and I would greatly appreciate some help on this matter.  If I can't fix this problem, I am willing to reinstall, as long as I can backup some of my files to a CD (I only need to save documents and spreadsheets).  However, I don't know how to do that with the terminal since I can't access the GUI.  Any help on any of the issues I'm having would be appreciated.  Thanks!
When I said, <insert file partition here>, I just meant hda1, hda2, etc. Whatever your Linux system is on. If you don't know, put in the command ```
sudo fdisk -l
``` and see which partition is "Linux". Then go ahead with what I previously posted.

---

