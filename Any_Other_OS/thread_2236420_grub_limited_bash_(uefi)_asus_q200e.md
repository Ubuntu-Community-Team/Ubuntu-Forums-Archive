---
title: "grub limited bash (uefi) asus q200e"
date: 2014-07-26
forum: Any Other OS
---

### Post by john124 on 2014-07-26
Ok, I've done a lot of searches and have tried almost everything and I'm about ready to give up. I am just installing Zorin OS 9 on my laptop and I keep ending up with the grub limited bash screen. I have a separate efi partition, and I have the secure boot turned off but still have issues. My Zorin install is on sda4, which comes up as hd0,gpt4 when I run ls. If I try to boot, it says the kernel is not loaded. I can load the live version from my usb stick I made with unetbootin. Something interesting is that the usb stick shows up with UEFI: in front of it in the bios boot order, where as my zorin install does not, which I'm not clear if that is indicative of anything. Any help would be appreciated.

Thanks,
John.

---

### Post by slooksterpsv on 2014-07-26
None of your operating systems are using EFI? Download boot-repair and just have it grab the information - DON'T RUN A REPAIR THIS MAY DAMAGE WHAT'S INSTALLED ALREADY!

Where do you install grub to?

---

### Post by john124 on 2014-07-26
Zorin is the only OS I have installed. I have grub installed on the efi partition (sda1). This is a fresh install, and I've tried formatting the whole disk and starting over, with the same results every time. I tried letting boot-repair run with efi selected and I get an error. If the error number would be of help I can run it again and post it up.

---

### Post by slooksterpsv on 2014-07-27
Usually it will give you a pastebin URL or a URL to post here on the forums so we can read the log results.

---

### Post by john124 on 2014-07-27
I ran boot-repair again and it had no errors this time. I did another fresh install with the same result. I would not be against installing without efi, but the boot screen in my bios won't recognize the HDD without an efi partition for some reason. I have tried turning on legacy bios option as well and have tried installing with a bios boot partion and it still won't recognize the HDD. Thanks for the help thus far, I may try installing windows 7 just to see if it will even work.

---

### Post by slooksterpsv on 2014-07-27
With EFI you have to make it legacy OS like you did, disable secure boot and fast boot. Some BIOSes have other options which you may need to enable or disable. What kind of a system is it? Also never received a link on here for the boot-repair information.

---

### Post by john124 on 2014-07-28
Ok, i tried another install without efi partition and in legacy mode. Bios still does not see the HDD in the boot menu. I put the live usb stick in and forced it to boot the HDD. At this point I was met with the busy box boot error. I ran boot-repair again and it said the boot of the PC is in EFI mode. I let it run anyway and did a purge and reinstall of grub, but it was still not seen by the bios. I have set everything up as you suggested in your previous post. My bios are American Megatrends "Aptio". Thanks again for the help.

---

### Post by john124 on 2014-07-28
Did a new efi install and ran boot-repair. This is the error message I got [http://paste2.org/DgVp0J4J](http://paste2.org/DgVp0J4J)

---

### Post by oldfred on 2014-07-28
Moved to otherOS since Zorin.

It says grub installed correctly.

>  Reinstall the GRUB of sda2 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0



I think Boot-Repair picks up some errors that are not critical. It was not updated to 14.04 and efi files names have changed.

Some systems only boot Windows in UEFI mode. They hard coded UEFI to look for Windows description in UEFI entry.

      >  BootOrder: 0000,0001,0002
Boot0001* UEFI: KingstonDataTraveler 2.0PMAP
Boot0002* UEFI: KingstonDataTraveler 2.0PMAP
Boot0000* zorin,BootCurrent: 0001Installation finished. No error reported.



   not sure if similar to other Asus models:
 Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

---

### Post by john124 on 2014-07-28
I went ahead and tried a standard Ubuntu 14.04 install, and low and behold it installed with no issue. So this seems to be an issue with Zorin OS 9. I have Zorin on my PC with no issue but it does not have UEFI, so perhaps they still have some bugs to work out in that area. I find it odd since I thought Zorin was a pretty direct port of Ubuntu with a more "Windows" desktop environment. Thanks for all the help, I'm going to stick with this for the time being.

---

### Post by john124 on 2014-07-29
I found some more information and I can now get Zorin to boot from the grub> prompt by typing "configfile (hd0,2)/boot/grub/grub.cfg". Any ideas on how to get this to boot correcty without having to type that each time? Thanks for any help.

---

### Post by oldfred on 2014-07-29
Someone posted that it should be in the grub.cfg in the efi partition to call the grub.cfg in the main install. Do you have a grub.cfg in /efi/zorin?

 configfile (hd0,gpt2)/boot/grub/grub.cfg

found that putting grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

---

### Post by john124 on 2014-07-29
Yes, there are actually 2 grub.cfg files. One is in /boot/grub on my root partition and the other is in EFI/zorin/ (on the efi partition, not the root partition). The cfg file on the efi partition is only 3 lines of code where as the one in the root partition is fairly lengthy. I went into vim and added the one line of code that works in the grub> prompt, but there was no change. I have also tried changing the cfg file to only have the one line of code, which again sends me to the grub> prompt on reboots.

---

### Post by oldfred on 2014-07-29
You would not edit the grub.cfg in /boot of your install. If you want to modify it you edit 40_custom or the settings in /etc/default/grub and then run sudo update-grub.

But the grub.cfg in your efi should be the configfile or something similar.

What was there? perhaps Zorin has a different or modified grub?

---

### Post by john124 on 2014-07-29
search.fs_uuid 797de168-fc0d-4196-a105-14e750c45c01 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


I'm going to try copying the other grub.cfg file over and see if that does anything. I have this file backed up so I'm not too worried.

:edit:
Well that didn't help either.

---

### Post by oldfred on 2014-07-29
One line configfile is essentially the same, but hard coded to one partition that must be boot drive hd0, and boot partition sda2 with gpt partitioning. If efi partition is on a different drive then the hd0 may also need changing.

But on your search line you have root hd0,gpt2 at the end & most search lines I have seen do not have that? Not sure if correct or not.

Normal grub now has a set root which it always had, but then they added the search by UUID which will override the set root so system can boot if drive order has changed as UUID almost never change.

---

### Post by john124 on 2014-07-30
Ok, I tried removing the root hd0 gpt2 from the search line, no change. currently the efi partition has the grub.cfg file, grubx64.efi MokManager.efi shimx64.efi on it an nothing else. Is this all that is needed? I have never had so many issues getting a system to boot until now (first efi install). Should I try reinstalling ubuntu and looking at the grub.cfg file that it used to see how it was done since it worked?

---

### Post by john124 on 2014-07-30
... ok... I installed ubuntu in a dual boot with Zorin. Now the ubuntu grub screen comes up where I can choose Zorin. If I do then it will load up just fine... so now I just need to figure out how to do this with only Zorin.

---

### Post by oldfred on 2014-07-30
Do you end up with two efi partitions, one ubuntu with its grub configfile pointing to the grub.cfg in Ubuntu and one Zorin with its configfile pointing to the grub.cfg in Zorin?
And Ubuntu's grub is using os-prober to find Zorin and directly boot it not thru UEFI. 
With Windows grub cannot directly boot it so it uses a chain load entry to go back to UEFI to load Windows own efi boot file.

If you want to see all the details post a link to the BootInfo report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But script do not include the grub.cfg in the efi partitions, so you should also post those.

---

