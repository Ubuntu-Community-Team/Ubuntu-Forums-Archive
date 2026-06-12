---
title: "I wanna stay in console :)"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by dysko on 2006-12-29
:KS I have xUbuntu installed on the network server and I don't want to get graphical environment, I prefer to stay in console login mode... any suggestions how to to this in terminal?

---

### Post by whizbaby on 2006-12-29
Good idea! 
But why then install xubuntu ...? Okok, back to the matter, there are several ways to do this, two of them really easy:
1: **sudo apt-get remove gdm  --purge** (removes all gdm components)
OR
2: rename **gdm** to lets say **rescue.gdm**
 [B]sudo mv /usr/sbin/gdm /usr/sbin/rescue.gdm
[/B]
Next time install server edition....

---

### Post by k1001001 on 2006-12-29
If you want to go from the GUI to the console, hit Ctrl-Alt-F1. F1-F6 all actually go to the console. Ctrl-Alt-F7 will take you back to the GUI. I don't know how to completely get rid of the GUI though. Like the post above said, maybe [Ubuntu Server Edition]("http://www.ubuntu.com/server") would be a better fit.

Also, in a comment to the post above, if Xubuntu is the only thing installed, then GDM isn't used. I'm guessing it would be some variant of XFCE. (XFCM?)

---

### Post by lloyd_b on 2006-12-29
If you remove the "gdm" package, the system will no longer go to a graphical login (though you may have to do a <CTRL><ALT><F1> to get the the first virtual terminal).

Note: If you install from the "Server" CD, Ubuntu does not install any graphical login (or any desktop, for that matter).

Lloyd B.

---

### Post by steve.horsley on 2006-12-29
I would suggest that you disable the gdm service in runlevel2 (the default runlevel fr Ubuntu) with this command:
**sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K86gdm**
You can restore it with this command:
**sudo mv /etc/rc2.d/K86gdm /etc/rc2.d/S13gdm**

---

### Post by whizbaby on 2006-12-30
> **k1001001 said:**
> 
Also, in a comment to the post above, if Xubuntu is the only thing installed, then GDM isn't used. I'm guessing it would be some variant of XFCE. (XFCM?)
Nohs, xfce runs on gdm (I'm pretty shure 'cause I can see it in my processes).

---

### Post by lythandrel on 2006-12-30
For those of us who don't want to login with gdm, but don't want to uninstall it entirely, here's another solution.  It will remove gdm references from rc.d but if you ever want to go back to gdm without a hassle you can.

The command is as follows:

```
update-rc.d -f gdm remove
```

---

### Post by dysko on 2007-01-08
This last one was thing which I was a looking for. I have server / workstation in the office and i don't want to remove graphical login or graphical environment, but just to stay in console when I'm not in the office that my PC don't use too many resources on things which are not necessary.  Tnx one more time

---

