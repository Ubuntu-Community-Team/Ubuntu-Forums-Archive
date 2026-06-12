---
title: "MacBook Air vs Grub and Windows - Cannot boot up Windows"
date: 2021-10-12
forum: Apple Hardware Users
---

### Post by ormopl on 2021-10-12
Hi, 

Ive just wiped all of Apple stuff out of my Macbook Air Mid2012 for private purposes. 

What i have done, was to install clean installation of Windows. 
Then i installed ubuntu along with windows on separate partition. 

Under macos 'bootloader' i can see only "EFI BOOT". After clicking it, ususal GRUB is being loaded. 
I can freely run ubuntu without any issues, but after choosing Windows two things take place:

1. Sometimes only black screen is displayed, no reaction on anything
2. Sometimes, after choosing windows in GRUB, it gets back to GRUB without loading anything. 

Windows created EFI partition, where also ubuntu has its bootloader. 

Ive tried to use boot-repair tool, but with no luck.

Any help would be appreciated. Thank you

---

### Post by yancek on 2021-10-12
If you have the boot repair software and are unfamiliar with Grub, you should run boot repair again and select the Create BootInfo Summary.  When it finishes, it will give you a link you can post here.  This is explained on the boot repair page and they also suggest this method as the first option for people who are unfamiliar with Grub.

If you have an EFI partition with both a microsoft directory and an ubuntu directory there with the efi files and have no problem booting Ubuntu EFI,  you might check the power settings in the Control Panel to make sure hibernation is off.  If you don resolve this problem, post the boot repair output.

---

### Post by slickymaster on 2021-10-12
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by ormopl on 2021-10-12
Thank you for reply. 

Please see attached link:

[https://paste.ubuntu.com/p/PwKWKv548h/](https://paste.ubuntu.com/p/PwKWKv548h/)

If youre unable to read it, let me know, i will paste it raw.

---

### Post by oldfred on 2021-10-12
Can you directly boot Windows from UEFI boot menu?
You still show rEFInd in UEFI entries, but not in ESP. Did you uninstall that?

Grub only boots working Windows and most common issue is that Windows fast start up is still on. Windows updates often turn it back on, so you may have to directly boot Windows from UEFI to turn it off after Windows updates.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by tea for one on 2021-10-12
If you have removed rEFInd, you can install it again from the Ubuntu universe repo.
```
sudo apt install refind
```
Alternatively, you can make a USB device, which can simply contain the rEFInd software.
USB Flash Drive Image File from [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)
Hopefully, it will find the Windows boot files.

---

### Post by ormopl on 2021-10-13
Thank you for all of the replies

For now i am not able to boot windows at all. 
After installing refind it is not available trough "option" button during boot up. Only Grub shows up. 
After choosing windows nothings happen.

---

### Post by tea for one on 2021-10-13
> **ormopl said:**
> After installing refind it is not available trough "option" button during boot up. Only Grub shows up

After you have booted into Ubuntu and, assuming that rEFInd was installed successfully, you can set it as default EFI boot option
```
refind-mkdefault
```
Here is the description of this instruction [http://manpages.ubuntu.com/manpages/focal/man8/refind-mkdefault.8.html](http://manpages.ubuntu.com/manpages/focal/man8/refind-mkdefault.8.html)

Did you try oldfred's suggestion in post 5? > Can you directly boot Windows from UEFI boot menu?
And using rEFInd as a USB boot device - did you experiment?

---

### Post by ormopl on 2021-10-13
Thank you guys for all of the replies.

So, 

ive tried to install refind from ubuntu, but it was not loaded into EFI at all. I was able to run only "EFI BOOT" option, which was about to run GRUB. 
After this i was about to mess a little bit with efibootmgr_gui, where i just checked the options, everything was there, including windows bootloader. 
I just removed the rest of refind, and tried to run refind from USB. I was able to boot it, it recognized all of efi images available on my computer, but after installation attempt nothings happened. Still only one option "EFI BOOT", no refind at all. 
What is more, refind was able to recognize Windows bootloader, but after this ive seen "No operating system" 

Still trying...

---

### Post by tea for one on 2021-10-14
When you first installed Windows, was it version 10?

Did you use Windows tools to create the free space for Ubuntu?

Did you run Windows chkdsk after creating free space?

---

### Post by ormopl on 2021-10-14
Yes, that was 10, thats correct, by windows tool i left free space for ubuntu. I didnt chkdsk

---

### Post by tea for one on 2021-10-14
> Can you directly boot Windows from UEFI boot menu?

You haven't yet replied to this suggestion from [COLOR="#0000FF"]oldfred[/COLOR] in post 5?

If it did not boot Windows 10, any error messages?

---

