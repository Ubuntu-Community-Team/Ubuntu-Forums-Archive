---
title: "[SOLVED] Can I fix xorg.conf from recovery mode?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-07-19
I had everything working fine last night. This morning I attempted a boot into Linux and got the warning that xorg.conf was "incomplete." The only thing I can figure is the problem is when I installed Beryl and maybe got some changes into xorg.conf wrong.

Is there a way to edit xorg.conf while using recovery mode? Thanks for the assistance.
kh

Edit: When all was said and done, I used this line command in recovery mode to fix my problem:

**[COLOR=Red]dpkg-reconfigure xserver-xorg[/COLOR]**

---

### Post by gn2 on 2007-07-19
If you get a command line up try "sudo dpkg -phigh xserver-xorg" or "sudo dpkg-reconfigure -phigh xserver-xorg" to sort it.

---

### Post by taurus on 2007-07-19
```
nano -Bw /etc/X11/xorg.conf
```
Save and exit with <Ctrl>o and <Ctrl>x.

---

### Post by Atomic Dog on 2007-07-19
Yes use nano.  Go into etc/x11 folder then type

```
sudo nano xorg.conf
```

You may want to make a copy of your xorg.conf first, but if it's hosed I guess the worst that can happen is you reconfigure X.

edit: wow, lots of fast answers.

---

### Post by AlexenderReez on 2007-07-19
i suggest you to follow this....if you reconfigure it...you need to set it..but system detected is better --->

> [http://ubuntuforums.org/showpost.php?p=3033579&postcount=5](http://ubuntuforums.org/showpost.php?p=3033579&postcount=5)

---

### Post by kittyhawk63 on 2007-07-19
Thanks. You guys are faster than McDonald's.
kh

---

### Post by kittyhawk63 on 2007-07-19
> **taurus said:**
> ```
nano -Bw /etc/X11/xorg.conf
```Save and exit with <Ctrl>o and <Ctrl>x.

Just to be clear on this. The line commands you gave are carried out while using recovery mode. Is that right?
kh

---

### Post by kittyhawk63 on 2007-07-19
> **AlexenderReez said:**
> i suggest you to follow this....if you reconfigure it...you need to set it..but system detected is better --->

This works from GUI. I do not have GUI while in recovery mode. Thanks

---

### Post by taurus on 2007-07-19
> **kittyhawk63 said:**
> Just to be clear on this. The line commands you gave are carried out while using recovery mode. Is that right?
kh

Yip.

---

### Post by aysiu on 2007-07-19
```
dpkg-reconfigure xserver-xorg
``` could also work.

---

### Post by Seisen on 2007-07-19
> **kittyhawk63 said:**
> Just to be clear on this. The line commands you gave are carried out while using recovery mode. Is that right?
kh

Exactly because when you boot into recovery mode you put into a terminal with root access so also make sure that you don't mess anything else up while your fixing your xorg.conf.

---

### Post by kittyhawk63 on 2007-07-19
> **gn2 said:**
> If you get a command line up try "sudo dpkg -phigh xserver-xorg" or "sudo dpkg-reconfigure -phigh xserver-xorg" to sort it.

If you will please:
In a simple reply, what is the difference between the two and what do each accomplish?
kh

Edit:  And how do these differ from another suggestion?: dpkg-reconfigure xserver-xorg

Edit: From what I've read here, sudo is not needed in these line commands. Isn't that correct?

---

### Post by kittyhawk63 on 2007-07-19
> **Seisen said:**
> Exactly because when you boot into recovery mode you put into a terminal with root access so also make sure that you don't mess anything else up while your fixing your xorg.conf.

Ok. Then that means while I am in recovery mode I never use "sudo". I don't need it. Is that correct. Still learning.
kh

---

### Post by taurus on 2007-07-19
Recovery mode = root.

---

### Post by Seisen on 2007-07-19
Yes that is correct.

---

### Post by kittyhawk63 on 2007-07-19
> **taurus said:**
> Recovery mode = root.

Taurus,
If you can look at the three commands I have asked about "dpkg...", which do you think is the best approach to fix xorg.conf while using recovery mode?
kh

---

### Post by taurus on 2007-07-19
```
dpkg-reconfigure xserver-xorg
```

---

### Post by kittyhawk63 on 2007-07-19
> **taurus said:**
> ```
dpkg-reconfigure xserver-xorg
```

Thank you. Off to see the wizard -> "recovery mode."
kh

---

### Post by AlexenderReez on 2007-07-19
> **kittyhawk63 said:**
> This works from GUI. I do not have GUI while in recovery mode. Thanks


that guide ask use gui in livecd....read it carefully...you will see...

---

### Post by kittyhawk63 on 2007-07-19
> **AlexenderReez said:**
> that guide ask use gui in livecd....read it carefully...you will see...

Missed that. I read it but it didn't register. sorry.
kh

Edit: BTW, I used this line command suggestion in recovery mode to resolve my problem:

[COLOR=Red]**dpkg-reconfigure xserver-xorg**[/COLOR]

---

