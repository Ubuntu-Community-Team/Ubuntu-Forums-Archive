---
title: "Looking for a Linux distro for an old laptop"
date: 2012-02-14
forum: Any Other OS
---

### Post by tech291083 on 2012-02-14
Hi Friends,
 
I have an old Toshiba laptop model no - L10 - 273 purchased in 2005, which still works fine. It has the following specs. 
 
 
[http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=106454&DISC_MODEL=1&service=UK](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=106454&DISC_MODEL=1&service=UK)
 
Part Number : PSL17E-009008AV
 
- Intel® Celeron® M processor 360
- Windows® XP Home Edition
- 40 GB Hard Disk Drive
- 256 MB DDR RAM
- 15 " TFT colour display
- DVD-SuperMultiDL
 
 
I have always used ths laptop as a dual boot system with Windows XP Home (which came pre-installed) and various versions of 32 bit Fedora namely Fedora 5/6/7/8/9 without any problems. Now the latest 32 bit Fedora 16 requires more RAM and thus I am now looking for a Linux distro, which has almost all the latest features like other distros, but still compatible with my laptop which has only 256 MB of DDR RAM as mentioned above. I still want to dual boot this distro with Windows XP Home. What should I do now? Which distro to download? Thanks.

---

### Post by dagroves on 2012-02-14
I would recommend something like CrunchBang or even Elementary OS which I run on a Pentium 4, 20GB HDD, and 756MB or RAM. It runs great. CrunchBang would probably be better though. CrunchBang is based off of Debian and Elementary is based off Ubuntu which in turn is based off of Debian. Good luck!

---

### Post by papibe on 2012-02-14
Within the Ubuntu family, I would recommend taking a look at [Lubuntu]("http://lubuntu.net/").

Regards.

---

### Post by dagroves on 2012-02-14
Also if you want to stay Fedora based you can try out Fuduntu, it is a mix of Ubuntu and Fedora but aimed at netbooks and older PC's.

---

### Post by tech291083 on 2012-02-14
> **dagroves said:**
>  aimed at netbooks and older PC's.
 
 
This is what my exact need is. I am looking for a distros which offers features, but still runs well on old pcs/laptops with minimum of hardware requirements such as RAM and hard disk space. Thanks.

---

### Post by dagroves on 2012-02-14
> **tech291083 said:**
> This is what my exact need is. I am looking for a distros which offers features, but still runs well on old pcs/laptops with minimum of hardware requirements such as RAM and hard disk space. Thanks.

Well I would definitely check out CrunchBang and Fuduntu then. Also check into Elementary, it really does run good on older hardware. Puppy Linux and SliTaz are good to, SliTaz is a little odd to get used to because their package management sucks. TinyCore is good if you want to build from scratch, and WattOS is great to. Just do some searching and find the ones that work best for your needs, all that I listed are good on older hardware.

---

### Post by KBD47 on 2012-02-14
Fuduntu ran slow on my netbook with a gig of ram. Might try Lubuntu, Mint LXDE, or Mint Debian Xfce.
KBD47

---

### Post by TheNosh on 2012-02-14
Puppy Linux. It's very light, and works with the ubuntu repositories.

---

### Post by ojdon on 2012-02-15
If you still want to stick with Fedora as a base. They have a LXDE spin. LXDE is a lightweight Desktop Enviroment. From my past experience of using the spin, I've noticed that on idle it uses around 90-110MB of RAM. 

Check it out here:

