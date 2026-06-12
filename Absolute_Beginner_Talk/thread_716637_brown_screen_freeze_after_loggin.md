---
title: "brown screen freeze after loggin"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by jtclicker on 2008-03-06
agggggh, ok after my thread about freezing on install...

installed ok by pulling ethernet cable out. Installed, rebooted fine. Then did all the updates that were needed manually. system asked for a reboot which I did. Entered my user name, password, then... got the usual brown screen but without any icons or dialogues, no -applications, system, nada de nada. If I alt ctrl F2 I can login but don-t know what to do once I-m there...

---

### Post by kesman on 2008-03-06
Try this:
```

sudo /etc/init.d/gdm restart

```

---

### Post by kpkeerthi on 2008-03-06
How much RAM do you have?

---

### Post by jtclicker on 2008-03-06
> **kpkeerthi said:**
> How much RAM do you have?

2gig. WinXP on a 60 gig drive and this new drive with ubuntu 120 gig. I-ve had ubuntu working fine in this setup on an old smaller disk, just can't get it going on the new disk

---

### Post by jtclicker on 2008-03-06
> **kesman said:**
> Try this:
```

sudo /etc/init.d/gdm restart

```

ok i'll try that thanks

---

### Post by kesman on 2008-03-06
Also could you paste the output of:
```

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```
commands? If you cannot paste them, just let me know if errors or warnings are present.

---

### Post by jtclicker on 2008-03-06
> **kesman said:**
> Also could you paste the output of:
```

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```
commands? If you cannot paste them, just let me know if errors or warnings are present.

I-m running off live cd, so paste seems to work

ubuntu@ubuntu:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
ubuntu@ubuntu:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
ubuntu@ubuntu:~$

---

### Post by jtclicker on 2008-03-06
> **kesman said:**
> Try this:
```

sudo /etc/init.d/gdm restart

```

Ok, did that and it just took me back to a loggin which in turn gave me the brown screen without icons...

---

### Post by kesman on 2008-03-06
Don't run these in the liveCD, it doesn't make any difference into your installed Ubuntu and give us wrong information.

---

### Post by jtclicker on 2008-03-06
> **kesman said:**
> Don't run these in the liveCD, it doesn't make any difference into your installed Ubuntu and give us wrong information.

ah ok sorry. one problem, I-m on a spanish keyboard and the code screen doesn-t acknowledge my third level keystrokes, so the vertical slash I can-t do. But without that I got file not found for both those strings

---

### Post by kesman on 2008-03-06
Do you mean | ? I have no idea how to do it with spanish keyboard, sorry =D

---

### Post by jtclicker on 2008-03-06
> **kesman said:**
> Do you mean | ? I have no idea how to do it with spanish keyboard, sorry =D
well it should be alt 1 but it isn-t working as I didn't have time to set up the third level keyboard strokes before having problems!

---

### Post by kesman on 2008-03-06
In my keyboard pipe (|) comes with Alt Gr + the key with < and > in it.

If you have a numpad in your keyboard, you can create the symbol with alt+0124 by holding down alt and then typing 0124 with the numeric keys on the right side of the keyboard.
You could also read trough the entire log with
```

nano /var/log/Xorg.0.log

```
and spot all line starting with WW or EE.
Then you could also edit your /etc/X11/xorg.conf -file and reduce the resolution used by Xorg.

---

### Post by jtclicker on 2008-03-06
OK, I got the same as I got from the live cd funnily enough


ubuntu@ubuntu:~$ cat /var/log/Xorg.0.log | grep EE
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
ubuntu@ubuntu:~$ cat /var/log/Xorg.0.log | grep WW
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
ubuntu@ubuntu:~$

---

### Post by kesman on 2008-03-06
That's interesting. What graphics adapter do you have? You could try to reconfigure xorg with
```

sudo dpkg-reconfigure xserver-xorg

```
and whenever you encounter something that you are not sure, just go with the defaults by pressing enter.
Before this, take a backup of your current xorg.conf with
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

```

---

### Post by jtclicker on 2008-03-06
Thanks for your help with this. I really don't know what has happened as I've had ubuntu working on this system and all I've done is change the hard disk! I'm going to try another reinstall, and if that doesn't work... I'll post on the forums again... :)

---

