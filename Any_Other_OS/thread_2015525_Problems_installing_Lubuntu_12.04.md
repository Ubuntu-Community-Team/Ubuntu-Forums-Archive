---
title: "Problems installing Lubuntu 12.04"
date: 2012-07-03
forum: Any Other OS
---

### Post by tech291083 on 2012-07-03
Dear Friends,

I have just downloaded Lubuntu and burned it to a CD. I want to install it on an old laptop. Here is a link to the my laptop model. It is 6+ years old. 


[http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=106454&DISC_MODEL=1&service=UK](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=106454&DISC_MODEL=1&service=UK)

Equium L10-273
Part Number : PSL17E-009008AV
Key Features
- Intel® Celeron® M processor 360
- Windows® XP Home Edition
- 40 GB Hard Disk Drive
- 256 MB DDR RAM
- 15 " TFT colour display
- DVD-SuperMultiDL

This laptop has 2 OS on it Windows XP Home and Fedora 5. So its a dual boot system. It works fine. A bit slow though. I inserted the Lubuntu 12.04 CD into the CD drive and restarted the laptop also changed the boot settings to boot from the CD, but for some reason it never really worked. So I booted into Win XP and inserted the CD afterwards. I opened the CD and got the screen with installtion options such as Full install and Demo. I chose that option and then I was greeted by another screen with 3 options if I remember correctly. I chose the one which was Help me to boot from CD. This took me to a process called Ubuntu CD Boot Helper. It went smoothly and I restarted the pc and there was Lubuntu alongside Win XP as an option to boot. I chose that and tried to boot into Lubuntu, but there was this Lubuntu screen which had small dots/sqares flickering one by one, but nothing really happened even after 20 mins or so. So I booted into Win XP and from Control Panel- Add/Remove uninstalled Lubuntu. 

I tried to install Lubuntu again using the same option ie - Help me to boot from CD. But this time it gave me some error which is displayed in the image attached to this post of mine.  

Now how do I install Lubuntu since the CD does not seem to be a bootable one. CD is new and not damaged at all. Thanks.

---

### Post by sudodus on 2012-07-03
> **tech291083 said:**
> ...
So I booted into Win XP and inserted the CD afterwards. I opened the CD and got the screen with installtion options such as Full install and Demo. I chose that option and then I was greeted by another screen with 3 options if I remember correctly. I chose the one which was Help me to boot from CD. This took me o a process called Ubuntu CD Boot Helper. It went smoothly and I restarted the pc and there was Lubuntu alongside Win XP as an option to boot. I chose that and tried to boot into Lubuntu, but there was this Lubuntu screen which had small dots/sqares flickering one by one, but nothing really happened even after 20 mins or so
...
You may have problems with the graphics or ACPI or something else, that might be fixed with a boot-option. See this link[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
Please try one of the boot-options. Start with ***nomodeset***

By the way, it would make it easier to help if you let us know what graphics chip/you have.

---

### Post by tech291083 on 2012-07-04
> **sudodus said:**
> You may have problems with the graphics or ACPI or something else, that might be fixed with a boot-option. See this link[[COLOR=red]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")
Please try one of the boot-options. Start with ***nomodeset***
 
 
Thanks a lot for the reply. It makes sense to me, but you have given a link to a page which has Ubuntu installation screenshots and I am looking for Lubuntu installation screenshots. Lubuntu installation is a bit different as I can tell that from what I have done so far with the CD. can you please also let me know as to how I can ser the nomodeset option before the actual installation of Lubuntu takes place? Thanks a lot.

---

### Post by sudodus on 2012-07-04
I think the basic installation is the same, so the text about boot options is relevant. I beta-tested Lubuntu 12.04 :-)

---

### Post by critin on 2012-07-09
> But this time it gave me some error 


Did you remove all evidence of the first install attempt as the error message stated?  You'll need to search for it all, it doesn't all delete just from the remove programs.

Check in the Programs for a folder.

---

### Post by tech291083 on 2012-07-10
> **critin said:**
> Did you remove all evidence of the first install attempt as the error message stated?  You'll need to search for it all, it doesn't all delete just from the remove programs.

Check in the Programs for a folder.

Yes, i have done all that you have mentioned. But all in vain.

Ok,

I did the instillation again. Kept Lubuntu alongside Win XP. Used the option - Help  me to boot from CD. All went smoothly with the graphical installation of Lubuntu. But now it appears that the 2nd stage of installation is yet to be completed. And it gives me these 5 options to do so, but even though I have chosed each of them one by one it simply does not boot or finish the 2nd stage. Here are the 5 options for booting into the 2nd stage of Lubuntu.

Normal mode
safe graphic mode
ACPI workarounds
verbose mode
demo mode.

Please help me go past this stage to finish the 2nd stage of installation. Thanks.

Fedora is no longer there on the hard drive, only Win XP and Lubuntu exist on different partitions. Thanks

---

### Post by Rodney9 on 2012-07-10
Safe Graphics looks pretty safe


Burn discs at the slowest speed you can.

Try a different brands.

Check MD5SUM for your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)



For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

