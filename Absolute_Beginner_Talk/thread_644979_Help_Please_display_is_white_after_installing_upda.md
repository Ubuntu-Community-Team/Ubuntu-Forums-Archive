---
title: "Help Please display is white after installing updates"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by khgiese on 2007-12-19
I am fairly new to ubuntu, so i  don't do much messing with my Ubuntu since I got it set up and working as I thought it should.
I downloaded some patches to today and now after I log in and should see the desktop, i see a blank white screen. I checked my xorg.conf file to to verify that nothing there has changed. 
If i use the Ctl+ Alt+F1 I can see the desktop as the screen switches. Also if I shut down the system I can see the desktop for a brief second before the shut down.

Please help.


KHGiese

---

### Post by khgiese on 2007-12-19
I think I have discovered that it is in the compiz package. If i use metacity --replace command I get my desktop back, but if I try to enable the compiz I get the white screen,
Here is the part that baffles me, some of the compiz package works, I can use the cube function to "roll" the screens but they are all white.

---

### Post by khgiese on 2007-12-19
I read through the install logs and it appears the following packages were installed at the time of the problem;
Libc6 2.6.1-lubuntu10
linux-image-2.6.22.14.generic
linux-headers-2.6.22-14-generic
linux-libc-dev 2.6.14.46
Question is how do I roll it back to the previous version?

---

### Post by khgiese on 2007-12-20
So here the steps used to solved my problem with the white screen.

A brief back ground on my video issues when I set up Ubuntu.

When i first used Envy setting up Ubuntu (a month or so a go) I took all the  all the defaults and even let Envy reconfig the xorg.conf file. This failed to give me the results I was looking for, namely the ability to use the Compiz Cube and cube rotate function. I spent a coulpe days tweaking my xorg.conf file after reading several blogs on the subject. Finally I managed to get the Compiz effects working with a very stripped down xorg.conf file.


This time I went through the same steps that worked before and used Envy to remove and install the ATI drivers without configuring the xorg.conf file. This did not resolve the white screen problem.

So with lots of reservations I let Envy uninstall and reinstall the ATI drives and reconfigure the Xorg.conf file. after rebooting I could now turn on the effects of compiz.

So even though it works, I am no wiser as to the real fix other then to praise Envy for doing what I could not.


Khgiese

---

