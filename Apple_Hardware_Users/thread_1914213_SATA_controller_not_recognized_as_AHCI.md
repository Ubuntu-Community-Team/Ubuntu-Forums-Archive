---
title: "SATA controller not recognized as AHCI"
date: 2012-01-23
forum: Apple Hardware Users
---

### Post by daehenoc on 2012-01-23
Hi all,

I have a Macbook Pro 15" from 2008 and I now have a Falcon II 64Gb SSD I would like to use in it :)  I currently have a 250Gb HDD in the Macbook.

I've been reading this wiki page on the Arch Linux site: [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Specifically the Mount Flags section, on Mac computers: [https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers](https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers)

I'm using the ubuntu-11.10-desktop-amd64+mac.iso for the installation, and following the instructions on the wiki page above, I see:
```
$ lspci -nn | grep -i sata
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 04)
```

I'd like to try setting the controller to AHCI by changing the grub boot options, but I have two problems:
[LIST=1]
[*]I can't find in the grub.cfg or /etc/default/grub where to enter the boot option, and
[*]Holding down the shift key when the Mac boots does not give me the grub boot menu.  I even attached a USB keyboard and that didn't work either.
[/LIST]

So, I need to read more about grub menu entry editing (unless someone can point me to a page which explains it well :p) and there's the problem of not being able to access the grub boot menu - is there config I can set to force the grub menu to appear on boot?

---

### Post by varunendra on 2012-01-25
The easier part first:

To make grub menu visible, boot into Ubuntu, and open **/etc/default/grub** file for editing by pressing Alt+F2, and entering the command:
```
gksu gedit /etc/default/grub
```Add a **# **before the line that says:
> GRUB_HIDDEN_TIMEOUT=0so that it now looks like:
> **# GRUB_HIDDEN_TIMEOUT=0**proofread, save and close. Then open a terminal and run:
```
sudo update-grub
```Now the other part:
> **daehenoc said:**
> I'd like to try setting the controller to AHCI by changing the grub boot options..
As far as I know, the kernel automatically picks it up IF AHCI is enabled in BIOS for the port in question. So make sure it is enabled there.

