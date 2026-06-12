---
title: "freeze at login"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by unisol on 2007-06-28
i just installed feisty and all went well. the system restarted and froze at the login screen. p3 384mb mem, nvidia geforce fx 5500. winxp hda1,etch hde3 feisty hde4, linuxmint(cassandra) hde7. could it be a video driver?

---

### Post by iver2435 on 2007-06-28
Does it hang after you've input your username and password and it's trying to authenticate you, or does it hang as soon as the login screen is displayed?

---

### Post by Scunizi on 2007-06-28
If you have a DVD installed in your system you may need to add irqpoll to the end of the "kernel" line in /boot/grub/menu.lst file..

---

### Post by unisol on 2007-06-28
iver2435, it freezes at the login screen. you dont even get to sign in. its a brand new install, i never even got to the desktop.

---

### Post by Scunizi on 2007-06-28
if you can boot into the "rescue" or recover mode, you'll get a text display without a gui.  You can log in there using your normal user name and password.  Now type "sudo nano /boot/grub/menu.lst" (those last three characters are LST, but they have to be lowercase).  Hit enter.  You should be in a text editor.  Use the arrow keys until you find a line without a "#" in front of it that begins with "Kernel".  Pay attention because the Kernel line may wrap to the next line.  If it doesn't wrap, the next line down should begin with "initrd".  At the end of the Kernel line make sure there is a space then type "irqpoll".  Don't hit enter, don't use the quotes (").  Now push and hold CTRL+O (that's oh not zero), hit enter then CTRL+X to exit.  Reboot and see if it works. 

I'm sorry, beyond this I'll be stumpted.

---

### Post by iver2435 on 2007-06-29
If the above doesn't work, then get back into the text mode and type:

```
dmesg
```

This will show you a log of your last boot-up cycle, allowing you to look to see if any services or apps are failing.

If you want to redirect this to a file in your home directory, type:

```
dmesg > ~/bootlog.txt
```

This way you can search it at your leisure.  I would look for keywords in the file like "fail", "not", "unsuccessful" and see what comes up. 

Hopefully this data mining will lead to a nugget or two.  :)

---

### Post by unisol on 2007-06-29
thanks for your help. it started up with no problems today. but i will use the tool as you said . try to find out why. again thanks for your help.

---

### Post by unisol on 2007-07-15
this is what someone told me to try when linux freezes:First, we&#8217;ll try and kill all the process on your current terminal. To do this, hold down the following keys -

ALT + SysReq + k


What the heck is a SysReq key? Look for it on your PrtSc or Print Screen key. The k in this instance stands for Kill.

If that doesn&#8217;t work for you, it&#8217;s time to take drastic action. You&#8217;ll now enter a series of keystrokes that will tell your computer to do some housekeeping before shutting down.

ALT + SysReq + r

This stands for Raw keyboard mode.

ALT + SysReq + s

This syncs the disk.

ALT + SysReq + e

This terminates all processes

ALT + SysReq + i

Kill&#8217;s all processes that weren&#8217;t terminated nicely.

ALT + SysReq + u

Remounts all filesystems as read only.

ALT + SysReq + b

reboots

Raising Skinny Elephants Is Utterly Boring - RSEIUB
i havent had much reason to use it lately, but if it works, i guess it could help someone.

---

### Post by jamestrowbridge on 2007-07-24
Thanks, I've been fighting with this thing.  I couldn't login with recovery mode or whatever, but I edited the kernel line right out or the grub menu with the " irqpoll " at the end and it booted up just fine.  Logged in and all that.  Thanks again.

---

### Post by unisol on 2007-07-25
that didnt work for me. i think im going to have to blacklist the rt61 drivers, and install the wireless drivers using ndiswrapper.

---

