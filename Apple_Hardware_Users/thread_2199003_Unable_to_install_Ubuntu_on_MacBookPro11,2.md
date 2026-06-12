---
title: "Unable to install Ubuntu on MacBookPro11,2"
date: 2014-01-11
forum: Apple Hardware Users
---

### Post by tmsandeep on 2014-01-11
I am trying to dual boot my macbook pro with ubuntu 12.04.3.
I partitioned my HD into 5 -
1) Apple OSX
2) /Boot - 1GB
3) /home - 4GB
4) swap - 4GB
5) Home "/" - 30GB
I downloaded .iso and wrote it to USB(I know the procedure and it is proper)
Then I installed refit on my MAC.

Restarted machine and went to install Ubuntu option, Display went blank but once after connecting to external monitor am able to view the screen.
I selected all partitions and started installing, everything is going smooth but at last I see an error
[B][COLOR=#333333][FONT=UbuntuRegular]"the grub-efi-amd64-signed package failed to install into /target/. Without the GRUB bootloader the system will not load"

[/FONT][/COLOR][/B][COLOR=#333333][FONT=UbuntuRegular]Can anyone help me to fix this issue?[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][/FONT][/COLOR]

---

### Post by sffvba[e0rt on 2014-01-14
*Thread moved to **Apple Users**.*

Perhaps someone here can better assist with your query...

---

### Post by tmsandeep on 2014-01-18
Can anybody help me with this please.

---

### Post by zircon_34 on 2014-01-18
During the installation did you choose to install the GRUB boot loader to the /(linux root) partition? if not, I would try that.

---

### Post by tmsandeep on 2014-01-22
I saw the same thing regarding GRUB in www but while installing I was not able to find any option like that.
Can you please help me where I can find that option.

---

### Post by zircon_34 on 2014-01-22
If you check my pic for the partition table during install [here]("http://ubuntuforums.org/album.php?albumid=2575&attachmentid=249436"), you see at the bottom the option "device for boot loader installation". Do not choose the whole drive (not sda).
There you select you root partition for e.g. /dev/sda/sda4 depending on your partition table. hope that helps :)

---

### Post by dan47 on 2014-01-23
Hi there
I have a MacBookPro8,3 an no problem to boot from a burned DVD of ubuntu-13.10-desktop-amd64.iso.
Why are you trying with ubuntu 12.04.3 and from a live USB ?
I tried a live USB myself with the same ubuntu-13.10-desktop-amd64.iso file and using rEFIt and later on rEFInd unsuccefully.

Dan (FR)

---

### Post by tmsandeep on 2014-01-25
Hi Thanks for that am able to install and was able to boot using ubuntu :-)
But am facing one more hurdle, my display is not proper on my macbook but if I connect to monitor its looking good.
Is there any fix for this.
I am attaching screen shot

---

### Post by tmsandeep on 2014-01-25
Hi Dan thanks for your reply yeah now am able to install from live usb too on mac.
I think I have two more issues one is display not proper and another one is wifi is not bein enabled.
Have you faced this?

---

### Post by tmsandeep on 2014-01-25
Can anybody please help me with this? I installed Ubuntu on Mac but I face a weird issue its not being displayed properly on laptop display but with external monitor it is fine.

---

### Post by kris-pypen-i on 2014-01-26
I had the same ugly screen, see [my solution here]("http://ubuntuforums.org/showthread.php?t=2201723&p=12911075#post12911075")

---