But since I am not familiar with macs, I may not be understanding your problem correctly. So if you do need to add a kernel-boot parameter (which I'm not aware of) to enable AHCI, you can add it to the GRUB_CMDLINE_LINUX_DEFAULT=... line in **/etc/default/grub** file (open it same as above). It usually looks like:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"Add your boot parameter in between the quotes, so that it looks like:
> GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash [COLOR=DarkRed]*<your_boot_parameter>*[/COLOR]**"**But I would recommend to try the boot parameter temporarily first to see its effects.

To do so, just make the grub menu visible first, then, selecting the default Ubuntu option in Grub menu:

[LIST]
[*]press 'E' to edit the kernel booting line.
[*]Bring down the cursor to the line that ends with ***"...quite splash"*** (the complete line would be in two or more lines. Just bring the cursor to the beginning of the line and press 'end' to add you boot-parameter at the end of the line).
[*]After typing the parameter, press **Ctrl+X** or **F10 **to boot.
[/LIST]
If the option seems to be doing what you are expecting from it, you can add it permanently by adding it to the /etc/default/grub file as suggested above.

Hope it helps.

---

### Post by daehenoc on 2012-01-26
> **varunendra said:**
> The easier part first:

To make grub menu visible, boot into Ubuntu, and open **/etc/default/grub** file for editing by pressing Alt+F2, and entering the command:
```
gksu gedit /etc/default/grub
```Add a **# **before the line that says:
so that it now looks like:
proofread, save and close. Then open a terminal and run:
```
sudo update-grub
```Thanks!  Done, however when the Mac boots up, I don't see the grub menu, I get a white screen, then a dark purple screen (maybe the grub menu is being displayed here but the Mac video card is not actually putting it on the LCD), then the Ubuntu boot screen and the computer boots Ubuntu.
> **varunendra said:**
> Now the other part:

As far as I know, the kernel automatically picks it up IF AHCI is enabled in BIOS for the port in question. So make sure it is enabled there.

But since I am not familiar with macs, I may not be understanding your problem correctly. So if you do need to add a kernel-boot parameter (which I'm not aware of) to enable AHCI, you can add it to the GRUB_CMDLINE_LINUX_DEFAULT=... line in **/etc/default/grub** file (open it same as above). It usually looks like:
Add your boot parameter in between the quotes, so that it looks like:
But I would recommend to try the boot parameter temporarily first to see its effects.

To do so, just make the grub menu visible first, then, selecting the default Ubuntu option in Grub menu:

[LIST]
[*]press 'E' to edit the kernel booting line.
[*]Bring down the cursor to the line that ends with ***"...quite splash"*** (the complete line would be in two or more lines. Just bring the cursor to the beginning of the line and press 'end' to add you boot-parameter at the end of the line).
[*]After typing the parameter, press **Ctrl+X** or **F10 **to boot.
[/LIST]
If the option seems to be doing what you are expecting from it, you can add it permanently by adding it to the /etc/default/grub file as suggested above.

Hope it helps.Your post sure has :)  The entry to add is a 'setpci' line above the "set root" line, which I can add in the boot order if I could see the grub menu!

See this part of the ArchWiki for details: [https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers](https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers)

---

### Post by varunendra on 2012-01-27
> **daehenoc said:**
> Thanks!  Done, however when the Mac boots up, I don't see the grub menu, I get a white screen, then a dark purple screen (maybe the grub menu is being displayed here but the Mac video card is not actually putting it on the LCD), then the Ubuntu boot screen and the computer boots Ubuntu.
Make sure the line: **"DEFAULT_TIMEOUT="** is _not set to 'zero'_. If it is, change it to **10 **or something that would be the timeout in seconds before it proceeds to boot the default selection.


> **daehenoc said:**
> The entry to add is a 'setpci' line above the "set root" line, which I can add in the boot order if I could see the grub menu!

See this part of the ArchWiki for details: [https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers](https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers)
That seems to me a full command, not just a boot-parameter. I'm not sure how to put that in /etc/default/grub file to make it effective, and the wiki page you linked to suggests to directly edit the **/boot/grub/grub.cfg** file which is _not recommended_! Because any error in editing that file may render the system to become unbootable, requiring you to correct it or completely regenerate it from a live session.

So I'd recommend to first try to make the grub menu show up, and try that command temporarily by editing the boot commands during boot time. If that seems to work, then you can safely add it to the grub.cfg file (but be careful with it).

If "DEFAULT_TIMEOUT=" already has a non-zero value or changing it to a higher value doesn't help, please post the contents of your /etc/default/grub file:
```
cat /etc/default/grub
```I hope it's something simple we are missing, and can figure it out this time.


**_EDIT_:**
Just realized - It is actually "GRUB_TIMEOUT in 11.10, not DEFAULT_TIMEOUT.

---

### Post by daehenoc on 2012-03-20
> **varunendra said:**
> Make sure the line: **"DEFAULT_TIMEOUT="** is _not set to 'zero'_. If it is, change it to **10 **or something that would be the timeout in seconds before it proceeds to boot the default selection.
OK, in the meantime, I have a replacement Macbook Pro and I have installed my SSD into it.  I've got the grub menu to display for 10 seconds, so win :)
> **varunendra said:**
> That seems to me a full command, not just a boot-parameter. I'm not sure how to put that in /etc/default/grub file to make it effective, and the wiki page you linked to suggests to directly edit the **/boot/grub/grub.cfg** file which is _not recommended_! Because any error in editing that file may render the system to become unbootable, requiring you to correct it or completely regenerate it from a live session.

So I'd recommend to first try to make the grub menu show up, and try that command temporarily by editing the boot commands during boot time. If that seems to work, then you can safely add it to the grub.cfg file (but be careful with it).I manually edited the boot entry "Ubuntu, with Linux 3.0.0-12-generic" and added the 'setpci' command into the boot order, just above the 'set root' line:
```
...
insmod ext2
setpci -d 8086:2828 90.b=40
set root='(hd0,gpt2)'
...
```
And booting Ubuntu is **[SIZE="3"]an order of magnitude faster[/SIZE]** (holy... from the grub menu to *desktop* is [SIZE="3"]FIVE SECONDS[/SIZE]) and looking at the output of lspci -nn shows that the SATA controller is now in AHCI mode rather than IDE mode :D

So now I need to figure out how to add this line into the grub boot order for this menu entry - obviously not adding it directly to grub.cfg, but into the 10_linux entry in /etc/grub.d ... somehow!  I'll go do some research and get back to you.

---

### Post by Sidolin on 2012-03-20
Unfortunately that breaks suspend/resume. Have a look at [https://bugs.launchpad.net/mactel-support/+bug/817017](https://bugs.launchpad.net/mactel-support/+bug/817017) for a kernel patch that does what the setpci does but works with suspend.

---

