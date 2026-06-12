---
title: "broken xserver"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-12-19
morning all ,
yesterday i tried to change my resolution ,gave up because most of the posts on here have not been able to fix them anyway so i will just put up with it.
this morning my xserver failed to start,now i have the command to recover my old one but where and how do i get there .
 so i need to recover my xserver.xorg
when i boot up what do i do,what buttons do i push
i am no geek so please plain easy instructions thanks

---

### Post by Kobalt on 2006-12-19
You made a backup of your xorg.conf file before you modified it ? What's the exact name you gave to you backup xorg.conf file ?

---

### Post by STREETURCHINE on 2006-12-19
i used sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup
 i need to use ..sudo cp /etc/x11/xorg.conf.backup /etc/x11/xorg.conf... to recover it but when i boot all i get is a jumbled screen .i just need to know how i get to the place i need to type in the recovery command

---

### Post by annda on 2006-12-19
type this:

```
sudo dpkg-reconfigure xserver-xorg
```

you will have to answer a few questions and the xorg.conf file will be overwritten with the new (working) settings.

---

### Post by STREETURCHINE on 2006-12-19
please i dont mean to be rude but i dont know where to go once i boot up it says broken xserver or xserver failed to start .i dont need the commands i already have them i need to know where to go once i boot in and get to the error screen

---

### Post by annda on 2006-12-19
i'm sorry if we're not helping. it doesn't happen very often so we may not remember exacty what messages we saw.i had a broken xserver twice and it gave me the choice of  displaying the error messages or not. after that i was able to log in using my username and password and issue the commands.

i suspect you are automatically logged in to your xserver and that's why you see the jumbled screen right off. when that happens, please try to hit CTRL+ALT+BACKSPACE (if nothing happens, repeat after 2-3 seconds) . this kills the xserver and should leave you with the login screen or the command line where you will be able to type the commands. if it's the login screen choose in the menu 'sessions' 'recovery terminal' or something similar - can't remember what it says exactly, but you will know when you see it.

i hope this was more helpul than the previous posts. please post back - we would really like to help but we can't see your screen so sometimes it's groping in the dark...

---

### Post by bodhi.zazen on 2006-12-19
Ctrl-Alt-F1 to get to the CLI (tty1)

sudo /etc/init.d/gdm restart 

to restart gdm

If you get an error message; sudo /etc/init.d/gdm stop && sudo /etc/init.d/gdm start

If needed, Crtl-alt-F7 to return to GDM

If that fails, boot to the live, desktop CD, mount your ubuntu partition, and restore form backup :p

---

### Post by STREETURCHINE on 2006-12-19
thanks yes i have done tht now ,answered the questions ,but it still seems to be brocken ,just loaded the live disk to try it from there ,
i seem to have broken it good

---

### Post by bodhi.zazen on 2006-12-19
Boot to the live cd.

mount your Ubuntu partition.

```
sudo chroot /mnt/ubuntu_partition
sudo dpkg-reconfigure -phigh xserver-xorg
```

Re-boot

---

### Post by STREETURCHINE on 2006-12-20
sorry it took so long to get back but the above commands failed ,i have a funny notion that i failed to back up my xorg before i fiddled,oops.
so can i fix it from here or is it a complete reload

ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu_partition
chroot: cannot change root directory to /mnt/ubuntu_partition: No such file or directory

---

### Post by LookTJ on 2006-12-20
> **STREETURCHINE said:**
> sorry it took so long to get back but the above commands failed ,i have a funny notion that i failed to back up my xorg before i fiddled,oops.
so can i fix it from here or is it a complete reload

ubuntu@ubuntu:~$ sudo chroot /mnt/ubuntu_partition
chroot: cannot change root directory to /mnt/ubuntu_partition: No such file or directory

did you mount the partition?

---

### Post by STREETURCHINE on 2006-12-20
i did the command in the post so i suppose i tried and failed .
if that is not the right command could you please tell me exactly what to type in

---

### Post by STREETURCHINE on 2006-12-20
what is my key board variant ?
what do i put in this question.
or how do i find out ?

---

### Post by az on 2006-12-20
If you use the -phigh switch do you still get asked that question?

dpkg-reconfigure -phigh xserver-xorg


And I would reccommend booting into recovery mode before you do that.  Then once it is reconfigured, go into graphical mode by running

init 2

---

