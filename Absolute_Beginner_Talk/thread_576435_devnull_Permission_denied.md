---
title: "/dev/null: Permission denied???"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Partyboi2 on 2007-10-15
When booting into feisty I get the following message:

Could not start the x server (your graphical environment)
due to some internal error
please contact your system administrator
or check your syslog yo diagnose.
In the mean time this display will be disabled. Please restart GDM when the problem is corrected.

After hitting ctrl+alt+F1 and trying to log in I get this error message:

-bash: /dev/null: Permission denied

I tried editing /etc/rc.local with:

chmod 666 /dev/null

and rebooted but still the same problem
How can I fix this problem so I can boot up feisty?
And what has cause this to happen in the first place?

---

### Post by cmnorton on 2007-10-15
This sounds like something your bash shell is processing is causing this error. 

I had this happen -- with a different error -- when I installed a commercially available backup agent onto Red Hat 9. With Red Hat 9, there was an "errno" warning that popped up anytime the C runtime library was accessed. It was just a warning, not an error.

This backup agent was called out of /etc/bashrc, and wound up causing the bash shell to choke, upon logging in. It did not prevent login though.

---

### Post by Partyboi2 on 2007-10-15
I tried ls -l /dev/null
and got:
crw-rw---- 1 root,root 1,3

So I chmod 666 /dev/null
and changed it to how I think its meant to be which looks like:
crw-rw-rw-rw-

But when I reboot it just changes back to the crw-rw---- one
How do I stop this from changing every time I reboot?

Then when I try to startx again I get errors saying:
/usr/bin/startx (read only file system)
How do I change it from read only file system?

Any help would be appreciated thanks

---

### Post by twiceasworn on 2007-10-15
Ok if you are getting a read-only file system error that is due to some problem at boot.  Ubuntu mounts the file system as read only if it encounters an error on boot (so to minimize the possibility of damaging the filesystem from said error). I suggest booting into recovery mode.  Once you get to a terminal try a 
```

sudo mount -o remount,rw /
```

Of course that doesn't fix the issue it is having at boot, so I would suggest trying to figure out what is throwing it into read-only.  For me it was because I fat fingered my /etc/fstab, so once I fixed it after making it writable everything was hunky dory.

---

### Post by schorsch on 2007-10-15
What is the output of
```
grep null /etc/udev/rules.d/*
```

---

### Post by Partyboi2 on 2007-10-15
grep null /etc/udev/rules.d/*

/etc/udev/rules.d/40-permission.rules:KERNEL=="null",ODE="0666"

I have also tried to boot into recovery mode, but I am unable to log in as when it comes to login in it is not in english, instead it is in strange looking characters. The only way I can get a log in screen is if I boot normally and use ctrl+alt+F1 then ctrl+C after I get the permission denied error. I have tried[FONT=monospace]:
sudo mount -o remount,rw /
But I get a error message:
Can't find ,rw / in /etc/fstab or /etc/mtab
Have looked at the fstab and mtab file and they seem normal to me
[/FONT]

---

### Post by Partyboi2 on 2007-10-16
Not matter what I try I am an unable to get the file system to read/write even when I try:
 mount -o remount,rw / 
is there any other way to get my file system to be r/w? So I can start x????

---

### Post by drascus on 2007-10-16
Did you cange a setting in gdmsetup that might have caused an issue?

---

### Post by Partyboi2 on 2007-10-16
I don't think I did, unless it was done by accident. I did try:
```
 sudo dpkg-reconfigure gdm 
```But was told I had a fatal error could not open
/lib/modules/2/6/20-15-generic/volatile/nvidia-ko no such file or directory
Error Nvidia (0) failed to load the nvidia kernel module

what does that mean? And could this be causing my file system to be read only at boot?

---

### Post by Partyboi2 on 2007-10-17
ended up re-installing everything.

---

