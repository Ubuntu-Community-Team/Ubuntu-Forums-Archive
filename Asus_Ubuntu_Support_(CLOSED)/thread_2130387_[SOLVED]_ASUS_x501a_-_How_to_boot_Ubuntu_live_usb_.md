---
title: "[SOLVED] ASUS x501a - How to boot Ubuntu live usb stick"
date: 2013-03-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by JimS on 2013-03-29
...
I bought an ASUS x501a laptop in March 2013.
It has no optical drive.
It has American Megatrends bios.
It has Windoz 8.
I want Linux.
I have a Kingston DataTraverler usb stick.
I tried to get the bios to recognize usb hdd (usb stick) - nogo.

A BestBuy guy showed me what to do.
And I pass this info on to you.

Directions:
Make a bootable usb stick.  Mine has Ubuntu 12.10.
Insert your bootable usb stick into PC.
Log into Windoz 8.
Select the following:
START
Settings
General
On the right side I scroll down to Advanced startup and select Restart now.
(The following may differ if you are using a different PC brand or model.)
Use a device - Use a USB drive, network connection, or Windows recovery DVD.
Use a device, UEFI: Kingston DataTraverler 109PMAP

GNU GRUB appears with 4 selections.
1. Try Ubuntu without installing.
2. Install Ubuntu
3. OEM install (for manufacturers)
4. Check disc for defects
I selected the first one
and it WORKED. 

This is a bit awkward and has to be done each time.
I keep these directions in the cloud where I can get to them easily.
If you have a better, quicker way, please let me know.

If you are going to install Ubuntu, FIRST set up your partitions using Windoz. 
 Swap and /
then follow my above directions and install into /.

Give Windoz the boot.
...

---

### Post by oldfred on 2013-03-29
Do not create partitions with Windows, it may convert to dynamic which does not work with Linux.
But do use Windows to shrink the Windows install to make unallocated space for Ubuntu to install into.

Was this what you go thru, looks very complex.
 Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

But you should be able to directly get to UEFI/BIOS with a key when first booting.
      
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by JimS on 2013-03-29
...
Oldfred
Do not create partitions with Windows, it may convert to dynamic which does not work with Linux.
But do use Windows to shrink the Windows install to make unallocated space for Ubuntu to install into.

JimS (very old Jim)
Yes, you are right.  Shrink w/ win8 and make partitions w/ Ubuntu. 
My goal:  Dual boot win8 and Ubuntu as shown in YouTube video
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)
My message here was about how I accomplished getting my ASUS
laptop to boot a usb stick.  I haven't gone any further as yet.

Oldfred
Was this what you go thru, looks very complex.
Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

JimS
In her video she starts as I do, but when it is time
to Choose an Option she selects Troubleshoot while
I select Use a Device.
And from there I can reboot and run the live usb stick.
I wish had seen her video earlier.

Oldfred
But you should be able to directly get to UEFI/BIOS with a key when first booting.

JimS
I can go directly, but I've not been able to select usb hdd.
Usb hdd is not shown which is very curious since I find it using win8.
I could go directly into my old laptop's bios and change boot order and
then was able to boot from usb stick.

Oldfred
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/...ows-to-go.aspx](http://social.technet.microsoft.com/...ows-to-go.aspx)

JimS
For my ASUS there is a bios utility key but no Boot Menu key.
As I wrote above I couldn't find how to enable usb hdd boot from within the bios.
I think it is disabled and the enabler is hidden.
Somehow win8 finds it.

I'll mark this SOLVED, since it was for info only.

Thanks for your reply and keep booting up.

JimS
...

---

