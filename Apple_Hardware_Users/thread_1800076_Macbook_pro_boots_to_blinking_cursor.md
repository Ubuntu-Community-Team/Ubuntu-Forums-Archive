---
title: "Macbook pro boots to blinking cursor"
date: 2011-07-08
forum: Apple Hardware Users
---

### Post by Jalaska13 on 2011-07-08
I'm trying to install ubuntu on my December 2009 MacBook Pro (15" - 64 bit).  I've tried using both the regular AMD64 version and the AMD64+mac version, but neither works.  They both boot past the "ISOLINUX" line but then sit at the blinking cursor for at least 10 minutes (I haven't let it go past that, but I have no reason to assume letting it run longer would help).  Does anybody know what causes this or how to fix it?

---

### Post by Jalaska13 on 2011-07-08
Bump.

---

### Post by Jalaska13 on 2011-07-10
bump...

---

### Post by johnmurrayvi on 2011-07-10
After you choose to boot from the live CD, right when the display turns purple, hit 'escape' then a menu should appear. Hit 'escape' again, the menu will disappear and you will be able to select a different menu. Hit 'fn' + 'f6' and use the arrow keys to go to "nomodeset", hit 'enter' to select it, then 'escape' again to close that menu. Then you can either select "Try Ubuntu without installing" or "Install Ubuntu" and it should boot.

---

### Post by Jalaska13 on 2011-07-10
thanks; trying this right now.  I'll let you know if it works.

---

### Post by Jalaska13 on 2011-07-11
So that worked for booting.  It booted fine (although the GUI was an older version like this - [http://nanangsyaifudin.files.wordpress.com/2011/03/ubuntu.jpg](http://nanangsyaifudin.files.wordpress.com/2011/03/ubuntu.jpg)).  It installed properly, but now the install won't boot.  I have my HD partitioned like this:
500 total
400 HFS+
100 EXT4 (formatted during install)
The bootloader is on the ext4 partition, but I have rEFIt installed, which recognizes the partition as bootable.  I've tried both booting from the bootloader and directly from the OS on the ext4 partition, and both just bring me to a quickly-bliking cursor like the original problem, but there's no purple screen and hitting escape doesn't work.

---

### Post by Jalaska13 on 2011-07-12
Nevermind.  Reinstalling as an upgrade (as if I were upgrading from an older OS) did the trick, although I have no idea why.  W/e; it works, and I may never know why it didn't before.

---

