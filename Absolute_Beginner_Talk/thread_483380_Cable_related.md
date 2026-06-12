---
title: "Cable related"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by V1ru586 on 2007-06-24
Hello, i just finished installing ubuntu into my second HD (80Gb) now i wanna connect my Windows Hd do i can dual boot but what i notice is that the cable that connects the HD(gray one) doesn't have enough extension to connect two HDs, can anybody tell me where can i find the extension? and am not talking about the power cable ... thnx!!

---

### Post by HotShotDJ on 2007-06-24
Which image looks like the type of cable you have?

---

### Post by V1ru586 on 2007-06-24
this one [http://ubuntuforums.org/attachment.php?attachmentid=36358&d=1182721882](http://ubuntuforums.org/attachment.php?attachmentid=36358&d=1182721882)

---

### Post by HotShotDJ on 2007-06-24
Ok.  If the cable provided with your system only has a plug for one hard drive, you'll need to purchase a new EIDE cable for two hard drives.  It is inexpensive and usually available at places like compUSA, Best Buy, NewEgg, etc.  Once you have the proper cable, you'll need to check the manuals for your hard drives and make sure that the one that you want to be the "first" hard drive is jumpered as "Master" and the "second" drive is jumpered as "Slave."  I don't recommend using "cable select."  Each manufacturer does this differently, so you'll have to do some research before connecting the two drives.  Once everything is configured and connected correctly, your system should be very happy.

You MAY run into a problem as far as the bootloader, called GRUB.  Since you installed Ubuntu while the hard drive was connected as the first drive, it is likely that Ubuntu set up GRUB on the Master Boot Record (MBR) of that drive.  You might have to fix that after you get your hardware sorted.  If that is the case, start a new thread on how to reconfigure GRUB.  But you don't need to cross that bridge until you get to it. :)

---

### Post by h0ax on 2007-06-24
Just as HotShotDJ said - here's a couple
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812105901](http://www.newegg.com/Product/Product.aspx?Item=N82E16812105901) rounded
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812200039](http://www.newegg.com/Product/Product.aspx?Item=N82E16812200039) ribbon

You're on the way!

---

### Post by V1ru586 on 2007-06-25
okay...heres my problem, the EIDE cable that is provided with my system has  connections which are used by 1)DVD-Rom 2)DVD-burner..now what i want is a EIDE cable  that has enough connections for my HDs and DVDrom and DVD burner...it seems the ones u guys are providing only has two which is the same as the one i have...thanks again!

---

### Post by kspn on 2007-06-25
An IDE cable has a maximum limitation of only 2 devices on it.

It should have 3 plugs, 
1) Main Board
2&3) Device (CD, DVD, Hard Drive, ect)

---

### Post by V1ru586 on 2007-06-25
soo in other words i cannot connect my two Hd CD=Rom ans DVD Rom?

---

### Post by kspn on 2007-06-25
No, unfortunately you cannot connect that many devices onto a single cable.

---

### Post by HotShotDJ on 2007-06-25
If I understand you correctly, you currently have one hard drive on the primary IDE channel, and your DVD-ROM  and your DVD burner on the secondary IDE channel.  Is there a reason why you can't configure the second hard drive as a slave on your primary IDE channel?  Did I miss a device?

---

### Post by V1ru586 on 2007-06-25
okay i guess it's my fault for not explaining myself appropriately...What i wanna do is get an extension for the cable so i can connect more than 1 Hd since my current cable only connect three devices which are my Primary HD, DVD-Rom  and CD-Rom, what i want is an extension for the cable so i can connect the secondary HD with Ubuntu on it...now if i want to connect the seonc HD(ubuntu) mi will have to disconnect either my DVD-Rom or CD-Rom which i dont wanna do...hope it helps

---

### Post by HotShotDJ on 2007-06-26
> **V1ru586 said:**
> since my current cable only connect three devices which are my Primary HD, DVD-Rom  and CD-RomUnfortunately, I'm unable to help you.  I've never heard of an IDE cable that can connect more than two devices, never mind 3 or 4.  The only way I know of to do what you want is to connect two devices on one IDE bus and two devices on the second IDE bus.

---

### Post by wink on 2007-06-26
You should have two IDE-type connectors on your motherboard, each of them can handle two devices. This makes for a total of four, like 2 HDs on one cable and the CD/DVD drives on the other. 

If you are saying that your second cable has only two connectors (motherboard and hard drive) - which is rare but not entirely unheard of - you'll definitely have to buy a new one as HotShotDJ already suggested.

---

