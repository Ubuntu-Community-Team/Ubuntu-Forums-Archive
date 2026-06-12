---
title: "Screen resolution problem"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by h1mself on 2007-09-20
I have a Dell Inspiron 1100 and have recently installed Ubuntu 7.0.4 on it.
My problem is that when try to change the screen resolution (System>Preferences>Screen 
Resolution) 640x480 is the only option. I want to modify it to 1024×768 because it is frustrating working with small screen with a 5cm black border around it.

      Any suggestions would be grand.

---

### Post by alienexplorers on 2007-09-20
RUN:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by tombott on 2007-09-20
As the above post says.

Maybe useful if you know or post the graphics card your using.

When running through the xserver setup you will need to select the graphics card driver to match your card.

You will also need to select the screen resolution sizes your monitor / screen will work with.

I usually start at 1024*768 and work my way up till i hit a screen res that won't work, but you may want to try a more structured approach!

Let us know how you get on!

Tom.

---

### Post by h1mself on 2007-09-20
Thanks for the feedback! 

Oh, and my graphics card is a: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Thanks,

Ben

---

