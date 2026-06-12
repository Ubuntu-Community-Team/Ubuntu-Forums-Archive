---
title: "compiz.."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by n3il on 2006-09-20
Bit of a Linux newbie here.. But wanting to learn :)

I decided to dual boot my new dell xps laptop so i could try and get to grips with linux.. After seeing all the flashy effects available in compiz I decided to give it a try..  

This is when it all goes horribly wrong :)  No matter which tutorial I follow (and I have tried about 4 different ones, reinstalling after each), I end up with hideous slowness on the system and no title bars on my windows..

From what i understand  need to use xgl rather than the other one (aixgl?) since nvidia cards dont support it or some such?

If anyone has a definative guide for getting this to work I would be most appreciative, or if it just wont work on my setup then someone please tell me so i can stop trying ;)

Cheers

Neil

---

### Post by croak77 on 2006-09-20
Are you using the nvidia driver?

---

### Post by n3il on 2006-09-20
Yes sir,

I have tried both installing from automatix and apt-get nvidia-glx i believe it was (though the later always involved changing the driver name from nv to nvidia as it would not do it automatically).  Both ways the splash screen came up at system start (and i did this before installing compiz or xgl to make sure) so i assume the driver was in there correctly.

---

### Post by Dinerty on 2006-09-20
This is the guide I used:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

There could be a number of reasons for the slowdown, I use to get major slowdown due to my xorg.conf configuration, "DefaultDepth" needed to be set to 24 rather than 16, once I did this and restarted X, ran perfect.

To see if your "DefaultDepth" is set to 24, fire up the terminal batman and

```
sudo gedit /etc/X11/xorg.conf
```

then search near the bottom, it may not solve it, but worth a try

---

### Post by n3il on 2006-09-20
I cant remember if i tried that guide or not now :)

Thanks for the reply, I will have a go with that one tonight and see how it goes.. Going to give up soon, damn computers :)

---

