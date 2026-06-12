---
title: "Resolution Help | No selection"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
Hello!

I posted earlier about this, but a solution has not been found.

I have a SCEPTRE screen, which the resolution I used on Windows was: 1680 x 1050.

I want to make this so with Ubuntu, but I don't know where to start. My stats are below.

```
GIGABYTE GV-NX73G128D-RH GeForce 7300GS 512MB(128MB on board) GDDR2 PCI Express x16 Video Card
```

---

### Post by Cilionelle on 2007-06-14
Can you post what you've tried, and any other information you have with you?  That'd help these lovely people out heaps, and if no-one else checks in, I'll be back tomorrow (or later today, or something...!)

---

### Post by alecwh on 2007-06-14
Nothing. I went to Screen Resolution on Ubuntu, but my listing isn't there. My eyes are hurting...

The text just looks stretched, and unnatural.

I have no idea where to start to accomplish this task, can someone weigh in?

---

### Post by wolfen69 on 2007-06-14
copy and paste these into a terminal:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

after that, a semi-graphical window will open, just go step by step(just hit OK throughout the keyboard and mouse setup) and when done, hit ctrl-alt-backspace to log back in.

---

### Post by visible on 2007-06-14
I was having a similar issue where resolutions were in xorg but would not show up in choices in GUI.  I have a an nvidia 7600 GS and am using an 19 in LCD that can go to 1440x990.  I was using the restricted nvidia driver that came with feisty.  what I stumbled upon was a post here that suggested that in terminal type:
```
sudo nvidia-settings
```
this launches the nvidia GUI as root and I discovered that all resolutions were available.  Also this will help anyone that has been wondering why the settings were not saved in the past just launching from the menu.
hoppe this helps.

---

### Post by alecwh on 2007-06-14
If I could find you, visible, I would give you a huge hug.

That solves my problem. :D

---

### Post by visible on 2007-06-14
I'm just glad I could help you out.  It took me almost a week and a fresh install to figure that one out.
enjoy.

---

