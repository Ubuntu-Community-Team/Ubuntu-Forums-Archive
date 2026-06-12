---
title: "Dual boot email"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by James Lee on 2007-08-31
I have installed Feisty Ubuntu using Wubi on my Windows XP PC. I have now managed to get the Ubuntu system connected to the internet and have also installed Thunderbird for email. My email on the XP system also uses Thunderbird and I have to use that system for incoming attachments in Word which need further Word processing. However no incoming email is arriving at the Ubuntu Thunderbird site. Is it possible to achieve incoming email arriving at both the Ubuntu and XP sites? If so, can anyone advise me what I would need to do? 

I will be very grateful for any advice and my thanks in anticipation

James Lee.

---

### Post by mlentink on 2007-08-31
I don't currently use Thunderbird, but I remember you could share the datafiles. Get Linux-Thunderbird to use the datafiles in your windows partition, configure Linux-TBird exactly (i.e. same POP-server, same SMTP server etc.) as you did the Windows version and you should be all set.
At least that's what I would try. Perhaps a TBird-guru on the forum could give more specific instructions?

---

### Post by eph1973 on 2007-08-31
This might seem like a silly question, but did you configure your Thunderbird in your Linux partition the way it is on your XP partition?  You have to set up your POP and SMTP connections as well as any passwords, the actual address of your mail server, etc. to make your Thunderbird check for any incoming e-mail from your ISP (assuming that's where your e-mail comes from).  If you click along the top menu bar Edit>Account Settings... and make the information in your Linux partition match the information in your XP partition, you should be able to get/send e-mail using Thunderbird whichever way you boot.

---

### Post by wormser on 2007-08-31
I found this [guide]("http://ubuntuforums.org/showthread.php?t=203524") on nhow to share data files.  It is older Dapper instructions but it should get you on the right track.

Good Luck

---

### Post by mlentink on 2007-08-31
Thx Wormser! Seems I remembered correctly.

Please also note the set-up mentioned in the guide (separate FAT-partition) is no longer needed. Your NTFS drive can be accessed from out of Feisty directly. Which saves you a lot of trouble, I think.

---

### Post by James Lee on 2007-09-08
I'd like to thank you who replied to my plea for help and very much appreciate your kindness. I have followed up as best I was able and have some progress but also a major problem. The problem is that I am unable to exit Ubuntu in the usual manner with the options of shutting down, restarting etc.

The history was

1. I looked up the howto 469666 and followed the instructions to instal ntfs-config which I called WinXP and duly found a 'File" FileSystem/media/WinXP.

2. It was when I tried to exit the system after doing this That I ran into the closing down problem.

3. The symptoms are that I get a screen with amongst others the following statements:

     Deactivating Swap     [fail]

followed later by

---

### Post by James Lee on 2007-09-08
I'd like to thank you who replied to my plea for help and very much appreciate your kindness. I have followed up as best I was able and have some progress but also a major problem. The problem is that I am unable to exit Ubuntu in the usual manner with the options of shutting down, restarting etc.

The history was
1. I looked up the howto 469666 and followed the instructions to instal ntfs-config which I called WinXP and duly found a 'File" FileSystem/media/WinXP.
2. It was when I tried to exit the system after doing this That I ran into the closing down problem.
3. The symptoms are that I get a screen with amongst others the following statements:
     Deactivating Swap     [fail]
followed later by
     can't link lock file /etc/mtab Read only file system (use -n flag to override)    [fail]
and hanging up on
[  440.004000] buffer I/O error on device loop0 logical block 653312
I tried Ctl/Alt/Del and got a repeat of the Swap statement finally ending on 
/etc/ind.d/rc: 2: /etc/rc6.d/S99killntfs3g:input/output error
After this the only way I could find to get out was to power off.
It starts again OK in either Ubuntu or the dual boot WinXP.
Continued in next response, I seem to have run out of space!

---

### Post by James Lee on 2007-09-08
Continued

4.   I did notice that occasionally this would get me the Thunderbird incoming email arriving in Ubuntu (but not in WinXP as well). The mail would revert to the WinXP system but not on a basis that I could identify.
5.   I did go on and install the second part of the 469666 howto to instal Ext2IFS_1_10c.exe on XP              but with no change to my shutdown problem or having email repeate on both Ub untu and WinXP independent of which is in use at any particular time.

All rather a mouthful - anyone got any advice or ideas, my thanks in anticipation best regards

James Lee

---

