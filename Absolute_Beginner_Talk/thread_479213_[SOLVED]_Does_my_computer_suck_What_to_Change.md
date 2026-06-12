---
title: "[SOLVED] Does my computer suck?? What to Change??"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by JimBuntu on 2007-06-20
My computer is a little old (a couple of years). Its an hp pavillion 754n if that helps. Basically i have noticed that when i put a screen saver on like Matrix, or anyone that is really graphical my computer runs really slow even when its still in the preview window. What is this caused from. 

Specs read as follows:

2.53GHz Intel Pentium 4
512 MB DDR SDRAM memory
80 GB Ultra DMA Hard Drive
64 MB DDR SDRAM  Integrated Intel Extreme Graphics with up to 64 MB shared video memory

I know this is an older computer, but can i upgrade stuff. What is the cheapest way to go??

---

### Post by Motoxrdude on 2007-06-20
it could be caused by a lack of video drivers. Paste the output of
```
glxinfo | grep direct
```

---

### Post by atria on 2007-06-20
You are having problems with graphics because your graphics card is either not powerful enough or the relevant drivers are not installed.

If the drivers are installed, then you should either get a better graphics card (i recommend nvidia) or get a new computer altogether, since your computer might not have the PCI-Express port which is required for modern graphics cards.

---

### Post by JimBuntu on 2007-06-20
Where do i paste the above code?

Also, what is a good yet cheap way to go for a graphics card. Is there used ones out there that are better than mine?

---

### Post by Motoxrdude on 2007-06-20
Go to the top-left corner of your desktop and select "Applications>>Accessories>>Terminal". It will open a little box with some text, just copy and paste this over
```
glxinfo | grep direct
```
and paste whatever it says back here.

---

### Post by atria on 2007-06-20
Inside the console (Applications, Accessories, Terminal)

Yep there are, like the geforce FX series

---

### Post by JimBuntu on 2007-06-20
administrator@ubuntu:~$ glxinfo | grep direct
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
administrator@ubuntu:~$ 



did i do something wrong?

---

### Post by atria on 2007-06-20
The command itself should run properly. Do you have sufficient free memory? Try doing the command again after closing your applications.

---

### Post by Motoxrdude on 2007-06-20
Close all your opening applications and try that command again.

---

### Post by JimBuntu on 2007-06-20
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17


I have nothing open except one window of firefox with 3 tabs

---

### Post by JimBuntu on 2007-06-20
also i have ubuntu studio. Does that change anything?

---

### Post by atria on 2007-06-20
Weird stuff, the drivers might indeed be broken. I'm sorry i won't be able to help you any further. You might want to do a forum search or wait till someone else helps.

Good luck

---

### Post by JimBuntu on 2007-06-20
ok thanks anyways

---

### Post by JimBuntu on 2007-06-20
Does anyone else know why my computer runs super slow with graphical screensavers? Ive tried puting 

glxinfo | grep direct

into my terminal but i get the error messages

what does this mean?

---

### Post by swoll1980 on 2007-06-20
I have 2.6 Ghz celleron and 256mb ram my screen savers work fine if that helps

---

### Post by JimBuntu on 2007-06-20
ya, it helps me to realize that something is wrong with my computer. SH(T!

---

### Post by atria on 2007-06-20
Thats because swoll has a different (and much better) graphics card. I don't think it has anything to do with the other components.

---

