---
title: "Google Analytics - Results not displaying properly"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by OMJD on 2006-11-04
Hi,

Whilst this problem is not directly linked to Ubuntu, I believe it is something only affecting Linux OS's as this issue does not occur on Mac OS X or Windows.

The problem is that the figures don't display properly on the charts. Any idea what's causing it? I have Flash 7 installed and am using Firefox 2.0. I have also tried using Opera but encounter the same problem.

Anyone know why I have this problem?

I know I probably should be emailing this to Google, but I think that'd turn out to be a waste of time.

Thanks for your time.

---

### Post by staib on 2006-11-11
I too have noticed this - if anyone has any pointers or solutions that would be great...

---

### Post by staib on 2006-11-11
I've answered this one myself :) 

A workaround of sorts but quite useful. Took no more than 3 minutes and works a treat.

Follow the [instructions here]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

I only installed IE6 (you get the option to add IE5 and IE5.5). 

It's also useful for those inevitable IE6 only sites you still stumble across out there.

Nick

---

### Post by nikkiana on 2006-11-11
I believe it may be because you don't have the font installed that Google Analytics uses to display all it's text (I vaguely recall having this same problem when I first swtiched to Linux). 

The easiest way to install the True Type font set is to just use [Easy Ubuntu](http://easyubuntu.freecontrib.org/) and install it using that... and I believe that will solve your problem. :)

---

### Post by willcritchlow on 2006-12-14
Thanks for the tips guys. I now have this working.

I have just notified Google because their [Analytics help page]("http://www.google.com/support/analytics/bin/answer.py?answer=27239&query=ubuntu&topic=&type=") says this can't be fixed.

I now have it working after searching for gsfonts in Synaptic package manager and installing everything in sight :) I suspect it might have been gsfonts-x11 that made the difference.

This has been bugging me a for a while - I kept having to use my Mac to look at analytics!

---

### Post by axle_foley00 on 2006-12-14
You could have also tried installing the [Flash Player 9 beta 2]("http://labs.adobe.com/technologies/flashplayer9/").

---

