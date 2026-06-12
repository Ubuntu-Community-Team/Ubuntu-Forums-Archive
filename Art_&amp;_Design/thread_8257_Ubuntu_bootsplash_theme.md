---
title: "Ubuntu bootsplash theme"
date: 2004-12-15
forum: Art &amp; Design
---

### Post by Nikola on 2004-12-15
Now, I'll not go into how to get bootsplash working, it's not trivial, and there is debian howto ([http://www.desktop-linux.net/bootsplash.htm](http://www.desktop-linux.net/bootsplash.htm)).
If you liked bootsplash theme from LiveCD, I've recreated it so you can use it.
Here is screenshot of silent mode:
[[IMG]http://img155.exs.cx/img155/1476/silentmode1vb.th.jpg[/IMG]](http://img155.exs.cx/my.php?loc=img155&image=silentmode1vb.jpg)

Get it here:
[http://damas.on.neobee.net/teme/ubuntu-bootsplash.tgz](http://damas.on.neobee.net/teme/ubuntu-bootsplash.tgz)

---

### Post by xsos on 2004-12-16
cool, have u tried with linier gradient color ? , i think it will be better thand the circular gradient.
would u attach ubuntu 3d logo that i have made :D. it is illustrator file but if you wold i will send the transparent png file :D

---

### Post by Nikola on 2004-12-17
I just wanted to recreate bootsplash theme from LiveCD, 'cause it matches default GDM theme.
Maybe now I'll look into adding mng animations and text.

---

### Post by xsos on 2004-12-17
cool

---

### Post by LB06 on 2004-12-27
Very nice!!! I would love to see this included by default in Hoary. A text based boot seems just so... ancient, especially for what is meant to be a modern desktop distribution. Very nice work!

---

### Post by charleyramm on 2004-12-27
Is there any way this could be made in to a .deb package? That would be cool.

---

### Post by Nikola on 2004-12-27
[QUOTE=charleyramm]Is there any way this could be made in to a .deb package? That would be cool.[/QUOTE]

There is already debs on that link I've posted. But it's not that simple. You need patched kernel first, then bootsplash utils installed after that.
Now, it would be nice to have precompiled kernel with bootsplash patch.. but for that maybe it would be wise to wait for official usplash release.

---

### Post by macewan on 2004-12-27
[QUOTE=Nikola]There is already debs on that link I've posted. But it's not that simple. You need patched kernel first, then bootsplash utils installed after that.
Now, it would be nice to have precompiled kernel with bootsplash patch.. but for that maybe it would be wise to wait for official usplash release.[/QUOTE]
 wget [http://www.bootsplash.de/files/debian/dists/unstable/main/binary-i386/kernel-patch-bootsplash/kernel-patch-bootsplash_3.1.4-3_i386.deb](http://www.bootsplash.de/files/debian/dists/unstable/main/binary-i386/kernel-patch-bootsplash/kernel-patch-bootsplash_3.1.4-3_i386.deb)

or just click

[http://www.bootsplash.de/files/debian/dists/unstable/main/binary-i386/kernel-patch-bootsplash/kernel-patch-bootsplash_3.1.4-3_i386.deb](http://www.bootsplash.de/files/debian/dists/unstable/main/binary-i386/kernel-patch-bootsplash/kernel-patch-bootsplash_3.1.4-3_i386.deb)

---

### Post by Martin Stigge on 2005-02-10
I didn't find any deb-Packages with the bootsplash-theme, the posted Link contains only a tarball. So to use it with the beauty of apt, I created a deb myself. It's the original theme from the Tarball above, plus support for 1280x1024. You can get it using the following line for your /etc/apt/sources.list:

deb [http://stigge.org/martin/debian/bootsplash/](http://stigge.org/martin/debian/bootsplash/) ./

Using deb-src instead of deb you can also obtain the source from there. The package itself is located at: [http://stigge.org/martin/debian/bootsplash/bootsplash-theme-ubuntu_0.2-1_i386.deb](http://stigge.org/martin/debian/bootsplash/bootsplash-theme-ubuntu_0.2-1_i386.deb)

Martin

---

### Post by Jad on 2005-02-10
verbose mode is much better :-)

---

### Post by jnoreiko on 2005-02-11
Have you cleaned up the silent image?
when I tried the live CD, I thought that image had quite a bit of jpeg blur around the logo.

---

### Post by ejms07 on 2005-03-23
Where can I get repositories for bootsplash & kernel patch?

---

### Post by Draaku on 2005-03-23
Hi, I was wondering if a guru could post a howto on setting up a bootsplash for Hoary? I am a complete newbie and would love to have a bootsplash instead of the verbose. thanks

---

### Post by kuleali on 2005-04-13
nice

---

### Post by Goshawk on 2005-04-15
Ehm... let me introduce splashy.
Splashy is a complete usermode splash that is installed like a program, for information see: 
[http://wiki.nanofreesoft.org/index.php/Splashy](http://wiki.nanofreesoft.org/index.php/Splashy)

---

