---
title: "MacBook Pro late 2011 booting to GNU Grub after Ubuntu re-install"
date: 2018-07-12
forum: Apple Hardware Users
---

### Post by nofrills2 on 2018-07-12
Hi there,

I'm a noob and have recently tried re-installing Ubuntu 18.04 on my MacBook after experiencing wi-fi card problems. I was installing Ubuntu on its own without any sort of dual-boot option. Now whenever I try to boot the machine I get the GNU grub menu. 

I can boot from USB, and have tried the boot-repair program. The program returns and error and suggested I send an output to an email address for further action. I did so about a week ago and have had no reply so far....

I really need my laptop back and running, so I'm looking for further help to get this problem fixed. I've tried searching the forums and have tried a few things with no luck so far.

Thanks in advance for any help you can offer!

---

### Post by kevin160 on 2018-07-12
Getting a grub menu isn't a problem.  What options is it giving you?   

Installing Ubuntu 18.04 alone should be very simple on that laptop, especially if you are simply wiping the drive and installing fresh.   You won't need rEFInd or anything like that.  Make sure you are installing in EFI mode, not legacy (aka "BIOS" or "Boot Camp") mode.  

What happens when you hold OPT while booting?  Does a PRAM reset (OPT-CMD-P-R until it chimes twice) change anything?  

If not, we'll need more details.  What error messages are you getting?  What is the exact model of mbp is it?  13" 15" or 17"?  

As for wifi, I think your laptop has the same Broadcom chip as my 2012 mini.  You have two driver choices.  Make sure you don't mix the two drivers:  

Installing the firmware-b43-installer and b43-fwcutter packages will get you 2.4 GHz and the ability to create an Access Point.
Installing the bcmwl-kernel-source package will get you 2.4 and 5 GHz but you can't create an Access Point.

---

### Post by nofrills2 on 2018-07-13
Hi Kevin,

I tried re-installing Ubuntu again (third time), and it has solved the problem (the boot issue that is). As for the wifi issue, I'm currently working on a solution here:

[https://ubuntuforums.org/showthread.php?t=2395758](https://ubuntuforums.org/showthread.php?t=2395758)

If you could contribute any advise that would be great!

Thanks for your help - Phill.

---

