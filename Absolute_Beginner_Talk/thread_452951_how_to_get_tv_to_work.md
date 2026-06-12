---
title: "how to get tv to work"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by theenglishmidget on 2007-05-23
Hi i have an old ATI All in wonder graphics card with a tv input. in windows i can watch tv but i cant figure out how to in linux. 
Thanks for your help.

---

### Post by chamberlain2006 on 2007-05-23
First, what is the model of your card. and second, what is the output of "lspci"?  (You have to go to Applications>Accessories>Terminal and type in lspci!)

---

### Post by jiminycricket on 2007-05-23
Hello,
ATI all in wonder cards are really bad tv tuners (software based as well, not hardware based).  You likely won't be able to get it to work in GNU/Linux.  Mine was an ATI All in Wonder (radeon 7200).

I have a Hauppauge PVR 150 that worked out of the box, on the other hand.  Much better in Windows, too.

---

### Post by theenglishmidget on 2007-05-23
i have an ati radeon all in wonder 128 pro or something along those lines. its old, i can tell you that.

00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thanks for your help.

---

