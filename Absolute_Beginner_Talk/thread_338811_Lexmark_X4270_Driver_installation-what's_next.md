---
title: "Lexmark X4270 Driver installation-what's next??"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-15
Ok I downloaded the driver for my Lexmark X4200 Multi-function printer and placed it in my Home folder. I have ndiswrapper installed and tried using it but it says there are no drivers installed. How do I get the program to find the driver and install it? Thanks for the help in advance--you guys have made the transition to linux very painless and very very interesting. Thanks again!!
P.S. The driver I downloaded is for Windoz XP.

---

### Post by oyvindaa on 2007-01-15
I think the driver has to be a .inf file(?), if that's what you've got you should be able to browse your way to it from ndiswrapper.

Did you manage to install that Yahoo Messenger by the way?

---

### Post by jerrynewt on 2007-01-15
Hmmm the only download available from Lexmark is an exe file (CJB4200EN.exe). I wonder where I get the inf file? As to Yahoo messenger I found a website (can't remember which one) saying that ymessenger wasn't avialable for Ubuntu as yet but was for Debian. I thought Ubuntu was a Debian based distro. I am starting to get really confused. Any light on the subject would be appreciated. Thanks again!!

---

### Post by uboat on 2007-01-15
As for problem #1 you Lexmark printer deep six it and purchase a Hp Officejet 6310 all in one.
And the second issue with Ubuntu and their being no version of yahoo messenger I'd recommend using the included gaim client.

---

### Post by jerrynewt on 2007-01-15
Yes I am using Gaim and am not even going to mess with ymessenger anymore--lots of more inportant things to play with on linux. Your suggestion on the choice of printers is well taken. All I see on these posts about Lexmark printers is negative--time to jump ship and simpify my life. Thanks for the quick response again and I'm sure I will be back with more questions in a bit.

---

### Post by Jeremiah Cornelius on 2007-04-01
Divers WORK with Gimp Print!

Select as the Pinter Model Lexmark Z42. This is the equivalent printer to the x4270, without scan and fax.

Worked flawlessly, in my situation - I am printing across a network to a Windows Print queue - local USB should also work the same.

See:
[http://lists.freestandards.org/pipermail/printing-user-lexmark/2005/003084.html](http://lists.freestandards.org/pipermail/printing-user-lexmark/2005/003084.html)

---

### Post by sciurus on 2007-08-07
> **Jeremiah Cornelius said:**
> Divers WORK with Gimp Print!

Select as the Pinter Model Lexmark Z42. This is the equivalent printer to the x4270, without scan and fax.

Worked flawlessly, in my situation - I am printing across a network to a Windows Print queue - local USB should also work the same.

See:
[http://lists.freestandards.org/pipermail/printing-user-lexmark/2005/003084.html](http://lists.freestandards.org/pipermail/printing-user-lexmark/2005/003084.html)
Choosing Z42 also worked for me.

---

### Post by AsburySteve1952 on 2007-08-27
I installed my driver as per the Z42 instructions. The printer then printed a test page, then 1 1/4 pages and froze. I tried another doc, and it won't print at all now. Any ideas?

Steve:guitar:

---

### Post by spinoff on 2007-10-11
Guys, I am an ABSOLUTE newbie to Linux. I installed Ubuntu Feisty Dawn 7.04 last week and, naturally, struck trouble when attempting to install my Lexmark X4270. After compiling much, much web info I stumbled through an installation of Gutenprint 5.0 and then found I had to install CUPS. I eventually installed the printer using the Z42 driver. Still stumbling around in the dark I input [http://localhost:631/](http://localhost:631/) into my web browser. I can't recall whether I added my printer here or not. I initially failed to print a test print (I could see the job in the queue though). Anyhow, today, I revisited [http://localhost:631/](http://localhost:631/) and selected 'printers'. From this screen I successfully printed a test print. I then successfully printed from Open Office. I don't know if I was a lucky stumbler or not but hope this helps another user.

:popcorn:

---

### Post by hurricaneflyer on 2007-10-18
Thanks all,
I had been trying the z42 (and almost everything else under the sun) through /system settings/printers, and didnt even get a peep from my lexmark x4270.

Then I saw spinoffs post and tried the [http://localhost:631/](http://localhost:631/) interface, Tadaa! now the printer part of my x4270 works like a charm!

Thanks again.

---

### Post by Fady on 2007-10-29
had same problem but spinoffs thing worked! thankyou!

---

