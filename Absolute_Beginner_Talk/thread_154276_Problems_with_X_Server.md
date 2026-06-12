---
title: "Problems with X Server"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by hbinded on 2006-04-02
Hi! I just installed ubuntu, but I got this a message that my X Server is not properly configured or not installed. I followed the advice on this [http://ubuntuforums.org/showthread.php?t=154203]("http://ubuntuforums.org/showthread.php?t=154203") post and set my refresh rates  and resolution accordingly but I still don't have the gui. I would really like to use ubuntu and finally get rid of the os that really sucks!........u know!!

---

### Post by r4ik on 2006-04-02
When you reconfigure the xserver, what drivers are you using? Have you tried the 'vesa' drivers?

---

### Post by hbinded on 2006-04-02
How do I do that?

---

### Post by Sutekh on 2006-04-02
When you start Ubuntu you only get to a command line?  At the command line type
```
sudo dpkg-reconfigure xserver-xorg
```
 - You will be asked a string of questions regarding the input devices (keyboard, mouse and monitor) on your PC.

 - If you are unsure what to answer, just use the default/suggested options.

 - When you get to the question about which driver you wish to use for the X Windows server.  Choose **vesa**

When the reconfiguring is finished, use
```
sudo /etc/init.d/gdm start
```

---

### Post by r4ik on 2006-04-02
sudo dpkg-reconfigure xserver-xorg

Select the desired xserver driver scroll down to "vesa" hit enter and proceed than do a,

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart

Good luck !

---

### Post by r4ik on 2006-04-02
Had to walk away from my SuSe box so it took a while but i guess the answer is there now :)

---

### Post by hbinded on 2006-04-02
yipppeee! It worked:D . Now to try out Ubuntu! Thanks a million!

---

### Post by catlett on 2006-04-02
Told you to get your own post and you'll find some smart ones. See you around the forum.:-D

---

