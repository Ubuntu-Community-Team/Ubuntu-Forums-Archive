---
title: "SOS!!! Problems while installing the Feisty Fawn on 64-bit Athlon due to APIC!!!!"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by vishwas_s on 2007-06-05
I read a lot about Ubuntu 7.04 on the net and elsewhere and thought I would give it a try.
I got the cd ordered from Canonical and tried to install the OS

Now, my computer config is:

 AMD Athlon X2 64-bit 4400+
 ASUS M2N-MX motherboard

I was running Win XP Pro SP2 prior to installing Ubuntu.
However, while running the CD Live , I had a problem
The terminal gave me a message that said:

"Kernel Panic: APIC + timer doesn't work together"

I duly went over to the motherboard options and disabled API.

The CD then ran fine and I installed Ubuntu.

Now I then tried to get back to Windows and I couldn't since API was disabled. So, I had to enable it again

So, here's my question: Do I have to run the charade of enabling and disabling API every time I switch OS?

Also, what is swap space? That caused quite a few problems during installation.

---

### Post by Kobalt on 2007-06-05
You can to boot disabling APIC this way : at the LiveCD boot screen press F6 and add at the end of the line, after a space, the following : > noapic nolapic
Then press Enter to boot.

You shouldn't worry about the swap partition if you don't want to partition your drive manually. If you need help though, you can check this out : [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by vishwas_s on 2007-06-05
Thanks a lot for ur suggestion.

But now, I have already installed Ubuntu. Can i still carry out the idea u gave me?

---

### Post by Kobalt on 2007-06-05
Yes, you can add that option to the 'defoptions' line in your /boot/grub/menu.lst file. You'll need to manually edit this file with ```
gksu gedit /boot/grub/menu.lst
```
Find this line, remove the # at the begining of the line and enter the boot options you'd like to be loaded. Save and exit, and upon your next reboot it will take effect.

---

