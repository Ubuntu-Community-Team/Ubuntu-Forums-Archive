---
title: "Some HD questions"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-22
hey all,

when installing Ubuntu, it asks fo you to designate a drive that is 2gb in size and has / in it. My BIOS can handle boot partitons of 8GB and less (or else I get Error 18 when Grub tries to load). I orginally wanted 20GB Ubuntu 7.10 partition. I heard you can do / and /root and /home (what do those do?). I have Ubuntu 7.10 installed on external HD

thanks in advance

---

### Post by mikewhatever on 2007-10-22
First, there is no /root, because /=root. That clarified, / is where your operating system resides, and /home is for personal files and settings. Home does not have to be a separate partition, and can also be a directory inside root. In your case, it seems the first partition should be /, sized anywhere beteween 3 - 8 BG, and another partition will need to be /home, sized 20 - the size of root. There should also be a swap partition. aysui has some nice pictures on his site [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning). The scheme you want is the last one.

---

### Post by JasonBourneLinux on 2007-10-23
awesome- thanks!

---

### Post by psusi on 2007-10-23
To get around the boot limit you can just make a 100-200 mb /boot partition at the start of the drive, then use the rest for /.

And there IS /root, it is the root account's home directory.

---

### Post by scorp123 on 2007-10-23
> **psusi said:**
>  And there IS /root, it is the root account's home directory. Yes, but not as a separate mount point. You can't have stuff like /root, /etc, /sbin and /lib on separate mount points as you could with /boot, /usr, /opt, /var and /home. I think that's what the he wanted to say up there, e.g. "there is no /root mount point".  :)

---

### Post by JasonBourneLinux on 2007-10-23
If i went /boot and / then grub would have to be installed on Hd0 right?

---

### Post by psusi on 2007-10-23
> **scorp123 said:**
> Yes, but not as a separate mount point. You can't have stuff like /root, /etc, /sbin and /lib on separate mount points as you could with /boot, /usr, /opt, /var and /home. I think that's what the he wanted to say up there, e.g. "there is no /root mount point".  :)

Sure you can; you can mount a drive in any directory you want.

> **JasonBourneLinux said:**
> If i went /boot and / then grub would have to be installed on Hd0 right?

Sort of... the bios always maps hd0 to whichever drive it boots from, so in that sense, grub is always installed to hd0.  That does not have to be what linux sees as /dev/sda though, and /boot does not have to go on hd0.  Such configurations though, do require some tweaking to setup right.

---

### Post by scorp123 on 2007-10-25
> **psusi said:**
> Sure you can; you can mount a drive in any directory you want.  Not with essential directories such as /etc, /sbin and /lib ... those have to be on the same "/" mount point. :)

---