[http://spins.fedoraproject.org/lxde/](http://spins.fedoraproject.org/lxde/)

---

### Post by kurt18947 on 2012-02-15
From Lubuntu's Wiki:

**System Requirements**

 [FONT=Courier New]A Pentium II  or Celeron system with 128 MB of RAM is probably a bottom-line  configuration that may yield slow yet usable system with Lubuntu. It  should be possible to install and run Lubuntu with less memory, but the  result will likely not be suitable for practical use.  
[/FONT]
I have a 2002 vintage Thinkpad.  It had a 256 DIMM with room for another.  I was able to find another compatible used DIMM on Ebay for <$10 US.  It runs very well with Lubuntu.  Would adding more RAM be practical?  The tricky part can be finding new RAM in old chips.  Hence my buying a used DIMM.  I bought from a vendor that had a 7 days after receipt return policy.  I immediatly uninstalled the existing chip, installed the new chip and ran memtest86+ for a few hours.  After that passed, I reinstalled the original chip and ran memtest86+ for a few more hours.  So far so good.

Lubuntu & Firefox will use about 170 Mb. RAM, Lubuntu & Chromium a bit less.

---

### Post by mips on 2012-02-15
> **tech291083 said:**
> ... but still compatible with my laptop which has only 256 MB of DDR RAM as mentioned above.

Some advice, if you can get another 1GB SODIMM stick for that laptop things will run great on it. Look at second hand places or eBay so it's cheap. It's well worth spending some small $ on ram.

---

### Post by snowpine on 2012-02-15
+1 on a RAM upgrade. It's not really the distro that's the problem (most any distro will run with 256mb if you use a "lightweight" desktop environment) but the applications you run on top of that. For example right now I am using over 256mb just for Firefox alone. ;)

---

### Post by tech291083 on 2012-02-21
Thanks guys, you have given me so many options that I need to have a serious look at each of them. But great replies indeed. Cheers.

---

### Post by boydrice on 2012-02-21
> **tech291083 said:**
> Hi Friends,
 
I have an old Toshiba laptop model no - L10 - 273 purchased in 2005, which still works fine. It has the following specs. 
 
 
[http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=106454&DISC_MODEL=1&service=UK](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=106454&DISC_MODEL=1&service=UK)
 
Part Number : PSL17E-009008AV
 
- Intel® Celeron® M processor 360
- Windows® XP Home Edition
- 40 GB Hard Disk Drive
- 256 MB DDR RAM
- 15 " TFT colour display
- DVD-SuperMultiDL
 
 
I have always used ths laptop as a dual boot system with Windows XP Home (which came pre-installed) and various versions of 32 bit Fedora namely Fedora 5/6/7/8/9 without any problems. Now the latest 32 bit Fedora 16 requires more RAM and thus I am now looking for a Linux distro, which has almost all the latest features like other distros, but still compatible with my laptop which has only 256 MB of DDR RAM as mentioned above. I still want to dual boot this distro with Windows XP Home. What should I do now? Which distro to download? Thanks.

If you want to stick with Fedora just use Xfce, LXDE, or the window manager of your choice.  I run Fedora 16 with Fluxbox and it doesn't use much ram.

---

### Post by samalex on 2012-02-24
Heh when you said old laptop I was thinking like a 286 or 386...  :) I personally have an old 8088 laptop I'd LOVE to get some form of Linux running on, but 8088 support dropped from the kernel years ago.

---

### Post by drawkcab on 2012-02-24
I would upgrade the RAM and then either 1.) run a lighter desktop on Fedora like xfce or lxde (available as spins I think) or 2.) look into Linux Mint Debian Edition which is fully featured and incredibly snappy.

---

### Post by mips on 2012-02-25
> **samalex said:**
> Heh when you said old laptop I was thinking like a 286 or 386...  :) I personally have an old 8088 laptop I'd LOVE to get some form of Linux running on, but 8088 support dropped from the kernel years ago.

How much RAM do you have? I'm assuming 640KB?

Try Minix 2.0.2 as it's the last version that could run in 640KB. Later versions have higher requirements.

