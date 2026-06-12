---
title: "Grub Do not Load Dual Boot"
date: 2014-06-19
forum: Any Other OS
---

### Post by nikhil55591 on 2014-06-19
I have Dual Boot Windows 8.1 and Ubuntu 13.10 .
When I shut down/restart the Ubuntu I get the the start screen but GRUB won`t load . If I Go to BIOS and then goto save changes and exit , without changing anything , GRUB would load . 
When I shut down/restart from Windows I am not even able to go BIOS , so I take the battery of the laptop out and then put it back again . Then again GRUB wouldn`t load , Then I go to BIOS and follow the same procedure again . 
Please HELP so that I am able to restart / shut down  laptop and turn it on normally .
PLEASE HELP .

---

### Post by ajgreeny on 2014-06-19
It sounds as if you might be a good candidate for boot repair (see my signature at the bottom).

Run that and report back here the link that it will give you so we can see your boot-info output.

---

### Post by nikhil55591 on 2014-06-19
I have done so , but its of no use .
[http://paste.ubuntu.com/7669279/](http://paste.ubuntu.com/7669279/)

---

### Post by nikhil55591 on 2014-06-19
Thanks for your reply
[http://paste.ubuntu.com/7669279/](http://paste.ubuntu.com/7669279/)

---

### Post by ajgreeny on 2014-06-19
I wonder if
```
=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

```
or ```
The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)
```
have any bearing on this problem.

The second suggests a possible answer, and for the first I am a bit baffled and can only suggest you try reinstalling grub from software-centre or synaptic

---

### Post by oldfred on 2014-06-19
The far from start of drive error was/is older systems and some BIOS/USB drivers with larger external drives.
Is BIOS set for AHCI not IDE nor RAID?

But Windows 8 has its always on hibernation which does not work with grub2. You must make sure that is turned off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by nikhil55591 on 2014-06-23
I have already turned off the fast startup .
Here is the new link [http://paste.ubuntu.com/7688867/](http://paste.ubuntu.com/7688867/)

---

### Post by oldfred on 2014-06-23
I do not see anything wrong?

Does system fully shutdown?  Are you shutting down normally not a forced REISUB?
Grub does say a parameter if system not shutdown, but then grub menu should always appear.

Try a REIFSUB instead of clicking on shut down.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Otherwise I might think it is something in BIOS? Are both system in BIOS boot mode, but you have UEFI on? Or someother setting. Windows 8 also can cause issues. You do not have EasyBCD do  you?

---

