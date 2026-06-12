---
title: "no gui after install"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by benner on 2006-08-30
i read the other posts about this issue but didn't see snything that helped.  i have a p3 with 128MB RAM.  i tried the live installers but, of course, they froze.  i downloaded the alternate install for kubuntu twice but it wasn't an iso image.  just a bunch of files.  wasn't bootable.  i had a copy of a ubuntu alternate install cd that i had kicking around but after it finished installing, it asked me to remove the disk to boot from the hard disk.  it only came up with a command prompt.  there was no GUI.  i read in another person's post that i could try 'dpkg-reconfigure xserver-xorg'.  i got a response that it wasn't installed.  any suggestions? 
thanks in advance for your thoughts,

-benner

---

### Post by confused57 on 2006-08-30
I believe you may have done a server install using the alternate cd...there is a way to add the ubuntu-desktop from the cd, but it'd probably be easier just to reinstall.  If you have a fast internet connection, you could just enter:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```


I'll try to explain how to do it from the cd, if you'd rather not reinstall...

---

### Post by croak77 on 2006-08-30
If you want the full Ubuntu, then try aptitude install ubuntu-desktop. If you would like to pick and choose what you want, then aptitude install x-window-system-core. That will install X. Then you can install any window manager or desktop you want (gnome-core, kde-core).

---

### Post by benner on 2006-08-30
thanks.  currently i don't have an internet connection for the machines that i am installing on.  they are going to be stand-alone machines in the back of my grade 2 classroom.  when i inserted the cd, the only option seemed to be to click 'enter' to install.  i tried twice, but i may have missed something.  ???

---

### Post by confused57 on 2006-08-30
> **benner said:**
> i read the other posts about this issue but didn't see snything that helped.  i have a p3 with 128MB RAM.  i tried the live installers but, of course, they froze.  i downloaded the alternate install for kubuntu twice but it wasn't an iso image.  just a bunch of files.  wasn't bootable.  i had a copy of a ubuntu alternate install cd that i had kicking around but after it finished installing, it asked me to remove the disk to boot from the hard disk.  it only came up with a command prompt.  there was no GUI.  i read in another person's post that i could try 'dpkg-reconfigure xserver-xorg'.  i got a response that it wasn't installed.  any suggestions? 
thanks in advance for your thoughts,

-benner

Xubuntu would be much faster on a computer with those specs, you can download the alternate iso here(select "Alternate install cd...PC(Intel x86...):
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

Here's how to burn an iso:
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)
Make sure to burn it "as an image" to cd(not as a data cd) and burn at 8x or lower.

---

