---
title: "only 2 resolution choices"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by kolakube on 2007-01-03
How can I make the res higher.


I only have 2 terrbly low choices in the screen res box

640 x 480 or 800 x 600.  I need much higher.


I muct say, I am trying hard to convert from XP and so far,what I see looks great!  Think this could be the start of a great relationship ;)

Kolakube

---

### Post by taurus on 2007-01-03
What video card do you have?  You probably need to install a driver for it...

---

### Post by kolakube on 2007-01-03
I have a nvidia 7900 gt

---

### Post by taurus on 2007-01-03
Here's a guide for you...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by kolakube on 2007-01-03
Thnx fella,

Im acctualy a certified win pro.  JUst trying hard to re tune my skills.

I must say, im finging ubuntu easy to use so far.  i no im only using the basics but so far so good:cool:

---

### Post by taurus on 2007-01-03
Once you have nvidia-glx installed, your experience of Ubuntu (or Linux) should be better, especially the graphic side.  

Good luck and if you're not sure how to install the nvidia driver for your graphic card, just let me know.

---

### Post by kolakube on 2007-01-03
I keep getting the same prob.

I am downloading directly from Nvidia and have downloaded two diff files but both say 

ould not open the file /home/oem/Desktop/NVIDIA…nux-x86-1.0-7184-pkg1.run using the Western (ISO-8859-15) character coding.

Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.


Eh??

I am downloading the right file i take it?  Linux IA32??

Many thanks for your help Taurus, it is greatly appreciated!

---

### Post by taurus on 2007-01-03
Don't download the one from nVidia's site.  Use the guide that I posted to install it.  Easier that way...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by kolakube on 2007-01-03
Mate I dont mean to sound out of turn, it was all going great.

What a hassle just to get a decent res.

6 steps and a load of typing that takes me back to my thankfully forgotton DOS days.


with XP its click once and thats it


Again I dont mean to sound rude or out of turn but offer an observation that could put many an otherwise XP convert off.

I mean, this is something you need to do before you can even appreciate a decent res.

Makes me think things I do on XP in a minute will take ten on linux

---

### Post by kolakube on 2007-01-03
OK, Rather than editing and deleting the above Im going to take this one on the chin.


ITS NOT UBUNTU THATS CAUSING MY LACK OF RES, ITS MY STUPIDITY!!!!!!!!!!](*,) 

Im was trying to use it on my server (not my desktop) that hasnt even got an nvidia card in it.
Yes im a total plonker but an honest one.:rolleyes: 


I have since installed ubuntu on my desktop with 7900gt gfx card and it detects and works fine from the offset.

I am very impressed with Ubuntu!!!!  Very impressed indeed and I would hate my earlier mark to cloud that. Esspecialy as it was my error.

Kola:cool:

---

### Post by bodhi.zazen on 2007-01-03
LOL kolakube, I hate it when that happens !

---

### Post by webgeek1 on 2007-01-03
I am having a similar issue only I get one choice...640x480. I need 1024x768 I have a dell inspiron 1100. I don't know all the techie details...as I am just trying this out.
I have NO clue what I am  doing here. Like I said I am very very new to linux period.
Thanks for any help possible!
~Jeremy

---

### Post by taurus on 2007-01-03
> **webgeek1 said:**
> I am having a similar issue only I get one choice...640x480. I need 1024x768 I have a dell inspiron 1100. I don't know all the techie details...as I am just trying this out.
I have NO clue what I am  doing here. Like I said I am very very new to linux period.
Thanks for any help possible!
~Jeremy

Are you sure you have an nVidia graphic on your machine?  I believe most Dell machines come with one of the Intel onboard graphic controllers (unless you upgrade it to ATI or nVidia card).  Therefore, what's the output of this command from a teminal?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by bodhi.zazen on 2007-01-03
> **webgeek1 said:**
> I am having a similar issue only I get one choice...640x480. I need 1024x768 I have a dell inspiron 1100. I don't know all the techie details...as I am just trying this out.
I have NO clue what I am  doing here. Like I said I am very very new to linux period.
Thanks for any help possible!
~Jeremy

This is how I solved the problem:

[http://www.ubuntuforums.org/showpost.php?&p=1799642&postcount=15](http://www.ubuntuforums.org/showpost.php?&p=1799642&postcount=15)

---

### Post by Shatrat on 2007-01-03
> **webgeek1 said:**
> I am having a similar issue only I get one choice...640x480. I need 1024x768 I have a dell inspiron 1100. I don't know all the techie details...as I am just trying this out.
I have NO clue what I am  doing here. Like I said I am very very new to linux period.
Thanks for any help possible!
~Jeremy

Same questions apply Jeremy.  Do you know what graphics chipset you have?  Unless you have an aftermarket card installed I believe you have an Intel chipset.  I'm not familiar what is involved in installing drivers for this chipset.  

I think the Intel drivers are open source unlike nvidia and ATI are included with Ubuntu and maybe all you need to do is add "1024x768" to the Mode lines in the Screen section of /etc/X11/xorg.conf

---

### Post by kolakube on 2007-01-04
As I have found out also, if your using VM ware unless you have VM ware tools installed, VM ware itself will only allow a res so high.

Hey, im as new as you if not newer lol

---

