---
title: "Ubuntu 7.04 on macbook pro"
date: 2007-04-30
forum: Apple Intel Users
---

### Post by siddharthc on 2007-04-30
Hi, 

I have ubuntu 6.06 installed on my macbook pro (along with XP and OS X). I would like to install ubuntu 7.04. However, I have the following question: 
- Currently I have LILO as the bootloader for linux. Does 7.04 use grub as the bootloader ? 
- Does grub install on hd(0,X) and not hd(0,0) ? I don't want to overwrite rEFIt and not be able to boot into mac os X ;-) 

thanks,
-siddharth

---

### Post by ronocdh on 2007-04-30
> **siddharthc said:**
> Hi, 

I have ubuntu 6.06 installed on my macbook pro (along with XP and OS X). I would like to install ubuntu 7.04. However, I have the following question: 
- Currently I have LILO as the bootloader for linux. Does 7.04 use grub as the bootloader ? 
- Does grub install on hd(0,X) and not hd(0,0) ? I don't want to overwrite rEFIt and not be able to boot into mac os X ;-) 

thanks,
-siddharth
As you may recall, installing 6.06 and 6.10 meant using LILO or the silly (but simple!) kludge during installation documented [here]("https://help.ubuntu.com/community/MacBook"). 7.04 handles EFI installations much better; for instance, on my triple boot setup, a fresh install of Feisty placed GRUB info right on the MBR that I had for WinXP. Worked like magic!

Of course, if you like, you can still spend the additional time to set up LILO. It's just not worth it to me. ;)

---

### Post by siddharthc on 2007-04-30
Thanks for the reply. I would like to go with grub. I am a little confused by your reply: Quote "a fresh install of Feisty placed GRUB info right on the MBR that I had for WinXP. Worked like magic!"

I thought grub would install on the MBR that I have for Linux and I would use rEFIt to boot into OSX, XP and grub for Linux. Are you suggesting that grub installs on MBR that has XP so you use rEFIt to boot into OSX and grub for either Linux or XP ? 

-siddharth

---

### Post by ronocdh on 2007-04-30
> **siddharthc said:**
> Thanks for the reply. I would like to go with grub. I am a little confused by your reply: Quote "a fresh install of Feisty placed GRUB info right on the MBR that I had for WinXP. Worked like magic!"

I thought grub would install on the MBR that I have for Linux and I would use rEFIt to boot into OSX, XP and grub for Linux. Are you suggesting that grub installs on MBR that has XP so you use rEFIt to boot into OSX and grub for either Linux or XP ? 

-siddharth
Yes, I should have gone into more detail. You have accurately inferred the bulk of the issue, actually. The case for me is that on the rEFIt screen I have icons for OS X, Linux (Ubuntu), and WinXP (and a boot CD when applicable). 

Choosing the OS X icon boots OS X without a hitch. Choosing Linux takes me to the GRUB screen, where I must again choose either Ubuntu or WinXP (I personally edited my GRUB conf and set the timeout at 3 seconds or something, so I can choose once and be done with it). Choosing WinXP on the rEFIt menu takes me to the exact same GRUB screen! So essentially I have to choose WinXP twice.

Only catch is that my keyboard often doesn't respond on the GRUB screen. This means that on the rare occasion I wish to boot WinXP, I have to reboot several times until I can actually move the selection from Ubuntu down to WinXP on GRUB.

---

### Post by mustang on 2007-04-30
> **siddharthc said:**
> 
I thought grub would install on the MBR that I have for Linux and I would use rEFIt to boot into OSX, XP and grub for Linux. 
-siddharth

This statement is correct. BTW, do you go to UCI?

-manish

---

### Post by siddharthc on 2007-04-30
Thanks for the reply. I just have one more question [hopefully ;)]. Did you choose to install grub on MBR of XP partition. Wouldn't it be easier to install grub on the MBR of Linux partition ? or am I missing something here ? 

Manish: Yes, I do go to UCI. 

thanks,
-siddharth

---

### Post by ronocdh on 2007-04-30
> **siddharthc said:**
> Thanks for the reply. I just have one more question [hopefully ;)]. Did you choose to install grub on MBR of XP partition. Wouldn't it be easier to install grub on the MBR of Linux partition ? or am I missing something here ? 

Manish: Yes, I do go to UCI. 

thanks,
-siddharth
Feisty was much more aware of my other OSes and the MBR/GPT issue than previous releases. The Feisty installer found WinXP and asked about the MBR; I believe the confirmation or the "Yes, go ahead" option resulted in GRUB being installed on the WinXP MBR. I am not certain of this, but IMO it wouldn't affect boot time either way.

---

### Post by Ptero-4 on 2007-05-04
If I wanted to get a MacBook/MacBook Pro and install ubuntu+minix (no OSX or XP). Can I install GRUB to the MBR and have it run w/o having to use rEFIt first?

---

### Post by ronocdh on 2007-05-04
> **Ptero-4 said:**
> If I wanted to get a MacBook/MacBook Pro and install ubuntu+minix (no OSX or XP). Can I install GRUB to the MBR and have it run w/o having to use rEFIt first?
I think that this is possible, but because GRUB doesn't understand EFI, the Mac would boot up and be puzzled for a little bit before it checked the sector of the disk where the MBR would be. 

Benanzo is pretty pro on this. Check out his posts in [this thread]("http://ubuntuforums.org/showthread.php?t=420866&highlight=mbr+efi").

*Edit: also check out Benanzo's post [here]("http://ubuntuforums.org/showthread.php?t=431280").*

---

### Post by Ptero-4 on 2007-05-05
But that can be avoided by setting the startup disk manually, or not?

---

### Post by ronocdh on 2007-05-05
> **Ptero-4 said:**
> But that can be avoided by setting the startup disk manually, or not?
Benanzo? Where are ya, buddy? This is your thing!

---

