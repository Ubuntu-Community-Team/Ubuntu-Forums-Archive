---
title: "Can I back up and restore Grub?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-04-20
I have a dual booting system which runs just fine (XP Pro and Hardy).

I would like to reinstall XP now as I want it streamlined for just games really, and it is currently bloated and all other things Microsoft.

I have read a number of threads about if it is or isn't possible to install XP second and still access Ubuntu, but as I already have everything set up with Grub etc, is it possible for me to back up grub and then install XP and then just drop grub back to where I need it? (I should also add that I don't actually know where it is at the moment!)

---

### Post by DBrocks on 2008-04-20
[http://ubuntuforums.org/showthread.php?t=112208](http://ubuntuforums.org/showthread.php?t=112208)

This should help you out alot. Look at "DarkPark's" post. (The one right under the Original Poster). He explains it perfectly.

> **darkpark said:**
> no, there isn't. the windows install will overwrite the MBR (master boot record) but this issue is easy to resolve.
after you install windows, boot from your ubuntu CD and select the recovery option.
once you're at the command prompt, simple re-run the grub config/setup. i don't know the specifics of reconfiguring grub, but if you search these forums than you should be able to find the answer or someone hopefully replies to this thread with a more complete answer.

---

### Post by markjensen on 2008-04-20
The basic MBR part of GRUB that gets overwritten is in the first section of your hard drive's MBR.  This section also contains partition information and such, so what I am about to show you **should not** be used if you plan on changing your partitioning (reformat, 'clean' installs are ok).

**sudo dd if=/dev/sda of=/boot/backup.mbr bs=512 count=1**
That will take one block of 512 bytes and make a copy called "backup.mbr" in your /boot directory.

Let Windows do it's thing, and you can boot Ubuntu LiveCD and then you can write the file back into sda.   You would have to change your "if=" (input file) to be wherever it is that your Ubuntu LiveCD sees the file.

---

### Post by DBrocks on 2008-04-20
> **markjensen said:**
> The basic MBR part of GRUB that gets overwritten is in the first section of your hard drive's MBR.  This section also contains partition information and such, so what I am about to show you **should not** be used if you plan on changing your partitioning (reformat, 'clean' installs are ok).

**sudo dd if=/dev/sda of=/boot/backup.mbr bs=512 count=1**
That will take one block of 512 bytes and make a copy called "backup.mbr" in your /boot directory.

Let Windows do it's thing, and you can boot Ubuntu LiveCD and then you can write the file back into sda.   You would have to change your "if=" (input file) to be wherever it is that your Ubuntu LiveCD sees the file.

Yes, but couldn't you do what DarkPark said to do?

---

### Post by lswest on 2008-04-20
my advice is just install XP and then follow instructions on restoring GRUB (i wrote a how-to, there's a link to it in the second line of my sig if you want).  It isn't hard to do, and definately a lot less work than backing up your GRUB now, since when you restore GRUB it will re-use the menu.lst you have on your linux partition.

---

### Post by Twizzle on 2008-04-20
> **markjensen said:**
>  you can write the file back into sda.  

Thankyou but I am being a real newbie here and need to know how exactly to do that?

---

### Post by sandysandy on 2008-04-20
just go ahead an reinstall XP, taking care that u do not overwrite ur ubuntu partition.

see this link on installing XP over ubuntu

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


ur MBR will also be overwriten by XP.

no sweat. just look at this thread to on how to re-install grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by sandysandy on 2008-04-20
have a look at this thread also

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)


regards

---

### Post by markjensen on 2008-04-20
> **DBrocks said:**
> Yes, but couldn't you do what DarkPark said to do?
Yeah, you can do a grub-install, but I think you lose your dual-boot options (not sure, as I haven't dual-booted in 5+ years) and have to manually edit and add in the chainloader to boot Windows.  Not difficult, but just different options.

Plus I was typing up my post while you already submitted yours linking to DarkPark's post. :P

---

