---
title: "upgrade and restricted drivers manager problem"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by themis on 2007-10-22
Hello everyone!

I upgraded to 7.10!After that a restricted drivers manager window poped and I installed the drivers for my Nvidia card. But I didn't read the upgrade post!  ](*,)

I knew that before the upgrade I couldn't use these drivers because I had a  problem and my screen greyed out when using the restricted drivers.

So,after this absolute stupidity, and without backed up my xorg.conf,
what can I do to use the default drivers???I don't want to solve the card problem,JUST GO BACK!


Thank you!

---

### Post by evilregis on 2007-10-22
Are you sure you don't have an xorg.conf backup?

Check the contents of /etc/X11/ and see if there's a xorg.conf.?????????????? (?s being a timestamp like 20070418095026).

If there is, you can use that to restore your conf file by following this: [http://ubuntuforums.org/showthread.php?t=258186](http://ubuntuforums.org/showthread.php?t=258186)

If you don't have one, the only thing I know of is running this:

```
sudo dpkg-reconfigure xserver-xorg
```

Perhaps someone can offer something better.

---

### Post by themis on 2007-10-23
> **evilregis said:**
> Are you sure you don't have an xorg.conf backup?

Check the contents of /etc/X11/ and see if there's a xorg.conf.?????????????? (?s being a timestamp like 20070418095026).

If there is, you can use that to restore your conf file by following this: [http://ubuntuforums.org/showthread.php?t=258186](http://ubuntuforums.org/showthread.php?t=258186)

If you don't have one, the only thing I know of is running this:

```
sudo dpkg-reconfigure xserver-xorg
```

Perhaps someone can offer something better.

I have a xorg.conf, but this shouldn't have the present set of the drivers???
I don't have a xorg.conf.(timestamp)         ... :(


So anyone any ideas before I proceed ruining more staff in here??

---

### Post by themis on 2007-10-24
So I did this,

```
sudo dpkg-reconfigure -phigh  xserver-xorg
```
 
so the default drivers are on, but the laptop is a bit slow than it used to!
Any help?

---

### Post by realvz on 2007-10-24
try restarting if you havent after reconfiguring X

---

### Post by themis on 2007-10-24
I did reboot !

---

### Post by realvz on 2007-10-24
can you explain further then as to what is slow...
is internet slow...applications are slow...doing alt+tab is slow..ubuntu boot is slow.

---

### Post by themis on 2007-10-24
I rebooted again, and things seem better.

Cpu went really high before and stayed there until I close mozilla, and it took a long time to load to a new page.

---

