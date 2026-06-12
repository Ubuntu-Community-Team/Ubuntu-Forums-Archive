---
title: "I downloaded Real Audio followed directions but"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2006-04-12
I downloaded Real Audio to my desktop.  I followed directions..went to the terminal and did the following:

Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.


it didn't work.  When I did the chmod it couldn't find the file??

---

### Post by noumaan on 2006-04-12
[Installation Instructions]("https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b") here. The easiest way to install real player is by downloading the debian package.

---

### Post by xwiz on 2006-04-12
noob needs help

the instructions say that i need to install libstdc++5. so i run sudo apt-get install libstdc++5 and then it asks me to insert the 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)' CD. 

and from there i'm confused. did something go wrong or where can i find that CD?

---

### Post by noumaan on 2006-04-12
xwiz: It is actually asking for the installation CD that you or someone else used to install Ubuntu on your computer. When I installed libstdc++5 it didn't ask me for CD please try installing using Synaptic thats how I did it.

---

### Post by Perfect Storm on 2006-04-12
Best way is to remove the CD line from the source list or comment it out if you want only to get the packages from the web.
```
 sudo gedit /etc/apt/sources.list
```

You will see something similar as this:
> deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted


Put a # infront of it so it looks this:
> # deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

Save and exit then:
```
sudo apt-get update
```

---

### Post by GMachine_24 on 2006-04-12
Yes, try Synaptic. You need to choose 

System>Administration>Synaptic Package Manager

enter your password in the box that pops up

then, when the Synaptic GUI opens, click "search" and insert "libstdc++5".

You should be able to find it in the list that Synaptic returns (in the right window). Click on 

libstdc++5

and then click "apply". After that it should all be downhill.

GM

---

### Post by esteban2x on 2006-04-12
I followed directions and it didn't work. Then I check my computer today and lo and behold, there is REal Audio working. Whatever I did worked. So, one of the directions above worked. Wish I could tell you which one. Thanks

---

