---
title: "i can't install anything from the updaters or package managers"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by lowsignal on 2008-04-17
hello everyone,

i'm running 7.10 on a dell inspiron 1525 laptop. only ubuntu, no widows  xp or any other operating system is installed.

i created three users, originally just one had administrator privileges. i couldn't find wine installed with the users with no administator privileges, so i gave one of them administrator privileges and tried to install wine with automatix. that's when the problems began.

wine froze so i executed "sudo killall automatix.py" and it unfroze. i thought all was fine until update manager notified me that i had 12 updates and i tried to install them. update manager said it "could not get exclusive lock". i don't know how to find and kill or stop the offending process.

when i try to run synaptic package manager it tells me i need to run "sudo dpkg --configure -a"..... when i do that i get this message.

============================

msttcorefonts uses defoma                                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474;  
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474;  
 &#9474; configure it to use defoma fonts.                                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474;  
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474;  
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474;  
 &#9474; printing) this is not required.     

============================

so i'm stuck i don't know what to do much less what to do first.

i've spent hours getting the browsers and other software installed so i'd really like to avoid doing a reinstall if i can.

i can download things from the internet and use email and just about everything thing else seems to work. i just can't install anything anymore.

any advice?

thank you.

---

### Post by Oldsoldier2003 on 2008-04-17
> **lowsignal said:**
> hello everyone,

i'm running 7.10 on a dell inspiron 1525 laptop. only ubuntu, no widows  xp or any other operating system is installed.

i created three users, originally just one had administrator privileges. i couldn't find wine installed with the users with no administator privileges, so i gave one of them administrator privileges and tried to install wine with automatix. that's when the problems began.

wine froze so i executed "sudo killall automatix.py" and it unfroze. i thought all was fine until update manager notified me that i had 12 updates and i tried to install them. update manager said it "could not get exclusive lock". i don't know how to find and kill or stop the offending process.

when i try to run synaptic package manager it tells me i need to run "sudo dpkg --configure -a"..... when i do that i get this message.

============================

msttcorefonts uses defoma                                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474;  
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474;  
 &#9474; configure it to use defoma fonts.                                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474;  
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474;  
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474;  
 &#9474; printing) this is not required.     

============================

so i'm stuck i don't know what to do much less what to do first.

i've spent hours getting the browsers and other software installed so i'd really like to avoid doing a reinstall if i can.

i can download things from the internet and use email and just about everything thing else seems to work. i just can't install anything anymore.

any advice?

thank you.

Another satisfied Ax user... 

You might try posting for recovery help on the [automatix forums]("http://www.getautomatix.com/forum/"). usually my advice when Ax fails is go ahead and backup your data and do a reinstall. Automatix is not officially supported so those forums may be your best bet for recovering short of reinstalling.

you could try sudo apt-get install -f and hope that that fixes it, but a crash in automatix usually means you need a reinstall...

---

### Post by lowsignal on 2008-04-17
ugh.. ok, i was afraid of that. i'm going to look on the automatix forums for some kind of answer. i might wait to do a reinstall for when i upgrade to hardy (8.04).

thanks Oldsoldier. always better to get the bad news sooner than later. btw, do you know where i can learn to make a backup and how to install it in a brand new reinstall?

i'm very new to ubuntu but i love it and am never going back to windows. i'm going to learn this OS but it will be a slow process..

thanks for the advice, every bit helps.

---

### Post by zvacet on 2008-04-17
@ 

>  i couldn't find wine installed with the users with no administator privileges

System>preferences>main menu>accessories and see if wine is there.If not create new launcher 

name = wine
command = /ust/bin/wine
icons = /usr/share/pixmaps

---

### Post by lowsignal on 2008-04-17
hi zvacet,

it was there. thank you for showing me that.

---

### Post by BOOBOOJS on 2008-04-17
Normally when you install msttcorefonts with synaptic or adept you get a dialog box that pops up and states the same info as in your error message. Then you can click ok and be done with it.

You might be able to uninstall it with "sudo apt-get remove msttcorefonts" and the reinstall it with "sudo apt-get install msttcorefonts" 

First I would try sudo dpkg-reconfigure msttcorefonts

Next time you can install msttcorefonts using a different method:
Add the medibuntu repo, the instructions are on medibuntu.org
And then just use synaptic or apt-get to install them for you.

Most of the things that Ax installs for you are accessible in synaptic with the proper repos enabled.
The rest are easily installed via how-tos in this forum
:popcorn:

---

### Post by lowsignal on 2008-04-17
i just now tried "sudo apt-get remove msttcorefonts"

i got this in response..

"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

i don't think i'll ever use automatix again. i didn't know i could get most of the same programs with other installers.

thank you for your help.

---

