---
title: "How to start samba automatically after reboot"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-09-05
Hello. Iv been searching for a detailed guide on how to start the samba service automatically after a reboot, but I have not found anything. Im tired of having to log in via ssh and run /etc/init.d/samba start everytime I reboot.

I hope someone could help me with this.


Thanks

---

### Post by Miademora on 2006-09-05
You could use "bum" as a graphical tool or do it oldschool.

Look in /etc/inittab and find your default runlevel.

```
# The default runlevel.
id:2:initdefault:
```

Tells me Runlevel 2 is default. Then switch to

```
cd /etc/rc2.d/
```

and create a symlink

```
ln -s ../samba S13samba
```

Now samba should start automatically.

---

### Post by chrisdee on 2006-09-05
Thanks for your suggesion but am afraid that didnt work either.
I cant belive this should be so difficult. Hmm.

---

### Post by Iowan on 2006-09-05
[http://www.ubuntuforums.org/showthread.php?t=250673]("http://www.ubuntuforums.org/showthread.php?t=250673")
Try the recommendation in this "similar" post - otherwise, I'll check/post my Samba startup files when I get home tonight.

---

