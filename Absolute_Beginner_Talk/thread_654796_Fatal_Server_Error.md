---
title: "Fatal Server Error"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by mschoenfeld on 2007-12-31
Hi All,

I installed Ubuntu Gutsy yesterday on my laptop as a dual boot.  Everything was working fine, but now i cannot access the GUI at all.  I can login via terminal but when i try and run the UI, i get the following error:

Fatal Server Error:
no screens found
XI0:  Fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processes) with 0 events remaining.

Please help =)

Thank,
Michael

---

### Post by mschoenfeld on 2007-12-31
Has anyone received a similar message?  I'd like to login to my computer hehe.
I also see failed to load fglrx module, do i just need to re-install that?

---

### Post by tgilber1 on 2007-12-31
Can you provide graphics chipset, /etc/X11/xorg.conf and log files (/var/log/gdm/*.log with error message?  

Note *.log means all the gdm log files with error message, which will give us some clue.  

If nothing is in these files.  you can try the steps below to get more detail from your Xorg.0.log file.  Because failsafeXServer starts after boot up, the Xorg.0.log file will show you last attempt.  Hence, it may not show you the bootup from the original xorg.conf file.  The directions below show how to diable the failsafeXserver in Ubuntu.

1.  Make a copy of the /etc/gdm/gdm.conf file # ex. sudo cp /etc/gdm.conf /etc/gdm.conf.bak

2.  Disable the failsafeXServer script in the /etc/gdm/gdm.conf by commenting out the failsafeXserver line with a pound sign#.  ex. #FailsafeXServer=/etc/gdm/failsafeXServer

3.  Restart Xserver by /etc/init.d/gdm restart or reboot computer.

4.  View your Xorg.0.log file, which should provide you more details on why your Xserver is failing.  Post failure in Xorg.0.log file, if you cannot figure out.

---

### Post by mschoenfeld on 2007-12-31
Will do, it may take me a while, because i cannot actually use the laptop.  I'm on my desktop.

---

### Post by mschoenfeld on 2007-12-31
Acer Aspire 5102WLMi
AMD Turion 64 x2 Mobile TL50
ATI Radeon Xpress 1100

When i use the following command: 
```
sudo gedit /etc/X11/xorg.conf 
```

I get cannot open display, same with xorg.0.log.

Any Ideas?  Also the files are larger then i thought, i can't copy and paste, so any specific segment you need?  Also not sure how to edit gdm.conf the best.

---

### Post by mschoenfeld on 2007-12-31
Is there a way to revert back to original graphic drivers?

---

### Post by tgilber1 on 2007-12-31
You can only use gedit via the GUI, i.e. Gnome.  Hence, try giving zmore or vi a shot to read the files.  Additionally, these files have read access for all users,thereby eliminating the need to use sudo for reading.

---

