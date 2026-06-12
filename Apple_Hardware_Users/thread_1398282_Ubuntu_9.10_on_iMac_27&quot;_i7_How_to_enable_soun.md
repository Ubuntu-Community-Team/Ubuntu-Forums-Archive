---
title: "Ubuntu 9.10 on iMac 27&quot; i7: How to enable sound and scroll-multitouch on Magic Mouse?"
date: 2010-02-04
forum: Apple Hardware Users
---

### Post by Kaos2K on 2010-02-04
Hi. 

I have and iMac 27" i7 with 4GB RAM and Ati HD 4850 graphics card. After so much triying i was able to install Ubuntu 9.10 64Bits (fighting against graphic issues solved installing restrictive driver FGLRX after installing from LiveCD using "secure graphics mode" at boot).

Now i'm triying to get the sound working via internal speakers and the Apple Magic Mouse scroll and multitouch functions.

For the sound i installed Alsa backport drivers:

```

aptitude update
aptitude install linux-backports-modules-alsa-karmic-generic
```Now sound is working through headphones but not from Speakers. I tried to unmute all channels with:

```

alsamixer

Using "m" key to unmute.

```But still no luck.


In the other part, the Apple Magic Mouse works well (you have to press buttons repeadtly to activate it each time you enter in Ubuntu) but without scroll or multitouch functions. I read that there is a series of patches to get it working but they need to recompile the kernel and i never do that before and i a bit lost.

 The patches are located here: [http://github.com/entrope/linux-magicmouse](http://github.com/entrope/linux-magicmouse)


I need some help with both problems. 

Thanks in advance.

---

### Post by Q007 on 2010-02-18
Hi, 

I'm in exactly the same position as you are. I've installed the alsa backport module, and sound works through headphones, but not the speakers.

Did you have any luck with that?

Now I have to sort out the mouse and everything else. At least I have my nice 2560x1440 display sorted out.

Cheers,
Q

---

### Post by linuxopjemac on 2010-02-19
Sound for this machine will work in kernel 2.6.33.
[http://mac.linux.be/content/more-apple-improvements-kernel-2633](http://mac.linux.be/content/more-apple-improvements-kernel-2633)

Apple multitouch mouse: for 64-bits users you can try the newly compiled karmic koala kernel 2.6.31-20.something:
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=82#p82](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=63&p=82#p82)

---

### Post by Kaos2K on 2010-02-19
> **Q007 said:**
> Hi, 

I'm in exactly the same position as you are. I've installed the alsa backport module, and sound works through headphones, but not the speakers.

Did you have any luck with that?

Now I have to sort out the mouse and everything else. At least I have my nice 2560x1440 display sorted out.

Cheers,
Q

I did not try, i was very busy with some things.

I'll wait to new kernels of ubuntu new versions because it seems to work with that :)

---

### Post by debutant10 on 2010-04-09
Hello,
 
I have a computer with the same configuration as Kaos2K: iMac 27" i7 with 4GB RAM and Ati HD 4850 graphics card.
 
Trying to install ubuntu 9.1 64b karmic Koala I am having problems with the 
drivers of the graphic card.
 
I try to proceed as explained by Kaos2K booting from the liveCD using "secure 
graphics mode" but I could not find this option. Could you please give me more 
details about what you did ?
It would really help me. 
 
Thank you very much in advance.

---

### Post by Kaos2K on 2010-04-09
> **debutant10 said:**
> Hello,
 
I have a computer with the same configuration as Kaos2K: iMac 27" i7 with 4GB RAM and Ati HD 4850 graphics card.
 
Trying to install ubuntu 9.1 64b karmic Koala I am having problems with the 
drivers of the graphic card.
 
I try to proceed as explained by Kaos2K booting from the liveCD using "secure 
graphics mode" but I could not find this option. Could you please give me more 
details about what you did ?
It would really help me. 
 
Thank you very much in advance.


Mate, i just browse the internet to remember what i did to get the imac working and i found this: [http://www.technicaljar.com/?p=267](http://www.technicaljar.com/?p=267)

When you press F4 a safe graphics mode must be selected. When you mailed me i tried to boot LiveCd again but that option disapeared form the menu as yours. I only get Normal mode in the chart. It's strange.

---

### Post by Kaos2K on 2010-04-09
Hello again. I just checked the LiveCD another time and this time i can select the secure graphics mode option when i press F4. I assume the problem is bad CD reading.

I made a screenhot using french language (I assume you are french because the .fr suffix in your email adress).

Take a look:

[[IMG]http://i251.photobucket.com/albums/gg285/Kaos2K/th_IMG_0047-1.jpg[/IMG]]("http://s251.photobucket.com/albums/gg285/Kaos2K/?action=view&current=IMG_0047-1.jpg")

---

### Post by debutant10 on 2010-04-09
Oh my God I am so stupid ! I went through all the F key options and I did not see it !!!
 
You just saved me.
 
 
ps: Please don't change your opinion about french people. 
I am the only one who is stupid .....

---

### Post by Kaos2K on 2010-04-09
> **debutant10 said:**
> Oh my God I am so stupid ! I went through all the F key options and I did not see it !!!
 
You just saved me.
 
 
ps: Please don't change your opinion about french people. 
I am the only one who is stupid .....

Don't worry mate. All make mistakes :P.

Hope it works for you. Remember to install the propietary video driver FGLRX after installing ubuntu to get full video performance ;)

---

### Post by debutant10 on 2010-04-09
Yes I installed the proprietary driver.

Except for the sound and the magic mouse everything is 
working perfectly fine. 

Thanks again for your help !

---

### Post by xvila on 2010-04-09
> **debutant10 said:**
> 

Except for the sound and the magic mouse everything is 
working perfectly fine. 



For the sound:

Try adding  "model=imac27" to the  last line in /etc/modprobe.d/alsa-base.conf so that it reads:

options snd-hda-intel model=imac27 power_save=10 power_save_controller=N

and reboot

For the magic mouse:

 ... I am wating as well ...

xavi

---

### Post by Kaos2K on 2010-04-09
> **debutant10 said:**
> Yes I installed the proprietary driver.

Except for the sound and the magic mouse everything is 
working perfectly fine. 

Thanks again for your help !ç

For the sound use this tutorial: [http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=64&p=84#p84](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=64&p=84#p84)

It works :)

---

### Post by jisaac on 2010-04-15
Did someone try it with Lucid Lynx?

---

### Post by jisaac on 2010-04-17
Did it! And can't find any "safe graphic mode"...

I've just create a new thread:
[http://ubuntuforums.org/showthread.php?t=1456439](http://ubuntuforums.org/showthread.php?t=1456439)

---

### Post by jisaac on 2010-04-23
For the sound issue if you've updated to a more recent kernel (2.6.31-20 or 2.6.31-21) use "model=imac27" in "/etc/modprobe.d/alsa-base.conf".

Works for me on Ubuntu 9.10 64bit with "2.6.31-21-generic" kernel. Remember to unmute everything in the alsamixer and set all the volumes correctly.

See this thread for more explanations:
[http://ubuntuforums.org/showthread.php?t=1351591&page=3](http://ubuntuforums.org/showthread.php?t=1351591&page=3)

PS: The internal microphone works but the recorded sound volume is very low although I push the input volume to the maximum! I have the same issue with 10.04.
See: [http://ubuntuforums.org/showthread.php?t=1459475](http://ubuntuforums.org/showthread.php?t=1459475)

---

### Post by jisaac on 2010-04-23
With Skype the microphone issue is worst! :(

---

### Post by jisaac on 2010-04-24
My USB Logitech microphone does not work at all on 9.10!

PS: But it does perfectly work with 10.04!

---

