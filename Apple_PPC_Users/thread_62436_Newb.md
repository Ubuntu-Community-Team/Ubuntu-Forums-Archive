---
title: "Newb"
date: 2005-09-04
forum: Apple PPC Users
---

### Post by rotary_moto on 2005-09-04
Alright everybody i am new to the whole Linux on Mac game,  Ive ran some mandrake on my Amd years ago, but nothing like this.

i have a 12' Ibook G3 700Mhz machine with 256Mb Ram and a 30Gb Hd. And of course the wonderful Combo Drive.

I am currently running Ubuntu 5.04 ONLY, I have panther but it just doesnt seem to run right on this g3. so i switched to linux since i couldnt find a copy of Os9 (personal favorite)

Anyways, my resolution is now set to 640x480 and WILL NOT budge. no second monitor support nothing.  If i could get the second monitor to work for me i would be soo happy.

So since i am new to this and dont understand how to do all this "xorg" crap, i need some serious walk through or something, this 640x480 is driving me crazy.



Any help would be greatly appreciated.

My Aim is Hillsongemo
Msn  [email]Called.to.worship@gmail.com[/email]


Scott.



-Or if anyone has a Os9 .iso or something that would be great too.-

---

### Post by numberexhaust on 2005-09-04
I'm not too sure how well this'll work on ppc, but it worked fine for me on my x86.  My resolution was also stuck at 640x480, and since my monitor did not support that, I ended up with a box around my tiny little screen.

If I understand your problem correctly, do this.  Run:

```
sudo dpkg-reconfigure xserver-xorg
``` 

This will walk you through a nice guide for a lot of things.  Skip through until you get to the monitor name.  When it asks you to go "Beginner/Medium/Advanced", select advanced.  It will give you some numbers, just accept the defaults, and when it asks if it's OK to save it say yes.  Then reboot the computer and see if it works.  If it doesn't, post back here and we can play around a little more.

---

### Post by rotary_moto on 2005-09-04
Sweet so now my resolutions can change, but now no second monitor support, it tries to show an image, but all it is, is lines and crap,  cnahge the res. and nothing helps.  It doesnt have to be a split setup it needs to be a clone, for the way im setup.


Thanks for your help with the res. 

Now if I can get the rest of this figured out, id be good to go.

---

### Post by numberexhaust on 2005-09-04
[QUOTE=rotary_moto]Sweet so now my resolutions can change, but now no second monitor support, it tries to show an image, but all it is, is lines and crap,  cnahge the res. and nothing helps.  It doesnt have to be a split setup it needs to be a clone, for the way im setup.


Thanks for your help with the res. 

Now if I can get the rest of this figured out, id be good to go.[/QUOTE]
 yea unfortunately I don't know anything about that... you could experiment a little with the command I gave you above, but that's the best I can do.

Good luck anyway

---

