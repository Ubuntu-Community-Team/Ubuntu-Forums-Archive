---
title: "Asus K55VD (A55VD) FN + F5 F6 Brightness dont working"
date: 2013-01-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by khaos1 on 2013-01-17
Hi I have just installed Ubuntu 12.10 in Asus K55VD (A55VD-SX406H)  I7-3630M, RAM 8GB, nvidia GEFORCE 610M 2GB. I have installed bumblebee nvdidia drivers. But the brightness keys (FN F5,F6) are not working. 

Any idea?

Thanks in advance

---

### Post by khaos1 on 2013-01-20
I am one step closer to the fix. I have tried acpi_osi= in boot options and now I can adjust the brightness with the fn keys but without Ubuntu notification. The sound adjustment works nice with notifications. Is there a way to fix that?

---

### Post by timroll on 2013-01-21
Hello!
I've got the same laptop and hot keys for brightness don't work too (I'm using Xubuntu 12.10 64-bit). Could you please tell me what did you mean?
> **khaos1 said:**
> I have tried acpi_osi= in boot options

I've tried this:
> 1. sudo gedit /etc/default/grub
   2. find the line starting with GRUB_CMDLINE_LINUX_DEFAULT
   3. add "acpi_osi=Linux acpi_backlight=vendor" to the options
   4. sudo update-grub2
   5. reboot
But no luck.
What did you do to make Fn+F5 and Fn+F6 work?
Thanks.

---

### Post by khaos1 on 2013-01-21
> **timroll said:**
> Hello!
I've got the same laptop and hot keys for brightness don't work too (I'm using Xubuntu 12.10 64-bit). Could you please tell me what did you mean?


I've tried this:

But no luck.
What did you do to make Fn+F5 and Fn+F6 work?
Thanks.

1. sudo gedit /etc/default/grub
2. find the line starting with GRUB_CMDLINE_LINUX_DEFAULT
3. add "acpi_osi=" to the options
4. sudo update-grub2
5. reboot


Hope that it will fix. Please reply here if that fixed for you and if you get ubuntu notification for this

---

### Post by timroll on 2013-01-22
Thanks a lot for your advice, khaos1!
Yesterday I tried to do as you told me. And voila - now I can adjust brightness with hot keys. But - just like you, I can't see any notifications from *buntu. Though it doesn't really bother me.

---

### Post by khaos1 on 2013-01-23
> **timroll said:**
> Thanks a lot for your advice, khaos1!
Yesterday I tried to do as you told me. And voila - now I can adjust brightness with hot keys. But - just like you, I can't see any notifications from *buntu. Though it doesn't really bother me.

Very nice to hear that is partial fixed. 

I have opened a launchpad bug report. Timroll please add your info to the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1100825](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1100825)

---

### Post by rafaelhsn on 2013-01-24
> **khaos1 said:**
> Very nice to hear that is partial fixed. 

I have opened a launchpad bug report. Timroll please add your info to the bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1100825](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1100825)

Hi! Thanks for the tip, it also worked here but with this change I have a little bug here, after reboot the browser chromium starts with a very small size and cannot be maximized (just on first open) , it stay like that, i have to close it and open again then it restore to normal size.

like that: [https://www.dropbox.com/s/v0dy33kc1f54slt/screen.png](https://www.dropbox.com/s/v0dy33kc1f54slt/screen.png)

Do you or someone have an idea what could be that?

Thanks!

---

### Post by khaos1 on 2013-01-25
> **rafaelhsn said:**
> Hi! Thanks for the tip, it also worked here but with this change I have a little bug here, after reboot the browser chromium starts with a very small size and cannot be maximized (just on first open) , it stay like that, i have to close it and open again then it restore to normal size.

like that: [https://www.dropbox.com/s/v0dy33kc1f54slt/screen.png](https://www.dropbox.com/s/v0dy33kc1f54slt/screen.png)

Do you or someone have an idea what could be that?

Thanks!

If you remove the boot setting then the chrome is ok? Very weird problem. If you can submit that you have the bug too in the launchpad page:

Please make a comment in the bug and describe your situation.
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1100825](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1100825)

---

### Post by rafaelhsn on 2013-01-25
> **khaos1 said:**
> If you remove the boot setting then the chrome is ok? Very weird problem. If you can submit that you have the bug too in the launchpad page:

Please make a comment in the bug and describe your situation.
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1100825](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1100825)

Hi

I Just fixed it using the command -start-maximized on shortcut =)

Thaks a lot for your help!

---

### Post by Guilmxm on 2013-05-02
Hi, 

I have the same problem using Ubuntu 13.04 (gnome version), also with an Asus KV55VD.

The only satisfying workaround is using [COLOR=#000000]"acpi_osi=".

Strangely, an other workaround i have found almost works:

[/COLOR][https://help.ubuntu.com/community/AsusZenbookPrime#Ubuntu_13.04](https://help.ubuntu.com/community/AsusZenbookPrime#Ubuntu_13.04)[COLOR=#000000]
[/COLOR][COLOR=#333333][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="splash quiet acpi_osi='!Windows 2012'"[/FONT][/COLOR]
Ubuntu notification works, hotkeys almost works but every press requires a few seconds to be detected or applied by the system.
This is not usable with in this case Ubuntu notification works...

Added this comment to the launchpad bug.

Thanks for this cool workaround, i was searching for it for many hours!

---

### Post by timroll on 2013-05-02
> **Guilmxm said:**
> 
[COLOR=#333333][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="splash quiet acpi_osi='!Windows 2012'"[/FONT][/COLOR]


Thanks a lot! It works for me on Xubuntu 13.04. All function keys are usable.

---

### Post by daltore on 2013-05-03
I have an ASUS K55A-DH71, and I can confirm that "GRUB_CMDLINE_LINUX_DEFAULT="splach quiet acpi_osi="" does work on the 3.5.0 kernel under Linux Mint 14 (equivalent to Ubuntu 12.10 for those who don't know).

No operating system notifications, as mentioned, but I can't say as I care too much, I have my brightness control keys working!  (Thank you very much, by the way.)

However, when I change "acpi_osi=" to "acpi_osi='!Windows 2012'", it does NOT work.  No idea why, just thought I'd contribute.

---

### Post by gatuki on 2013-05-03
Hi, I've got the same problem with my ASUS S200E running Linux Mint 14, everything works except for the Brightness function keys F5 and F6. When I type "sudo gedit /etc/default/grub" into the Terminal an empty window opens with "grub (/etc/default) - gedit" written at the top. There's no text to edit whatsoever.
Do you know whether there's something I need to install first?
I'm grateful for any help!

---

### Post by LightD7 on 2013-05-03
Hi, sorry that my English isn't that good. I've got the same computer(Asus K55vd) but with i5-3210M. I never got bumblebee to work but brightness buttons works fine!

I might have done something wrong when installing bumblebee, but I don't think so. Any ideas?

---

