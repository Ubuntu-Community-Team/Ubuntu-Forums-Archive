---
title: "PC wont shut down, just restarts."
date: 2012-01-27
forum: Any Other OS
---

### Post by Dlambert on 2012-01-27
Hello, my computer wont shut down when I click "shut down" in windows. It shuts down for a second and then reboots. I havent tested in a linux distro yet, but I would like to fix the problem in Windows first. Is it maybe the header for the front panel, or a driver error in windows. I built the computer (specs in signiture). These isnt a huge issue, but I would like my computer's time to be correct:)  Thanks, Dlambert

---

### Post by wolfen69 on 2012-01-27
This should actually be in *Other OS Talk*, but first try a linux live cd to see if the problem is repeatable.

---

### Post by Dlambert on 2012-01-27
Bump. Trying that soon

---

### Post by lisati on 2012-01-27
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Dlambert on 2012-01-27
> **lisati said:**
> *Thread moved to **Other OS/Distro Talk**.*

Thank you

---

### Post by nipunshakya on 2012-01-27
Try to have a normal shutdown with ubuntu to make sure its not a hardware malfunction or something. Then later you may wish to fix your windows..

Regards,WinuxUser

---

### Post by k357k9 on 2012-01-28
On the hardware side, take a look at the power suppy.

---

### Post by Double.J on 2012-01-28
As you've just built it, check any bios setting that could be affecting this would be my tip -it'd be very unusual for a default Window install to reboot the machine when asked to shutdown.

to be doubly sure it's not the OS, boot up a live medium,open a terminal and enter
```
sudo shutdown -h 0
```
If you still get a restart you know it's a hardware setting - it may be something like power failure settings in the bios ;)

Hope it helps :)

---

### Post by qyot27 on 2012-01-28
A couple of other suggestions would be:

Open up the Task Manager (Control-Alt-Delete) and choose the Turn Off option from the Shut Down menu.  That's XP, I would guess that Vista and Win7 are the same as far as the Task Manager goes.  I never had to resort to using it to shut down the computer on there, only on XP.

Open a Command Prompt and issue the following command (you probably need to have opened it as an Administrator for this to work):
```
shutdown -s -t 0
```

---

### Post by Dlambert on 2012-01-28
Thank you, I will try asap

---

### Post by Dlambert on 2012-02-03
Randomly, it shut down. I don't know what I did. But thank you guys!

---

### Post by nipunshakya on 2012-02-03
haha...glad to know you solved it out...though in random way...hehe

Happy Linuxing:D

---

