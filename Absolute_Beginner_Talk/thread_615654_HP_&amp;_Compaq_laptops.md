---
title: "HP &amp; Compaq laptops"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-11-17
The threads seem to say if you have HP or Compaq, steer clear of gutsy. 
 
Is there anything in the works to ensure Hardy doesn't leave these brands stranded?

---

### Post by TidusBlade on 2007-11-17
Have you tried it yet? I dont know about you, but the best way to find out if something works is to try it ;)

---

### Post by irw on 2007-11-17
I have an HP pavilion dv88396 - and it works perfectly 

The only problem was the sound - the volume control did not work initially, but that was easily sorted by selecting both master and PCM under System/Preferences/Sound

---

### Post by evilregis on 2007-11-17
I've got an HP dv9000 notebook and I've been running Ubnuntu on it since Feisty.  Everything that I use worked out-of-the-box.  The built-in web cam in the montior, the wireless, the touch-sensitive volume controls, all USB ports, video drivers, SD reader, etc.  

As well, it's running just fine on my wife's HP.  I forget her model number right now and I'm too lazy to run and check but it's about a year and a half old.

I would agree with TidusBlade... just give it a shot using a live CD (Ubuntu Desktop CD) to see what works and what doesn't.

---

### Post by RH9R on 2007-11-17
The live cd is what convinced me to stay w/ feisty. The noapci etc parameters on boot got feisty working. That some have had an easy time is not surprising, but the threads are full of 'Don't try Gutsy' on an HP or Compaq. 
 
The time spent getting feisty up & stable makes me gunshy of trying to go through it again to get gutsy up. 
 
I'm glad it has worked well for you. Are you running Intel or AMD chips? This little compaq has the amd.

---

### Post by TidusBlade on 2007-11-17
If you dont wanna risk it, I suggest making a smaller partition, maybe around 5GB and use it to install and try out Gutsy.

---

### Post by Cybergod on 2007-11-17
I have an HP zv5476cl laptop and Gutsy runs just fine on it.  The only thing that doesn't work is my Texas Instruments 1620 memory card reader.  I have tried everything I know and then some but still can't get it to work.  If anyone knows anything about this and possibly a way to get it working I'll appreciate it.

---

### Post by deep.tinker77 on 2007-11-17
I have to agree with RH9R, i just received my brand new hp dv9500t and i've read nothing but install fiesty and wait on gutsy. I'm pretty sure in a month or two, most of the kinks will be worked out (hopefully :) ) so i guess i'll just wait.

---

### Post by evilregis on 2007-11-17
My notebook (dv9000) is Intel Centrino Duo and my wife's PC is AMD64.  However, I installed i386 on it instead of AMD64 because I'd read about a lot of problems getting 64bit apps.  But they've both worked extremely well for me.

---

### Post by Inxsible on 2007-11-17
HP dv9000t over here. and everything works perfectly.

Gutsy even rectified my suspend and hibernate which didnt work in feisty

---

### Post by GaryLittlemore on 2007-11-17
I have a HP NX9005, works fine for me. I've had a problem with the 'Black Screen/Booting Problem' but that has been fixed now, and I have a problem with the keyring manager  which is still to be fixed.

---

### Post by ru7hl3ss on 2007-11-17
I have the dv9500t, and everything worked out of the box, except wireless and sound. I had some freezing running Compiz, but that is taken care of now. 

My only issue seems to be... heat. Idle around 29C for both CPU's in Vista, and 45C in Ubuntu, my wrist sure does get warm...

---

### Post by Inxsible on 2007-11-17
> **ru7hl3ss said:**
> I have the dv9500t, and everything worked out of the box, except wireless and sound. I had some freezing running Compiz, but that is taken care of now. 

My only issue seems to be... heat. Idle around 29C for both CPU's in Vista, and 45C in Ubuntu, my wrist sure does get warm...
my dv9000t had the same problem with heat and my fan would run constantly. When i switched to 64 bit gutsy, its been great !!

suspend and hibernate worked out of the box too.
if you want you can install 64 bit version in another partition and see how that works out for you.

---

### Post by ru7hl3ss on 2007-11-17
> **Inxsible said:**
> my dv9000t had the same problem with heat and my fan would run constantly. When i switched to 64 bit gutsy, its been great !!

suspend and hibernate worked out of the box too.
if you want you can install 64 bit version in another partition and see how that works out for you.

Thanks mate, I'll need to try that out.

---

### Post by Inxsible on 2007-11-17
> **ru7hl3ss said:**
> Thanks mate, I'll need to try that out.Good Luck. hopefully it runs for you as quietly as it does for me and without heating up :)

---

### Post by fourscore on 2007-11-18
I have  a HP nx6110 and am dualbooting  with XPHome and Gutsy.   The WiFi (Broadcom ) and the  DialupModem work fine on Gutsy after installing the restricted drivers.   I had installed Fiesty earlier and this too worked fine (after lot of tweaking to get the wifi and modem to run).

One observation - Prior to installing linux,   while  checking for updated drivers (for windows)  from the HP siite, I noticed a   BIOS update for this notebook model.  The revision history mentioned " Corrects installation issue with SuSE Linux".      I did go ahead and install the BIOS update , reason being,  if it helps  SuSE linux then it could help other Linux.   Maybe this helped  in someway.

---

### Post by shuttleworthwannabe on 2007-11-18
I have a HP Compaq Bussiness notebook nw8240 with a ATI firegl card. everything works like a charm including full 3d rendering and compiz (just that it is heats up faster than without compiz). There are issues with this model that have not been rectified since Dapper release (kernel xxx.20.x); It has brokent the acpi to suspend or hibernate; and also does not allow to reboot (only shutdown works). Breezy was just fine.

Another problem is the WIFI LED light does not come on even when the WIFI card is working well and able to send and receive signals.

Besides this all else is sweet as heaven.

S

---

### Post by RH9R on 2007-11-19
Fourscore - That is another thing I noticed on the little F500 amd/compaq. On startup - there is a brief msg about 'bios' error. I checked the HP site, ( I believe the Compaq site redirects there), but I couldn't find anything on it. Perhaps some more searching. 
 
It makes sense that the various models have different levels of compatibility, but I've not seen so many surrounding one or two brands like this in Dapper or Feisty. 
 
I'm hoping the development process will be more kind in testing the Compaq/HP worlds for Hardy. With Feisty still stable & working (sleep doesn't), I'm a happy camper & grateful for the coders & engineers at canonical & the user base.

---

### Post by adi82 on 2007-11-19
i have HP 510 and everything works.
i didn't test at all my wireless but it seams to work because when i make search i get a lot of networks.

---

