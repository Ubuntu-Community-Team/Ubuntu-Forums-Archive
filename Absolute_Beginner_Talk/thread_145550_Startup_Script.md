---
title: "Startup Script?"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by -=Raven=- on 2006-03-16
Is it possible to create a script of some sort to map my NTFS drive and run Gkrellm when i start ubuntu? Its driving me crazy having to keep doing it everytime i switch my pc on.

---

### Post by mlind on 2006-03-16
by mapping your NTFS drive do you mean mounting it automatically?

If you define your drive on /etc/fstab and provide *auto* parameter, it will
be automatically mount on boot

mine looks like
```

/dev/hda5       /media/E        ntfs    ro,auto,nls=utf8,umask=0222     0      0

```

after system has started, I can access it by going to /media/E.

You need to change the "file system" to your NTFS partition. Use *sudo fdisk -l* 
to see all partitions. You need to create the mount point manually. 
Usual places are /mnt or /media

for running applications when you log in ubuntu see System > Preferences > Sessions > Startup Programs

---

### Post by aggiechemist on 2006-03-16
It can be done with scripts, but there is probably an easier way.

As for mapping the drive, you should be able to work with your /etc/fstab file and add a line that describes the NTFS drive. If you add an automount command, it should go automatically.

I'm not really familiar with the other program, but if it is just a program you should be able to have it start with each session. Look under System -> Preferences -> Sessions and you should be able to list it as a program to start when the computer starts.

Also, if you save the session when the NTFS is mounted it might automatically load it with all other sessions (but I've never tried that). Hope this helps.

If you really want to try it with scripts, I might be able to help with that too.

---

### Post by jpkotta on 2006-03-16
Make a script called /etc/init.d/local, and put your commands in there.  To do things properly, make your script set things up when given the argument "start", and tear things down with "stop".  This is not strictly necessary.  Then do ```
update-rc.d local defaults 99 0
```

The above is for booting, not logging in.  I suspect that you would want to be logged in before gkrellm started.  In that case, there is some GNOME setting that needs to be set.  I don't use GNOME, so I can't help you there.

---

### Post by -=Raven=- on 2006-03-16
Thank you :)

---

