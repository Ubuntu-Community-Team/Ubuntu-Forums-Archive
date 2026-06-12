---
title: "Wireless Security Problems for Newbie"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Guy Smiley on 2007-01-12
Well after 20 years of using computers most days I finally post my first notice into a forum.
A hardened XP user, used to cursing its idiosyncrasies, I have installed Ubuntu (three times now after several f**k ups on my part involving grub files and soundcards) over the last two days.
So this is day three in the Ubuntu house and I've got a problem.. 

I've just bought a new wireless router for ADSL connection, and Ubuntu, marvelous feat of programming that it is has detected it and I'm successfully on the net.

As soon as I try to introduce encryption of any kind (via router control panel) the connection 
to the internet is lost. The signal strength is still on full. I've been configuring it via the   
 'connection properties' dialogue box accessed by right clicking on the double screen icons in the top right of the screen, using both ascii and hexidecimal password for 64bit, 128 bit and WAP encryption but with the same net result for all of them.
It seems odd that the configuration box doesn't ask which type of encryption the password applies to ?

Anyway any help gratefully received. I notice that there are several other posts on various forums discussing 'full signal strength but no internet' ???:confused:

---

### Post by annda on 2007-01-12
sometimes it is difficult to configure WAP encryption for some cards. try WEP on your router.

and post the results, of course.

---

### Post by Guy Smiley on 2007-01-12
Hi Annda,
Sorted it. I had already tried WEP options but your post prompted me to have another go.
In the router it gives the option to either enter the hexidecimal numbers manually, or use a phrase to generate them. So i was typing in a password, and using this to generate the numbers, and then using this password in Ubuntu to try and gain access. This time round i entered the numbers manually in the router, and then again in Ubuntu.
Pretty stupid mistake huh ?
Thanks for your prompt feedback though
Bill

---

### Post by annda on 2007-01-12
congratulations!

and no mistakes are stupid if someone can learn from them - you or others. so posting back is important and please keep on doing that for the sake of us all. it helps a lot when searching old posts for solutions.

---

### Post by jas0 on 2007-01-12
Using WEP is a bad idea. You can safely implement WPA-PSK (using TKIP) on your wireless access point. 

After you do that install the following:

```
sudo apt-get install network-manager-gnome
sudo reboot
```

After you reboot, you will notice that you have a new icon on your task bar. Right click this icon and click on the name of your network and fill in your WPA key.

---

### Post by Guy Smiley on 2007-01-12
Thanks for the additonal information, I'll try that.
Why is using WEP stupid though ?
I've only got two computers in a residential street, so a really minimal security setting should do the job. I thought that WPA's only advantage over WEP was improved encryption ?

---

### Post by jas0 on 2007-01-12
When using WEP, it's safe to assume that you have no security. It can be easily cracked within 10-20 minutes. The worst scenarions I've heard about were about people using other peoples' wireless for file sharing and kiddie pornography.

The weakness of WEP is not as much its encryption as is its implementation. Both use RC4 (WEP uses PRNG + RC4) by the way.

Look at it this way--with WEP you eliminate 90% of the potential offenders and with WPA-PSK you eliminate 98%.

---

