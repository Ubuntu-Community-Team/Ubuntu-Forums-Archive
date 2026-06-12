---
title: "apt-get being annoying"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-04
Ok, i want to install VLC player, so I go to their site, i do what it tells me to do "sudo apt-get update", "sudo apt-get install vlc vlc-plugin-esd", and on the "sudo apt-get install vlc vlc-plugin-esd" it gives me some stuff about apt-get, here is what it tells me: "E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."


Here is the whole code:


admin@admin-desktop:~$ sudo apt-get install vlc vlc-plugin-esd
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bmp-docklet: Depends: beep-media-player but it is not going to be installed
  vlc: Depends: liba52-0.7.4 but it is not going to be installed
       Depends: libdc1394-13 but it is not going to be installed
       Depends: libdvbpsi4 but it is not going to be installed
       Depends: libdvdnav4 (>= 0.1.9) but it is not going to be installed
       Depends: libgsm1 (>= 1.0.10) but it is not going to be installed
       Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
       Depends: libiso9660-4 but it is not going to be installed
       Depends: libmodplug0c2 (>= 1:0.7-4.1) but it is not going to be installed       Depends: libmpeg2-4 but it is not going to be installed
       Depends: libtar but it is not going to be installed
       Depends: libvcdinfo0 (> 0.7.23) but it is not going to be installed
       Depends: libxosd2 (>= 2.2.13) but it is not going to be installed
       Depends: wxvlc but it is not going to be installed
       Depends: vlc-plugin-alsa but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
admin@admin-desktop:~$

---

### Post by orb9220 on 2006-09-04
vlc is in synaptic you don't need to go to thier web site.

---

### Post by bluevoodoo1 on 2006-09-04
```
sudo apt-get -f install
```
```
sudo apt-get update
```
```
sudo apt-get install vlc vlc-plugin-esd
```

Try that from the terminal.

---

### Post by maelgwynffn on 2006-09-04
I would jsut use Synaptic, as it needs to have some dependancies resolved.  The GUI is good for resolving the issues.  Err... I would just do what it wants.  Then it will be happy. :)

---

### Post by crunchystrike on 2006-09-04
can't do it, this is what it tells me

admin@admin-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
admin@admin-desktop:~$

---

### Post by ds[de] on 2006-09-05
> **crunchystrike said:**
> can't do it, this is what it tells me

admin@admin-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
admin@admin-desktop:~$

Well ... I'm almost afraid to ask, but did you try 'sudo dpkg --configure -a'? If yes, what was the output? If no, why not? :-k

---

