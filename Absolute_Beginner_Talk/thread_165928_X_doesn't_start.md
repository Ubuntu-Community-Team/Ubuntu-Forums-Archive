---
title: "X doesn't start?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-04-25
I just upgraded from Breezy to Dapper by way of editing xorg.config and everything worked alright until I rebooted.  Now X doesn't start.  I've tried configuring my xserver-xorg settings but I still get the same error message.  It says....

Failed to open framebuffer device
and
Screen(s) found but none have a useable configuration

Any ideas?

---

### Post by Stealth on 2006-04-25
What card do you have?

---

### Post by masooga on 2006-04-25
[QUOTE=Stealth]What card do you have?[/QUOTE]

Nvidia GeForce something or other, I forget off the top of my head.  It's an inspiron 9300.

---

### Post by danielph on 2006-04-25
When you reconfigured xorg did you run sudo dpkg-reconfigure xserver-xorg?

If you didn't then it's probably worth doing. If you did, did you say yes to "Use kernel frame buffer device?" If so it maybe worth saying no.

Just my guess.

Dan

---

### Post by pbaehr on 2006-04-25
I had to reinstall my nvidia drivers after I did a dist-upgrade to Dapper. I had the same trouble you did. You may want to try the same. There is a good tutorial floating around here regarding installing the nvidia drivers for Dapper. I'll see if I can find it for you.

Edit: Here's the link: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by masooga on 2006-04-25
Installing the nvidia drivers worked!  Thank you so much!

---

### Post by pbaehr on 2006-04-25
Excellent. Glad to hear it!

---

