---
title: "Cant figure installed packages out????"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-01
Hi people..back again...

..If i try play any content on such as google video or you tube etc OR even put a dvd in im told i need the relevant plugins etc.

Ive looked in the synaptic package manager and have over 1000 of them installed (green box shaded) and i seem to have a lot of the stuff i seem to require installed too.

I got told i needed a decoder when i tried a dvd so when i look in the package manager IT tells me i have a couple installed that play dvd`s.

IS there something else i need to be doing to actually use these "installed" packages..

I`ve gathered a lot of the usual windows comparable tasks require that i use the terminal here in unbunto but i cant figure out whats ALREADY done and what still NEEDS done..i.e..is it installed and working OR do i need to 
do something more?????

My printer and cameras all seem to work fine and actual video off my cameras plays ok when it`s selected.......

I think im suffering that other chaps discombobulation.......

THE NEW OPERATING SYSTEM WORKED A TREAT BUT THE OLD USER HAD PROBLEMS!!!

---

### Post by T700 on 2006-08-01
Please see the link for Automatix in my sig.  It will automatically install all that you need.

Paul

---

### Post by Dinerty on 2006-08-01
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Alot of good guides here for DVD's and MP3's :)

---

### Post by xpod on 2006-08-01
Sorry for my complete ignorance here but that warning about it not already being installed looks pretty serious.
I dont seem to have a system tools option in the applications tab to go check

How do i know i aint got it??????

---

### Post by T700 on 2006-08-01
> **xpod said:**
> Sorry for my complete ignorance here but that warning about it not already being installed looks pretty serious.
I dont seem to have a system tools option in the applications tab to go check

How do i know i aint got it??????

You don't.  Just install it.  You can do it by hand, use Easy Ubuntu, or use Automatix.  It really isn't a big deal; we've all had the same issue.

Paul

---

### Post by xpod on 2006-08-01
well tried to use those three commands to install automatix but got this

--16:33:33--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
           => `automatix-installer'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,071 (7.9K) [text/plain]

100%[====================================>] 8,071         --.--K/s

16:33:34 (317.33 KB/s) - `automatix-installer' saved [8071/8071]

dad@dad-desktop:~$ chmod 755 ~/automatix-installer
dad@dad-desktop:~$ ./automatix-installer
root      8325  0.0  0.0      0     0 ?        Zs   14:03   0:06 [synaptic] <def unct>
Automatix-Installer WILL NOT run alongside Synaptic. Automatix-Installer will no w exit after a couple of seconds.
dad@dad-desktop:~$



I see what it says BUT knowing what it means is another matter

---

### Post by avtolle on 2006-08-01
You need to close Synaptic, then try automatix again. There can't be two "file getters" (apologize for the poor phrase) opoen simultaneously. So, close Synaptic; then run automatix.

---

### Post by xpod on 2006-08-01
Dont apoligise..........YOUR definitions are fine BUT my powers of deduction are sadly lacking...

IT IS CLOSED.......i assume thats it stopped "running" when i close it?

OR is it like still actually running like some process and needing killed somewhere..

I hope this dont turn into another of those "aplogy competitions"..haha

---

### Post by avtolle on 2006-08-01
Sometimes, I understand, Synaptic will be running in the background for a short period after it has been "closed". So, try automatix again assuming some time has passed since closing Synaptic. BTW, there is an Automatix subforum here under Third Party Projects (?), where you might find help if the error message continues. HTH.

---

