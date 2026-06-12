---
title: "Weird gutsy screen resolution"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by awiggin on 2008-03-22
Hello friendly Ubuntu community!

I upgraded to gutsy last night (through update manager) and most everything went smoothly.  I have a couple problems.

The one strange one is this.  The first couple times I booted up, the screen resolution was fine (my monitor should be 1440X900).  But on the third or fourth try, it went to 800X600, which looks ridiculous of course.  On the screen resolution GUI, there are no other options other than 800X600.

Any help?

Thanks all.

---

### Post by kazamx on 2008-03-22
It sounds like something has gone wrong with X.org. 

When it boots into the screen res you say, thats the backup resolution. You may need to go in and edit the resolution options by hand.

---

### Post by awiggin on 2008-03-22
Thanks, Kazamx!  

Can you tell me exactly how to do that?  (Pretty much a noob here.  If not a noob, then at least I'm not really a techie.)

Thanks for the help.

-awiggin

---

### Post by zvacet on 2008-03-22
```
sudo dpkg-reconfigure xserver-xorg
```

In this proces you will be able to set desired resolution.

---

### Post by unutbu on 2008-03-22
I have no personal experience, but I have seen this recommended by many here on ubuntu forums, with success.

```
sudo dpkg-reconfigure xserver-xorg
```

See [http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/](http://www.newlinuxuser.com/screen-resolution-got-all-funky-try-dpkg-reconfigure-xserver-xorg/)

---

### Post by kazamx on 2008-03-22
This may help too

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

It talks you through pretty much everything that could have gone wrong and gives step by step instructions on how to fix it.

---

### Post by awiggin on 2008-03-22
Thanks to all!  The xorg config did the trick.

You guys rock!

Peace,
awiggin

---

