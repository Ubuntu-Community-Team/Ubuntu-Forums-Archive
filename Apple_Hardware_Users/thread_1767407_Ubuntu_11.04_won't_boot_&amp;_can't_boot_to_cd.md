---
title: "Ubuntu 11.04 won't boot &amp; can't boot to cd"
date: 2011-05-25
forum: Apple Hardware Users
---

### Post by konnichwakid on 2011-05-25
Ubuntu 11.04 won't boot & can't boot from cd. After installing ubuntu 11.04 and rebooting it never goes back into the OS. It just goes purple and then black with a fuzzy purple bar across the horizon. Now the whole computer is completely fubar'd and I can't even boot from CD. I can't access anything. 

I was trying to install the Mac OS that came with the computer and start over again, but the CD is stuck in there now and I can't boot from it or anything. I tried pulling ram and of course holding 'C' to boot from CD. 

What else can I do? This is a mac mini.

---

### Post by beringse on 2011-05-25
May be a video driver, I'm sure someone that's been there can give you some input. 
On your CD issue, if I run into a stuck one I power off the machine, and then hold the eject key down while powering back up.

---

### Post by thinktyler on 2011-05-25
To get the DVD from a Mac:
1) Reboot
2) Once you hear the Mac startup sound hold the option key.
3) From the partition menu you can then eject the DVD.

Did you burn the AMD64 version of Ubuntu? Did you burn it at 4x or below?

Can you boot and get to the main list where it says "install ubuntu" "boot from first hard disk"?
If you can, try hiting tab and add
"nomodeset" to the kernal line and hit enter.

Perhaps the video driver will work then. 

Good luck.

---

### Post by konnichwakid on 2011-05-26
> **thinktyler said:**
> To get the DVD from a Mac:
1) Reboot
2) Once you hear the Mac startup sound hold the option key.
3) From the partition menu you can then eject the DVD.

Did you burn the AMD64 version of Ubuntu? Did you burn it at 4x or below?

Can you boot and get to the main list where it says "install ubuntu" "boot from first hard disk"?
If you can, try hiting tab and add
"nomodeset" to the kernal line and hit enter.

Perhaps the video driver will work then. 

Good luck.

I will give it a shot and let you know how it goes. Thanks.

---

### Post by konnichwakid on 2011-05-26
> **thinktyler said:**
> To get the DVD from a Mac:
1) Reboot
2) Once you hear the Mac startup sound hold the option key.
3) From the partition menu you can then eject the DVD.

Did you burn the AMD64 version of Ubuntu? Did you burn it at 4x or below?

Can you boot and get to the main list where it says "install ubuntu" "boot from first hard disk"?
If you can, try hiting tab and add
"nomodeset" to the kernal line and hit enter.

Perhaps the video driver will work then. 

Good luck.

This worked. I typed "nomodeset xforcevesa" because that worked previously. However now after I reboot the newly installed Ubuntu, it boots into another road block. The screen ends up freezing on a black window with a fuzzy purple horizon. I am getting dizzy now. I was here once before.

---

### Post by parkerlab on 2011-06-27
I have the exact same problem. Did you find out the answer yet? Thanks

---

