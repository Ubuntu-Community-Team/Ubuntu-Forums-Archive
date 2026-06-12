---
title: "Laptop not turning off (backlight is still on and fan running)"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by pjhartt on 2008-03-17
I read some similar problems and it was suggested that I add acpi=force to #defoptions

I have done this as suggested

sudo update-grub

cat /proc/cmdline

and added the acpi=force to the kernal

and the update worked, in that when I did the cat /proc/cmdline it said

root=UUID=790d6d30-ebca-482a-b08e-132746698f2d ro quiet splash acpi=force

But (big BUT) my laptop still does not shutdown. The backlight is still on and the fan is running. It stops at that point and the only way I can turn it off is to hold the power button down until it turns off. Then same happens when I use Hibernate.

Are there any other suggestions?

Regards
Peter

---

### Post by spiderbatdad on 2008-03-17
What kind of laptop, please? No. no. let me guess...Thinkpad...er T-60

---

### Post by linuxman94 on 2008-03-17
my desktop does that to and i just hit the power button when the screen is blank.  i haven't had any problems so far.

Best of luck 
Evan

---

### Post by pjhartt on 2008-03-17
It is a Zoostorm 4-6612 15.4" Advanced Vista Premium Media Laptop

Intel Core 2 Duo 2.0GHz, 1GB RAM, 120GB HDD, 256MB ATI X1600, Wireless LAN, TV

I'm am running a dual boot with Vista and Ubuntu desktop 7.10 i386 looking to eventually dump vista

---

### Post by spiderbatdad on 2008-03-17
When you boot into Linux you should not leave Vista hibernating. Vista must be shut down cleanly first.

---

### Post by pjhartt on 2008-03-17
Vista has been shutdown either by completely turning off laptop or by doing a restart.

---

### Post by spiderbatdad on 2008-03-17
This appears to be a bios related issue. Possibly updating your bios or restoring default settings will fix the problem. You might also be able to set irq polling in the bios to automatic. There is a lengthy bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42160](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/42160)
While it does mention forcing acpi, it offers some other solutions. I read in another bug report as well where the user solved by adding ```
acpi=force lapic
``` to the kernel line.

---

### Post by pjhartt on 2008-03-18
I have added the lapic

But there is no change.

I am going to try the suppliers for a bios upgrade

---

