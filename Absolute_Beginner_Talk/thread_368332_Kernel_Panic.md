---
title: "Kernel Panic"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by enpey on 2007-02-23
Ok, well I managed to sort out the issues I was having with the update process (was a DNS issue), and then once I installed all the updates, I believe the machine has been restarted once or twice today, but when i got home tonight and the very first time after the updates were installed I have been hit with this:

[17179570.936000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option

So I have searched a little, but not enough. I have no idea what this means, so a short explanation as to what my problem might be would be great, and a suggested solution would make my day. I'm also unsure of how to boot with apic=debug or boot with noapic option, so if I need to do this please tell me how to do it. Any info will be appreciated

Thanks, Nathan

---

### Post by Jussi Kukkonen on 2007-02-23
Can't tell what the problem is, but here's info about the boot options:

The options are something you add into your "boot stanza". For example my */boot/grub/menu.lst* currently has this: 
> title           Ubuntu, kernel 2.6.20-8-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-8-generic root=UUID=8b3a87cc-9b93-4670-b131-f5cc23c00b72 ro quiet splash
initrd          /boot/initrd.img-2.6.20-8-generic
savedefault

However, earlier kernels had a bug that resulted in a similar crash as yours. I had to use the "acpi=force" option like this :
> title           Ubuntu, kernel 2.6.20-8-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-8-generic root=UUID=8b3a87cc-9b93-4670-b131-f5cc23c00b72 ro quiet splash acpi=force
initrd          /boot/initrd.img-2.6.20-8-generic
savedefault


Some notes:
* You can try these out without permanently editing the file: just select "Edit" in the GRUB menu when booting and edit the kernel-line
* If you decide that you need a boot-option to succesfully boot, be aware that the config file /boot/grub/menu.lst is partly generated automatically -- if you do it wrong, changes will be lost on next upgrade. You'll have to edit the #defoptions and #altopions -lines. Ask if you have questions about that.

---

### Post by enpey on 2007-02-23
Noone can point me in any supportive direction? Even another place to ask?
I would really appreciate it..
Nathan

---

### Post by enpey on 2007-02-23
Sorry, seems the page wasn't reloaded when I went back into it. 
Well I'm back in Ubuntu (I rebooted from Windows and it just worked, current kernel & normal boot), but I have read in threads elsewhere similar things have happened ie the problem can be inconsistent like that. 

Ok, thanks for the info on where to place those options, what does the "acpi=force" option do? What is this acpi thing we are talking about? I'm prepared to read, so links or detailed info won't bother me too much. 

I figured out how to edit the GRUB menu (as I couldn't get GRUB to work off (hd0) so I installed it to (hd1) instead and had to edit the top lines of all options to get them to work and have manually and permanently had them edited in the menu.lst file), but I am unsure as to what the "#defoptions and #altopions -lines" are, so an explanation of what they are and why I'd change them would be great.

Thanks, Nathan

---

### Post by Jussi Kukkonen on 2007-02-23
The boot options are a notoriously under-documented feature... I'm guessing there are not many people on the planet that actually understand what they do. Mostly they have to be used to switch off some feature because motherboard manufacturers mess up e.g. their ACPI implementation or a kernel coder made a mistake -- mostly things will be fixed in later kernels so one can stop using the options (like I did)

About menu.lst:
All lines that are not comments between the AUTOMAGIC KERNELS LIST markers may be modified by the debian update-grub script, and that script is ran every time there's a new kernel. Permanent modifications to the file should be made , a bit confusingly, to the comments, like this (the last line is what matters):
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi=force

```
Now, when I run update-grub, all normal kernel stanzas in the file will be updated so that they have those options. When a new kernel is installed it will also use those options -- pretty nifty actually.
I believe your grub location should be added with the *default grub root device* -option
```
# groot=(hd0,1)

```
(edited to suit your configuration of course)

---

