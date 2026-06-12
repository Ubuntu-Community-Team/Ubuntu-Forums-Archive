---
title: "GRUB loader question...."
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-09
I would like to load Windows, Ubuntu and Kubuntu on one disk. Can the GRUB loader accept three Operating Systems? I want to play with Gnome and KDE for a while to see which flavor I like the best. 
I have done Windows and Ubuntu on the same drive so far.

---

### Post by Spleenie on 2006-07-09
> **dragon1964m said:**
> I would like to load Windows, Ubuntu and Kubuntu on one disk. Can the GRUB loader accept three Operating Systems? I want to play with Gnome and KDE for a while to see which flavor I like the best. 
I have done Windows and Ubuntu on the same drive so far.

It sure can. Might I suggest, however, that you run:

```
sudo apt-get install kubuntu-desktop
```

and obtain kubuntu without any more work :) When you log in, you can choose to log into either gnome or KDE then, and another benefit is you only have one home directory 

Is there another reason you want kubuntu to be seperate?

---

### Post by dragon1964m on 2006-07-09
Sure. One of them is going to go away after comparison. Then I want to keep the third partition open for a future distro. I do like my toys.....:)

---

### Post by dragon1964m on 2006-07-09
Oh, I should ask if there is anything special I need to do when I load the third OS?

---

### Post by Spleenie on 2006-07-09
> **dragon1964m said:**
> Sure. One of them is going to go away after comparison. Then I want to keep the third partition open for a future distro. I do like my toys.....:)

You could save the trouble of repartioning until you have that future distro in your hands, and still be able to try out kde.

If you really need to install kubuntu on a seperate partition, you will have to resize either the windows or ubuntu partitions (unless you left space already) and the kubuntu installation will rebuild you a new grub boot list.

As for capacity, I have no idea how many OS's grub will hold but I know I had 6 going at one stage (win98 and xp, mandriva, redhat, ubuntu and freebsd). A bit of a squeeze and not very efficient, but it was an experimental time :)

---

### Post by dragon1964m on 2006-07-09
Thats great to know! I have 80 GB to play with. And the third partition is already in place. I just want to be sure I am not going to mess things up too bad. Play time is fun...broken toys are not.

---

### Post by Spleenie on 2006-07-09
> **dragon1964m said:**
> Thats great to know! I have 80 GB to play with. And the third partition is already in place. I just want to be sure I am not going to mess things up too bad. Play time is fun...broken toys are not.

Remember you can use the swap partition you made for ubuntu as the swap partition for kubuntu, which will save you some space. Also its generally a good idea to have a seperate partition for your /home directory. You can do this during the kubuntu install by splitting your free partition, but if you are just experimenting with the os, then this probably isnt necessary.

Good luck!

---

