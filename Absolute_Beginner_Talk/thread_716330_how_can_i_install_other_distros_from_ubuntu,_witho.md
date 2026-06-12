---
title: "how can i install other distros from ubuntu, without burning a cd?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by rob1101 on 2008-03-05
ok i have ubuntu installed but i would like to expand my linux experience and try out a few different distros. since i would also like to learn from this experience and i don't really feel the need to waste cds i would like to learn how to install these distros from ubuntu.

my first choice is MintLinux

my hard drives are set up like this:

[LIST]
[*]250gig[LIST]
[*]Extended partition[/LIST][LIST][LIST]
[*]10gig ext3 Ubuntu sda6
[*]05gig ext3 BLANK  sda5
[*]05gig ext3 BLANK  sda7
[*]05gid ext3 BLANK  sda8[/LIST][/LIST][LIST]
[*]PRIMARY /home[/LIST]
[*]80gig Windows XP Home[/LIST]I atempted to install Mint on sda5 by creating /boot directory on /media/sda5. then extracting the initrd.gz and vmlinuz from the mint.iso and putting them in /media/sda5/boot.

I then added this to /boot/grub/menu.lst

```
title        Mint
kernel        (hd0,4)/boot/vmlinuz
initrd        (hd0,4)/boot/initrd.gz
```

and i get this error
```
Error 2: File not found
Press any key to continue...
```

---

### Post by dstew on 2008-03-05
You can install other distributions over the network using the [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") program.

---

### Post by Forrest Gumpp on 2008-03-05
You may find this thread of interest for installing without CD ROM drive availability.  See:  [http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by ubutufan on 2008-03-05
You may want to try running any OS on a virtual machine, from within ubuntu.

A good, simple and very straightforward piece of program is Vbox by innotek

At the end of the day if you are not happy with the distro you are testing, you just delete it from within Vbox and kiss it bye bye

---

