---
title: "The software source for the package nvidia-glx-new is not enabled."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Matymoo on 2007-10-19
I have been searching high and low for a simple to follow way to resolve this. I am disappointed. I have been using ubuntu for around 10 months now and Gutsy is giving me far more trouble than I have experienced with any other release because of the above issue. Can anyone provide a straight forward simple to follow fix for this?

---

### Post by bruce89 on 2007-10-19
Tick all the boxes in Software Sources (main, restricted, universe, multiverse).

Incidentally, Brisbane is named after someone who was born near here.

---

### Post by Matymoo on 2007-10-19
thanks, will give it a go ;-) Incidentally, I believe my surname comes from where you live.... Rea.

---

### Post by Matymoo on 2007-10-19
ticked all boxes and get this message 

[I]The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.[/I]

Reload and getting "failed" for the first 2 packages and it hangs on the third. 

url seems to be cdrom://Ubuntu 7.10_...etc for the first 2 ???

I have the CD in the drive. Hmmmmm

I never had any probs like this with Edgy or Feisty :-(

---

### Post by bruce89 on 2007-10-19
> **Matymoo said:**
> ticked all boxes and get this message 

[I]The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.[/I]

Reload and getting "failed" for the first 2 packages and it hangs on the third. 

url seems to be cdrom://Ubuntu 7.10_...etc for the first 2 ???

I have the CD in the drive. Hmmmmm

I never had any probs like this with Edgy or Feisty :-(

Untick the CD-DVD thingy at the bottom.

---

### Post by Shlomir on 2007-10-19
yeah it seems nvidia-glx-new is stuffed...uninstall is and just use nvidia-glx...

THEN you'll prolly have trouble getting it as all the Aussie repos and stuffed and there's nothing to download, you might have to find pone on the Soviet Republic or Guatemala!

I was albe to unintall glx-new from Package manager, and reinstall the plain vanilla nvidia-glx..

Then I was able to activate the driver via the Restricted Drivers Manager and it all loaded hunky dory and I got my 3D gay-cube working and the like

But yes, they still haven't perfected the graphics driver issues.:mad:

---

### Post by Matymoo on 2007-10-19
done that! getting fails on everything :-([IMG]http://img156.imageshack.us/img156/3677/screenshotyt6.jpg[/IMG]

---

### Post by Matymoo on 2007-10-19
hahaha mirror.yandex.ru seems to work!!

Typical Australian servers!! There is a report in todays news that discusses how us Australians pay around 9 times more for broadband that is 35 times slower the worlds fastest countries. 

[http://www.news.com.au/business/story/0,23636,22616385-462,00.html](http://www.news.com.au/business/story/0,23636,22616385-462,00.html)

Our internet SUX!!!!!! Hopefully a change of government will rectify the problem. I'm off door knocking for the opposition now! Doing my bit to fix our broadband hahaha

Thanks for the assistance. Hopefuly it will solve my probs.

---

### Post by Matymoo on 2007-10-20
[http://ubuntuforums.org/showthread.php?t=563937](http://ubuntuforums.org/showthread.php?t=563937)

followed this thread and it fixed my probs!

---

### Post by techgermz on 2007-10-20
> **bruce89 said:**
> Tick all the boxes in Software Sources (main, restricted, universe, multiverse).

I was having the exact same issue, with my just installed Gutsy. The above worked for me like a charm. Being a newbie ubuntur, the only hiccup I had was finding the "Software Sources" option [found under System -> Administration] #-o,

Thanx guys... :-)

---

### Post by vugh on 2007-10-24
i followed this thread and now the problem is fixed! thanks

---

### Post by twodayslate on 2007-12-10
OK, here is what I have checked under Software Sources. BTW, I have no internet connection (trying to install wireless card).
-> Ubuntu Software -> everything but Installable from CD-Rom
-> 3rd Party ->Everything
->updates -> everything

I am also having the same error with the Broadcom 43xx chipset
called bcm43xx-fwcutter

edit:// this did it: [http://ubuntuforums.org/showthread.php?t=488130](http://ubuntuforums.org/showthread.php?t=488130)

---

### Post by Newy11 on 2008-02-02
> **bruce89 said:**
> Tick all the boxes in Software Sources (main, restricted, universe, multiverse).

Incidentally, Brisbane is named after someone who was born near here.

This also worked for me ;)

Did the older versions of ubuntu have these ticked on as defult? cause i remember i didnt have to do that in the version before Gutsy

---

### Post by bruce89 on 2008-02-02
> **Newy11 said:**
> This also worked for me ;)

Did the older versions of ubuntu have these ticked on as defult? cause i remember i didnt have to do that in the version before Gutsy

AFAIK, Gutsy was the first to have them all ticked.

---

### Post by frogitts on 2008-03-04
So, I'm having a similar problem to all this. The big catch is that I don't have internet access on the computer I'm trying to install the driver for. So.

I've gotten through the initial installation of NVIDIA-Linux-x86-169.12.pkg1.run on Gutsy (2.6.22-14), so now I'm trying to enable the advanced effects in the Preferences>Appearance app. Of course, whenever I check the "normal" or "extra" options, it asks me to enable the driver, and then when I choose to enable the driver, it gives me the "The software source for the package nvidia-glx-new is not enabled" message.

Now, of course, since I'm not connected to the internet, the software source for the package nvidia-glx-new will NEVER be enabled, because Ubuntu prevents you from enabling a source it can't access.

So then I figure the problem isn't really that the software source isn't enabled; the problem behind all this is that nvidia-glx-new isn't installed. So I download the .deb for nvidia-glx-new, and its dependant nvidia-glx. I try to install nvidia-glx-new just to test it and sure enough, it gives me a dependancy error citing "nvidia-glx" as the missing package. So I install nvidia-glx, and that goes smooth. I now open the nvidia-glx-new deb file and it gives me an error saying that it conflicts with package "nvidia-glx". 

So I can't install nvidia-glx-new no matter what I try, and I can't enable the repositories because I have no way to connect this computer to the internet. To top it all off, I can't use apt-zip, because the only internet-enabled computer I can access runs Windows XP. 

So, does anyone have any ideas as to how I could enabled the "extra" option in the appearances app with all these circumstances?

---