Should be able to find it here somewhere [http://minix1.woodhull.com/hints.html](http://minix1.woodhull.com/hints.html)

---

### Post by scrub jay on 2012-02-25
I use Xubuntu 11.10 on an eMachines eM250 netbook with 1GB of ram and it runs decently. I would throw my hat with Lubuntu for with the amount of ram you have installed.

---

### Post by kyrealtor on 2012-02-27
> **ojdon said:**
> If you still want to stick with Fedora as a base. They have a LXDE spin. LXDE is a lightweight Desktop Enviroment. From my past experience of using the spin, I've noticed that on idle it uses around 90-110MB of RAM. 
 
Check it out here:
 
[http://spins.fedoraproject.org/lxde/](http://spins.fedoraproject.org/lxde/)
 
I think the Fedora Live CDs require 640 MB for Fedora 15 LXDE and 512 MB for Fedora 16 LXDE, so you might need to try another RPM based distribution.
If you are willing to try a distro with Debian based packages, Lubuntu and Xubuntu worked fine on my 256 MB P3 machine. After install, you can use straight LXDE or XFCE desktops which use a bit less memory than the lubuntu and xubuntu desktops.

---

### Post by tech291083 on 2012-06-26
Dear friends,

First of all sorry for being away for so long. 

You have given me so many options. Thanks for that. I have done some thinking on this issue and I think I need that old Toshiba laptop of mine as an experimental system ie to try and learn new distros/packages etc.


Now I have used Ubuntu and Fedora both in the recent past and I love both of them equally to tell you the truth. So I would go for a Ubuntu based or Fedora based distro which takes low RAM etc. Now as you have suggested earlier that Lubuntu and Fedora spins with LXDE or Xfce are good options. So I will download the latest versions of both ASAP. My net is a bit slow will take a few days. But I have a query.

Will I be able to install all the packages after installing either of them ie Fedora (LXDE/Xfce) or Lubuntu just like their more memory hungry counterparts namely Ubuntu 12.04 LTS and Fedora 16/17 with Gnome? I can't find another RAM stick so I will have to stick with 512 DDR RAM for the time being. Will I be able to use my laptop as a server and do all the necessary stuff. I understand that some apps/packages use more RAM, but still most of the packages should be happy with 512 MB of DDR RAM. Am I right here?

Thanks.

---

### Post by Dlambert on 2012-06-26
> **thenosh said:**
> puppy linux. It's very light, and works with the ubuntu repositories.

+1

---

### Post by BBQdave on 2012-06-27
> **tech291083 said:**
> Will I be able to install all the packages after installing either of them ie Fedora (LXDE/Xfce) or Lubuntu just like their more memory hungry counterparts namely Ubuntu 12.04 LTS and Fedora 16/17 with Gnome? I can't find another RAM stick so I will have to stick with 512 DDR RAM for the time being.

I have F16 (32-bit) Xfce on a Dell Inspiron 1100 (1GHz Celeron and 1 gig of ram). It runs great. If you can get to 1 gig of ram, that will help you a lot.

F16 live cd requires 756 Mb of ram to install (Gnome, Xfce, or LXDE).

Unless you want to work out of a CLI, for graphics - you need more ram :)

---

### Post by Dlambert on 2012-06-27
> **BBQdave said:**
> I have F16 (32-bit) Xfce on a Dell Inspiron 1100 (1GHz Celeron and 1 gig of ram). It runs great. If you can get to 1 gig of ram, that will help you a lot.

F16 live cd requires 756 Mb of ram to install (Gnome, Xfce, or LXDE).

Unless you want to work out of a CLI, for graphics - you need more ram :)

ANd why not use F17? :)

---

### Post by LemursDontExist on 2012-06-27
> **tech291083 said:**
> Will I be able to install all the packages after installing either of them ie Fedora (LXDE/Xfce) or Lubuntu just like their more memory hungry counterparts namely Ubuntu 12.04 LTS and Fedora 16/17 with Gnome? I can't find another RAM stick so I will have to stick with 512 DDR RAM for the time being. Will I be able to use my laptop as a server and do all the necessary stuff. I understand that some apps/packages use more RAM, but still most of the packages should be happy with 512 MB of DDR RAM. Am I right here?

Thanks.

With Lubuntu, the answer is a definite yes.  I'm running it on my old laptop and the repos are well maintained and populated with all the packages.  

