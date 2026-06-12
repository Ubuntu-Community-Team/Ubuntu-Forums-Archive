---
title: "command line boot file"
date: 2010-09-29
forum: Apple Hardware Users
---

### Post by trj021782 on 2010-09-29
hey quick question, is there file, perhaps similiar to the window autoexec.bat or config.sys files, that would allow me to enter a command line to be executed on boot in ubuntu?

---

### Post by ajgreeny on 2010-09-29
You can add various boot options to the kernel line in grub by editing the grub menu on the fly when it appears, or you can add a default option to the /etc/default/grub file at line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```adding the option in the " " marks at the end, separated by a space, for example ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset noapic"
```

What do you want to do?

---

### Post by trj021782 on 2010-09-30
well i am running 9.10 on a PS3 and in order to get it to boot into 1080p output to match my tv I had to add 

video=ps3fb:mode:133 

to the kboot.conf file. there are parameters I wish to use in conjunction with this to make use of the PS3 "HMDI full range" option. 

The command line to do this is:

ps3videomode -f -c -v 133

-f = fullscreen (not needed with the  kboot line)
-c = full color range for HDMI (the important one)
-v = video mode id (set resolution with a number derived from some simple math)

So since I do not know what will happen if I just add the "-c" trigger to the kboot file and since I don't know what (if any) triggers would be used there i was hoping to find a way to automatically use the command line on boot

***EDIT***

Also is "quiet" used to bypass asking for confirmation? I see that at the end of most of my boot options I was just wondering what it does.

---

### Post by trj021782 on 2010-09-30
> **batteryexpress said:**
> up, got it

I do not understand your post, nor do I see its contribution to this thread - however you name and signature seem to indicate you are actually trying to pump ads into this forum, is this correct?

---

### Post by howefield on 2010-09-30
> **trj021782 said:**
> I do not understand your post, nor do I see its contribution to this thread - however you name and signature seem to indicate you are actually trying to pump ads into this forum, is this correct?

Yes, it is spam, (now removed). Please use the report button when you see it.

---

### Post by trj021782 on 2010-09-30
> **howefield said:**
> Yes, it is spam, (now removed). Please use the report button when you see it.

I suspected as much but I didn't want to report someone on a mistake, I shall be less shy in the future

---

### Post by trj021782 on 2010-10-03
I figured it out, rc.local in /ect/init.d folder will execute command lines at boot

---

