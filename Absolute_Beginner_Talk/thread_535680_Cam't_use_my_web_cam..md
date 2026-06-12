---
title: "Cam't use my web cam."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by felipebarroeta on 2007-08-26
Hello to everyone! I am happy to see how quickly is this free software community growing. I happend to be a user who liberated himself just a couple of days ago, and I am having problems with my webcam, I can't use it in the IM software I'm using (aMSN).  It's a T-Com webcam, but do not know what model.
If anyone could put a link to an existing forum or give me please some advice how to get started  this side of the world i would definitely be much thankful.

Peace!

:guitar:

---

### Post by linuxwizard on 2007-08-26
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by felipebarroeta on 2007-08-27
Thanx!!!

---

### Post by felipebarroeta on 2007-08-27
Hello!

I was trying to install an program called easycam that's supposed to detect my webcam. While trying that, I got this from the console:

felipe@felipe-desktop:~$ deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
bash: deb: orden no encontrada

That means "deb: order not found"

What does that means? Sorry but I am newbie newbie... 

Cheers!

---

### Post by Lord Illidan on 2007-08-27
That's because it's not a command.

That line  deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main should be inserted in your /etc/apt/sources.list.

Follow the procedures here : [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam) 

What you have to do is basically type in a terminal :

gksudo gedit /etc/apt/sources.list

Then enter the line :```
 deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
``` at the bottom.

Then exit gedit and type sudo update in the console, followed by sudo apt-get install easycam.

EDIT : You might find this link [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) very useful if you are a newbie..please do tell if you have further problems.

---

### Post by felipebarroeta on 2007-09-01
I could install easycam but i cant see where it si :S

i also got this from camorama, a software supposed to show me my web cam: could not connect to video device  (/dev/video0).
please check connection.

so i still can't use my web cam...

---

### Post by felipebarroeta on 2007-09-01
I could install easycam but i cant see where it si :S

i also got this from camorama, a software supposed to show me my web cam: could not connect to video device  (/dev/video0).
please check connection.

so i still can't use my web cam...

---