Generally installing more programs shouldn't use any extra ram unless they in the background.  Most programs don't run unless you explicitly tell them to, and you can use
```
ps -e
``` 
from a terminal to get a list of running processes, which should help you keep track of what's using ram.

512MB is tight, but should be manageable as long as you don't want to do things like run a webbrowser and several other programs at the same time.

---

### Post by tech291083 on 2012-06-27
> **LemursDontExist said:**
> With Lubuntu, the answer is a definite yes.


Generally installing more programs shouldn't use any extra ram unless they in the background.  Most programs don't run unless you explicitly tell them to, and you can use
```
ps -e
```from a terminal to get a list of running processes, which should help you keep track of what's using ram.

512MB is tight, but should be manageable as long as you don't want to do things like run a web browser and several other programs at the same time.

Yes, you have understood my situation very well here. I simply can't upgrade from my total RAM which happens to be 512 DDR. Then I will start downloading it ASAP. Thanks a lot.

---

### Post by BBQdave on 2012-06-28
> **Dlambert said:**
> ANd why not use F17? :)

F17 was buggy for me. F16 (32-bit and 64-bit) Xfce is rock solid!

I would highly recommend F16 Xfce-4.8, and then upgrade to F18 Xfce-4.10 when F16 reaches EOL.

**Rule of Thumb**: not sure exactly why, but the *even* releases of Fedora are more stable than the *odd* releases :D

---

### Post by Lemuriano on 2012-06-28
Debian netinstall with xfce will do the job like a champ.

Regards.

Also a netinstall of Trisquel with xfce which is base in Ubuntu will be nice and fast. Or Trisquel-mini that use as a DE LXDE will do the trick.

---

### Post by mojo risin on 2012-06-28
Lubuntu doesnt require a lot of ram :). I think you can even get an extra small version of it too at the download sites.

---

### Post by tech291083 on 2012-07-17
Dear Friends,

I have always loved Ubuntu and Fedora and used them both with great fun and ease. So I have decided to use both of them for this old laptop of mine. As mentioned earlier I can't upgrade the RAM to 1GB as rightly recommended by some of you earlier. So I will have to stick with 512 MB RAM for the time being. I have downloaded and tried to install Lubuntu 12.04 on this laptop, but I could not despite 4-5 tries. I still have not got the workaround. Please have a look at my thread dealing with this particular issue.

[http://ubuntuforums.org/showthread.php?t=2015525](http://ubuntuforums.org/showthread.php?t=2015525)

So I have to download the most compatible Fedora spin as recommended by a few members. But my RAM will stay only 512 MB and I am not sure as to which one I should download from this page, which can run well on 512MB RAM. 

[http://fedoraproject.org/en/get-fedora-options#desktops](http://fedoraproject.org/en/get-fedora-options#desktops)

Which one I should download and install? Please help me here. I am still not able to find out the exact system requirements for all the 4 spins listed on this page ie KDE, LXDE, Xfce. I hope that I will be able to install all the regular packages after install the spin and be able to use the following packages.

IDEs for C, C++, Java, PHP, Perl, Python programming
Apache
MySQL

Thanks.

---

### Post by oldrocker99 on 2012-07-17
I'm a little surprised:confused: not to have seen Peppermint, which is built off LXDE\\:D/ and is VERY light on disc space, using Google Docs, etc. as LibreOffice replacements. It's nice & fast on my rescued-from-the-trash Acer 15xx laptop which has 3.8 GB of RAM, a 320 GB hard drive (salvaged from another laptop that died) and is doing a great job, even though it has the dreaded AMD X1200 video[-X. As did the dead laptop I also have:sad:.

I know Peppermint, which uses the Ubuntu repos, has their own LTS version coming out in a week or so8-). Just sayin':D

---

### Post by tech291083 on 2012-07-24
Hi,

At last, I have installed Lubuntu 12.04 and Fedora 17 LXDE spin one by one as the only distro on the laptop and they both worked well. Now I am going to use Fedora for some days to come and see how it goes and then I will try Lubuntu. Thanks a lot guys.

---

