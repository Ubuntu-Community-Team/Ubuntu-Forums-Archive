---
title: "Toshiba Satelite"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-11-17
After my friend saw me slaving over my old and quite near dead laptop, he sold me his old Satelite laptop.  I pu in my LiveCD and it loaded fine until it tried to load the desktop and froze on a blue fuzzy screen.

What made this happen and how can I fix this?  Is it a CD or possible architecture problem?

All the web sites said it was a pentium 4 so the Intel CD should work.

HELP?

---

### Post by Brautigam on 2007-11-17
ask your friend if he had problems b4

---

### Post by madmatrixz3000 on 2007-11-17
He was a simple windows user, and got a virus in windows.
Non hardware fatal, I'm able to completely load and use puppy and DSL

---

### Post by mellowd on 2007-11-17
Have you tried installing form the alternative cd? it might just be a config problem with x

---

### Post by daimaru on 2007-11-17
i have a toshiba satellite p100-239 and just got it working with gutsy. there were loads of problems so please post your system specs before i go into them.

---

### Post by overdrank on 2007-11-17
> **madmatrixz3000 said:**
> He was a simple windows user, and got a virus in windows.
Non hardware fatal, I'm able to completely load and use puppy and DSL

Hi just a suggestion, maybe check the cd for errors
 this link I think may help 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by madmatrixz3000 on 2007-11-17
no cd probs, I was able to install through safe graphics, but when I installed the nvidia driver, my screen freaked.  How do I disable this driver.

Once back in should I try a reinstall of the restricted driver, instead of restarting the system, I just restarted X (i'm an idiot)

---

### Post by overdrank on 2007-11-17
> **madmatrixz3000 said:**
> no cd probs, I was able to install through safe graphics, but when I installed the nvidia driver, my screen freaked.  How do I disable this driver.

Once back in should I try a reinstall of the restricted driver, instead of restarting the system, I just restarted X (i'm an idiot)

Just boot into recovery mode and reconfigure your xorg
 Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
```

---

### Post by madmatrixz3000 on 2007-11-17
I'll try that

---

### Post by daimaru on 2007-11-17
deleted by me cause bs; was referring to shutdown :)

---

### Post by madmatrixz3000 on 2007-11-17
Also, does anyone know if the touchpad shortcuts are supported in Ubuntu.  Or can I use the touchpad as a second screen for like a media ticker or something.

---

### Post by madmatrixz3000 on 2007-11-17
After doing this, I get a regular screen, but the same error occurs when I activate Beryl.

Does my card need a different restricted driver than the one that Gusty auto-installs?

---

### Post by overdrank on 2007-11-17
> **madmatrixz3000 said:**
> After doing this, I get a regular screen, but the same error occurs when I activate Beryl.

Does my card need a different restricted driver than the one that Gusty auto-installs?

Can you post the output of this command ```
cat /etc/X11/xorg.conf
```
and why use beryl  when there is compiz-fusion.

---

### Post by drewster1829 on 2007-11-17
> **overdrank said:**
> 
and why use beryl  when there is compiz-fusion.

I used beryl on my Toshiba Satellite laptop with 7.04, but after upgrading to 7.10, I switched to compiz-fusion, and the desktop cube doesn't work at all!  It also didn't work on my old Dell desktop after upgrading to 7.10 and switching to compiz-fusion.  They both use (crappy) Intel integrated graphics, and I was using the i810 drivers for them...I recently got an old Radeon 9200SE (slow edition...it's about as bad as the integrated graphics) to work in the Dell with the ati driver, but the desktop cube STILL doesn't work.

Also, I miss the cool 'slamming' the mouse into the to right corner of the desktop to initiate the Scale feature...does anyone know how to fix these things?  I really miss the Cube.  Thanks!

---

### Post by overdrank on 2007-11-18
> **drewster1829 said:**
> I used beryl on my Toshiba Satellite laptop with 7.04, but after upgrading to 7.10, I switched to compiz-fusion, and the desktop cube doesn't work at all!  It also didn't work on my old Dell desktop after upgrading to 7.10 and switching to compiz-fusion.  They both use (crappy) Intel integrated graphics, and I was using the i810 drivers for them...I recently got an old Radeon 9200SE (slow edition...it's about as bad as the integrated graphics) to work in the Dell with the ati driver, but the desktop cube STILL doesn't work.

Also, I miss the cool 'slamming' the mouse into the to right corner of the desktop to initiate the Scale feature...does anyone know how to fix these things?  I really miss the Cube.  Thanks!

That feature is located under the expo feature in the advance desktop settings.
I have a spare system with the intel chipset and it runs gutsy and CF just fine. My laptop also uses the intel but I use feisty and CF is great. :KS

---

### Post by drewster1829 on 2007-11-18
I must've been using the wrong key combo, 'cause the cube works now! :o

---

### Post by madmatrixz3000 on 2007-11-18
Some new questions one day into my new system.
First let me say thank you, as the earier code allowed me to enter X and then reconf to fix it with compiz.

1.  I plugged in an external moniter, yet I am completely lost on how to get it to work as an extention.  it is being seen as the primary (very bad for what I need)

2.  My touch pad scroll areas are not working how do I get those up and running.

---

### Post by madmatrixz3000 on 2007-11-18
Also, how can I switch my Fn and Windows keys?

The toshiba has the win key in the corner and the fn key in the win key's spot

---

