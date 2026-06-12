---
title: "Broadcom BCM4306"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by dtholen on 2007-03-12
Now that I have successfully installed 6.10 I am trying to figure out how to connect to the outside world. I have an HP zd7160 laptop using a Broadcom card with a BCM4306KFB chip and have read of the difficult experiences to configure this card to use wireless. Is there an appropriate tutorial or instructions available that could get me started in the right direction?

---

### Post by Ek0nomik on 2007-03-12
[http://www.ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://www.ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306)

I hope this can offer you some assistance.

Cheers!

---

### Post by overdrank on 2007-03-12
> **Ek0nomik said:**
> [http://www.ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://www.ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306)

I hope this can offer you some assistance.

Cheers!

Woo hoo  thanks, the second link worked great and I am wireless. Man you have to luv the ubuntu Community. Great work people and thanks again!=D>

---

### Post by arron on 2007-03-12
> **paul capps said:**
> Woo hoo  thanks, the second link worked great and I am wireless. Man you have to luv the ubuntu Community. Great work people and thanks again!=D>

All hail the Ubuntu community =D> !

---

### Post by dtholen on 2007-03-13
Nope, didn't work for me.....yet. Here is another observation that may be causing me some trouble. I have an HP zd7160us laptop with a button that can turn on and off the wifi card. Presumably to save on power when wifi is unavailable and you are operating on battery power. It functions normally when booting with XP but remains off and will not function when booting Ubuntu. Anyone have experience with HP Pavilion zd7000 series laptops with this feature?

---

### Post by jdfreshwater on 2007-03-13
The button still works under Ubuntu, it may or may not show the light, but you may need to use it to start the wireless connection.

---

### Post by dtholen on 2007-03-13
> **jdfreshwater said:**
> The button still works under Ubuntu, it may or may not show the light, but you may need to use it to start the wireless connection.

If the light does not work, then what indication is there that your wireless card is powered up?
I have been struggling to get Ubuntu to access Wifi without success. Thought maybe this was part of the problem.

---

### Post by dtholen on 2007-03-13
Here is another observation that looks significant. I have been attempting to install using ndiswrapper. At one point the instructions were this:

sudo ndiswrapper -l 

The response is:
bcmw15 driver present, hardware present, bdmwl5 invalid driver!

Note that it is "bdmwl5" and not "bcmwl5". Am I using a bad driver perhaps? If so where can I get a clean copy of bcmwl5.sys and bcmwl5.inf?

---

### Post by lamalex on 2007-03-13
did you try getting the exe from hp and then using cabextract to suck out the .sys and .inf files?

---

### Post by dtholen on 2007-03-13
> **Iamalex said:**
> did you try getting the exe from hp and then using cabextract to suck out the .sys and .inf files?

No, I didn't. Can you tell me where I can find information about this process and how to use "cabextract"? Were talking newbie here.

---

### Post by Matt1632 on 2007-03-14
I'm also having problems, I've tried both of those guides in the past and I had to reinstall on both occasions.  Fwcutter worked for a while, then all my networking stopped working entirely.  With ndiswrapper it didn't work, it listed my card as eth1 rather thatn wlan0.  Then when I followed the instructions to fix that I lost my GUI. I also have an HP laptop with a button, but after 2 reinstalls I've given up on trying to get my 4306 card working...:(

---

