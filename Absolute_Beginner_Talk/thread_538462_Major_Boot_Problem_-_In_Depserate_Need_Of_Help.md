---
title: "Major Boot Problem - In Depserate Need Of Help"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by GallienKreuger on 2007-08-30
Hi all, any help you can lend me would be greatly appreciated.

I've never used Linux before and was very interested in trying it out, so I installed Wubi on my system. I have an HP Laptop that runs the Media Center edition of Windows XP. For whatever reason, after I had played with Ubuntu in Wubi a few times with a few normal reboots after upgrades, I rebooted and now the my computer won't boot any operating system. It defaults to Windows XP, says it won't boot correctly, I go to safe mode, and then a blue screen flickers and the system restarts. I could really use some help as this is my main computer system.

Again, please help, as you can tell, I'm very confused and severely panicked.

Thanks,
Dan

---

### Post by Hobo Joe on 2007-08-30
I'm not totally clear on how Wubi works, but I'm assuming it doesn't open when you boot up, and that you have to run it to get Ubuntu.

If that's the case, then your problems should not be related to Ubuntu or Wubi.

---

### Post by GallienKreuger on 2007-08-30
When Wubi worked, what would happen was when I would boot the computer it would give me the option of choosing between XP and Ubuntu.  Wubi, instead of requiring a partition, installed into a virtual file (or somethin like that)

---

### Post by Hobo Joe on 2007-08-30
Oh, in that case, I'd guess it's the bootloader.

Does it run on GRUB?

---

### Post by GallienKreuger on 2007-08-30
the wubi page says it runs on grub4dos

---

### Post by hh93 on 2007-08-30
> **GallienKreuger said:**
> the wubi page says it runs on grub4dos

is windows CD available?

---

### Post by TeaSwigger on 2007-08-30
Hello,

Don't panic. Sounds like a bootloader issue so your actual files and operating systems should be there and ok. You'll get it fixed and back on the go.

Ubuntu has its own bootloader, GRUB, which will let you pick which system you want to use at startup, like the wubi you're describing. So, maybe a silly question given I don't know a whole lot about this stuff and that you say it was after some number of boots, but,,, Did ubuntu's GRUB replace wubi's? 

Can you select to boot into ubuntu?

---

### Post by TeaSwigger on 2007-08-30
Another possibly silly question, but when you installed ubuntu, do you remember if it said something to the effect that it would install GRUB into the MBR? That would over-write the windows bootloader; ubuntu might have booted fine, but then when Wubi tried to boot Windows, it unexpectedly found the ubuntu bootloader, causing the inability to load it properly that you describe...

---

### Post by stevebakerj on 2007-08-30
I would boot from your XP disk and do a FIXMBR, as Wubi is a virtual install it will not harm any data on XP or on the virtual Ubuntu. If you want to move your Wubi install from its virtual setting to a dual boot with XP read here:

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Or just uninstall Wubi through the normal Win uninstall procedure and do a clean Dual Boot install of Ubuntu with XP and get the real GRUB installed, to change between OS's

---

