---
title: "Mounting Mac (OS X) volume on a local network"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by tomekpilot on 2006-08-24
Greetings!
I'm very happy nooby noob to Ubuntu (since last night) and the only snag I can't solve yet is mounting a folder from a Mac on local network.

I've come accross some threads trying to deal with it, but no luck.
Finally I found this and I'd give it a shot:

[http://www.debuntu.org/2006/03/30/11-how-to-mount-a-remote-filesystem-using-ssh-sshfs-and-fuse](http://www.debuntu.org/2006/03/30/11-how-to-mount-a-remote-filesystem-using-ssh-sshfs-and-fuse)

... but when I finally get to:
sudo sshfs rohan@192.168.2.9:548/Users/rohan/Work remotefs/
the directory remotefs can't be seen in the file system, and ls -la on the home dir shows:
?    ?    ?     ?     ?      ?      remotefs

... then here's the output from 'mount' (not sure what I'm looking at here)

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sshfs#rohan@192.168.2.9:548/Users/rohan/Work on /home/animasophi/remotefs type fuse (rw,nosuid,n odev,max_read=65536)

... I don't even know if I'm going in the right direction or after right thing, all I'm trying to do is mount a folder on the desktop, edit and save some files to it.

Thanks in advance :=)

---

### Post by tomekpilot on 2006-08-24
... well, you know how sometimes you're almost there, but not something's missing?

It's all working like a charm, but this is the  command syntax that fixed it:
sshfs rohan@192.168.2.9:/Users/rohan/Work ~/remotefs

then it asks for passwords and files are there!

---

