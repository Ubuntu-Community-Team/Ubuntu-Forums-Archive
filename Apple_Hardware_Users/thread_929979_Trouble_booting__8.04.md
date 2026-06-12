---
title: "Trouble booting  8.04"
date: 2008-09-25
forum: Apple Hardware Users
---

### Post by crapple on 2008-09-25
I have been trying for over a year to boot my emac g4 with gusty and now hardy. Anything up to feisty fawn worked fine but past that it installs boots and then when it gets to login blank screen. I know the x org file needs to be configured and the yaboot file also might need some. Can someone please post a guide on what might need to be changed in both. (Everything not just the slight configuring cases on easier machines but include those too.)
Thanks

---

### Post by BryannPaulaMelvin on 2008-09-25
This sounds similiar to the problems I had with my ibook.

I was good up to edgy...and then x problems.

to get hardy to work

I installed hardy via alternate cd.
installed a xorg.conf file from 6.06.2
rewrote yaboot config to exclude the splash which was still causing screen problems

ybin to get the new yaboot installed.

If you don't have a backed up xorg.conf file you might boot a live cd version that worked well before, and then stick it on a server you can retrieve it from, like webmail or google apps etc. then burn it to cd with another machine.(or flash etc) I had one on my backup/file server.

Bryann

---

### Post by seeker1458 on 2008-09-25
> **BryannPaulaMelvin said:**
> 

If you don't have a backed up xorg.conf ...
Bryann

This will rewrite the xorg.conf to default

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by BryannPaulaMelvin on 2008-09-25
oh one more thing I still had problems with gnome... It didn't recognize smb:  said there was no application for that file type ?

I installed Kubuntu desktop then removed gnome.

sudo aptitude remove ubuntu-desktop
sudo aptitude remove gnome*

I had to add the KDE integration package for OO after too as I lost all my OO.org icons.

8.04 works better for me with KDE or XCFE which seems to be a switch for me

---

### Post by BryannPaulaMelvin on 2008-09-25
Not sure if this would work.(reconfigure) It appears that 8.04 uses different files note the "configured monitor" etc in the default xorg.conf

when I googled I ran into situations where this was tried and didn't work.I didn't attempt it.

---

### Post by crapple on 2008-09-26
I have already tryed using 6.06 x org file with no luck. Does anyone have any suggestions on how to reconfigure 8.04's x11 and yaboot?

---

### Post by BryannPaulaMelvin on 2008-09-26
hmm changing the xorg.conf worked for me....you could edit it by hand...


as far as yaboot :

sudo yabootconf will write a new simple yaboot

Usage: yabootconfig [OPTION]...
Generate a working /etc/yaboot.conf.

  -t, --chroot               set root directory yabootconfig should work from
  -r, --root                 set root partition, Example: /dev/hda3
                               default: determined from {chroot}/etc/fstab
  -b, --boot                 set bootstrap partition, Example: /dev/hda2
                               default: first type: Apple_Bootstrap partition
      --kernel-args          add an append= line with specified arguments
  -q, --quiet                don't ask any questions/confirmation
      --noinstall            don't automatically run mkofboot
  -h, --help                 display this help and exit
  -V, --version              output version information and exit

---

