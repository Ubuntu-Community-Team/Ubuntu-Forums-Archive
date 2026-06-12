---
title: "Problem with the beginning..."
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by MTommy on 2005-10-07
Hello everyone....
I've just downloaded Ubuntu 5.10 for AMD64. At firt I want to say that I have a Laptop from HP, CPU Turion64 1.8ghz, 1gb DDR ram, Ati Xpress200 with 128mb shared memory and a Fujitsu 80gb.
Now, I've installed Ubuntu (the installation appeard to be good), and I lunched(?) it. When it should desplay the main page (where you have to write your user name and password) It appears a message like this: XServer cannot start. Your Graphic Interface has problems (or somthing like that). It says if I want to see the detail of the problem and then it links me to the console, where i have no idea what to do....
Did i take an uncomplatible version of Ubuntu with my Laptop or is there something that I can do to solve the problem???


PLEASE HELP ME!!!! 

Many Thanks Tommy

---

### Post by Ampersand on 2005-10-07
Hi
Press OK or Yes to see the details of the problem, then post them here. We should be able to help then. (:

---

### Post by MTommy on 2005-10-07
I'm omw..Thank you....

---

### Post by MTommy on 2005-10-07
Ok, so the error is:

Failed to start X Server (your graphical Interface) It is likely it is not set up correctly.

Then i click on ok to see the detail of the error:

At first it gives me a descritpion of the pc, then:
Skipping
"usr\x11r6\lib\modules\extension\libglcore.a:m_debug_clip.0" No symbols found

Skipping
"usr\x11r6\lib\modules\extension\libglcore.a:m_debug_norm.0" No symbols found

Skipping
"usr\x11r6\lib\modules\extension\libglcore.a:m_debug_xform.0" No symbols found

Then it says

Fatal server error. Caught signal 11

If I go futher it gives me other detail of the error, and there it says a lot about ATI graphics card, all of them,it seems that it searching mine, because at a certain point it says "ATI Xpress 200M found" (it was too long to write, but if you need that i can try to write it), and at the end it says the same thing "Fatal server error. Caught signal 11.

I hope it is enough...meanwhile i'm downloading the 5.04 version of Ubuntu.

---

### Post by Ampersand on 2005-10-07
It's possible that some of your hardware wasn't detected properly, try logging in at the prompt that comes up, then enter the command 'sudo dpkg-reconfigure xserver-xorg'.

---

