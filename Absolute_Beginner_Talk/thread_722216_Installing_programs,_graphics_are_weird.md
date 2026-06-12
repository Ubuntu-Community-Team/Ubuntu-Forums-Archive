---
title: "Installing programs, graphics are weird"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by mrfraser89 on 2008-03-12
Ok guys, I've installed the game Teewars, and it works fine. Then I move it into a protected part of the filesystem, and when I run it as my normal user, the graphics come out weird.

I've installed Matlab also, and this ended up going into /opt/matlab

I had to install as superuser obviously.

Anyhow, I can't run the program unless I'm in sudo mode and the menus etc don't display correctly, which I think is the same reason as Teewars not displaying correctly...

What could be the problem?

---

### Post by Bölvaður on 2008-03-12
I do not know what is wrong, but you should not use sudo to run any programs that aren't trusted system tools.

---

### Post by intel on 2008-03-12
what did you do ?.......exactly.

---

### Post by mrfraser89 on 2008-03-12
With Matlab I just ran the installer (it's a Linux version of Matlab)

I decided to install into /opt/matlab (which is apparently the usual place to do it) but to do so, I needed root privileges.

I started the installer using gksu which gave me the privileges and it all worked out.

I can only run matlab if I start the program with sudo now. Why would this be? Furthermore, where can I install matlab that I won't need root privileges?

---

### Post by Bölvaður on 2008-03-12
dunno, you could try put it in your home directory for a test.

when I installed enemy territory I put it here:

/usr/local/games/etqw/

---

### Post by amd-64 on 2008-03-13
How about you do the following 


sudo chmod 755 /opt/matlab/bin/*

This should make any user able to run matlab. When you start matlab, do so from a location you have write access to, such as your home folder. In a terminal, type 

cd
/opt/matlab/bin/matlab

If things work out, you can create a link for matlab in /usr/bin and then you can simply type matlab instead of the full path. See if this helps.

---

