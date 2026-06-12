---
title: "[SOLVED] No sound in Hardy on imac20 aluminium"
date: 2008-06-16
forum: Apple Hardware Users
---

### Post by RRR-007 on 2008-06-16
Hi

 I recently installed hardy on my imac20" aluminium. After a great struggle that i successfully configured ndiswrapper, wireless keyboard and wireless mouse etc., from the info available on this forum. Now landed in a big trouble of getting sound working on imac. I cant hear any sound in speaker, i tried all the suggestions from this forum. options sda-hda-intel on alsa-base doesn't work for me. 

Also in the alsamixer gui, there is no option for speaker available in switches tab instead i have got IEC958 & IEC958 capture. I dont know what to do with this option. I installed the latest alsa-driver 1.0.16 but no hope... no sound in speaker but i can hear barely very very minimun sound in the headphone... can anyone help me to figure out the problem and get sound working on my machine..... also let me know where to enable speaker option in alsa-mixer  

](*,)

---

### Post by cyberdork33 on 2008-06-16
check the FAQ:
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

---

### Post by RRR-007 on 2008-06-17
cyberdork,

  I have visited this link (imac aluminium - sound patch) already but I am not sure whether it works for alsa-driver 1.0.16 or not. Mine is alsa-driver 1.0.16. Honestly that i didn't give a try when i saw the patch marked as alsa-1.0.15-imac.txt.

Is the same patch work for 1.0.16 in hardy? if so, I think i'll have to download 1.0.16 driver again and follow the instructions mentioned in that link.

I really appreciate you since I have seen many of your replies in this forum. Indeed I fixed many issues revolved around ubuntu-hardy from the day one I installed it on my machine based on your replies.

Its a great work !!!.... 

thanks a lot...

---

### Post by al-fred on 2008-06-17
[best free porn](http://absolutely.bedava250mb.com) 
[8mg avandia](http://abusing.bedava250mb.com) 
[accutane when will skin get dry](http://accutane.bedava250mb.com) 
[adalat non extended release](http://adalat.bedava250mb.com) 
[arizona lasix](http://arimidex.bedava250mb.com) 
[atrovent nebulizers](http://atrovent.bedava250mb.com) 
[aleve and blood pressure](http://alcoholics.bedava250mb.com) 
[allegra hotel in chicago](http://allegra.bedava250mb.com) 
[amitriptyline and cymbalta](http://amitriptyline.bedava250mb.com)

---

### Post by RRR-007 on 2008-06-22
I tried to apply the patch alsa-1.0.15-imac.txt to alsa-driver-1.0.16 and got the following error:

 sudo patch < alsa-1.0.15-imac.txt
patching file patch_realtek.c
Hunk #1 succeeded at 175 (offset 16 lines).
Hunk #2 succeeded at 5718 (offset 404 lines).
Hunk #3 succeeded at 5912 (offset 404 lines).
Hunk #4 succeeded at 6054 (offset 402 lines).
Hunk #5 succeeded at 6158 (offset 403 lines).
Hunk #6 FAILED at 6389.
1 out of 6 hunks FAILED -- saving rejects to file patch_realtek.c.rej

Also i ignored the above failure message and went on with the instructions,

 sudo mv -v /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/snd-hda-intel{,-ubuntu}.ko
mv: cannot stat `/lib/modules/2.6.24-18-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko': No such file or directory

The above error was due to the fact that I dont have snd-hda-intel folder under media :-(


somebody please help me !!!!!!!!!!!!!!!!!!!!!!!!!!!!...........................

---

### Post by Kimmik on 2008-06-22
I have an iMac 20" alu too. I had problem getting sound to work, I tried everything that was posted on the forums and wikis.
The solution was simple.
Don't mess around with installing alsastuff etc. Don't change anything from the default configuration! Just include 

options snd_hda_intel model=mbp3

at the end of alsa-base and options (in /etc/modprobe.d).
I don't know which one is right, but it works when you put it in both files (options and alsa-base).

Reboot and it should work.
If it doesn't work (probably because you have tried to use patches etc.), boot a different kernel.
You can do that in grub (when you startup the iMac).
Boot an older unchanged kernel or see if there's a new one available via update.

Or reinstall ubuntu completely.

If it still doesn't work, check if the speaker checkbox is checked.

---

### Post by RRR-007 on 2008-06-25
Yes, you are right. I messed up the alsa-base driver by installing patches, fixes e.t.c...,, 

So, I completely reinstalled ubuntu from CD, this time, I followed your suggestion of editing alsabase and options from modprobe.d folder.

First I tried with snd-hda-intel model=mbp3 ( i believe its not snd_hda_intel), sound quality was too low and there was no base sound capture. 

Then, I tried with snd-hda-intel model=imac24... now its rocking :guitar:   but not close to the sound when i run in Mac OS :-( I know its a high expectation from free OS .....

btw, your imac alu becomes extremely hot when you run ubuntu in it? 

Mine is almost to be melted...:confused: if i touch the top portion of my imac after running ubuntu for sometime, it is extremely hot to the extent of burning my fingers :-( ....

ok, i'll create a new thread for this issuee... thanks a lot for helping out to fix sound issues...

---

### Post by ninjapenguin on 2008-06-25
Thank you for this solution, I was soundless on ubuntu for a bit until i saw this forum.

---

