---
title: "Grub Removal"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Anthonylinxop on 2007-07-05
Hi!
I have recently installed Ubuntu, and it is really useful. However, I need the use for the harddisk partition and I deleted the linux partition. The Grub bootloader is still in the computer and now it is not able to boot up directly to WinXP OS. Is there anybody who can help or advice me to remove that totally? :(

---

### Post by koshari on 2007-07-05
google "restore mbr"

---

### Post by aquavitae on 2007-07-05
Reinstall the windows boot loader using the windows install cd - repair.  As koshari says, Google is your Friend.

---

### Post by coffeecat on 2007-07-05
To repair the mbr you can run 'fixmbr' from the repair console of the Windows XP install CD. Which is fine if you have a Windows XP install CD but, of course, most computers come with a restore image CD or none at all.

So... Although you want to get rid of Grub, you can use the [Super Grub Disk]("http://geocities.com/supergrubdisk/"). What it doesn't spell out on that page is that you can boot into Windows using the SGD and/or repair the mbr with a fixmbr equivalent.

But there's one problem if you don't have a Linux or Apple machine handy. You have to download a .bz2 or .gz compressed image from which you extract the .iso image.

**Edit:** To the two previous posters - this is the Absolute Beginners subforum. My opinion is that 'Google is your friend' is inappropriate here.

---

### Post by koshari on 2007-07-05
> To the two previous posters - this is the Absolute Beginners subforum

with my apologies iam sure a beginner will find a lot more user friendly instructional from a dedicated windows site as there are prolly 10 times more of them than linux support forums, if i were a beginner wanting to restore a windows mbr a super grub disc would be the last avenue i would explore.

---

### Post by coffeecat on 2007-07-05
> **koshari said:**
> iam sure a beginner will find a lot more user friendly instructional from a dedicated windows site

Except that a dedicated Windows site would be full of people either ignorant of or prejudiced against Linux, and who would probably make silly comments about grub  - not knowing what it is.

> **koshari said:**
> if i were a beginner wanting to restore a windows mbr a super grub disc would be the last avenue i would explore.

Which is precisely the reason I mentioned it. It's an excellent all-round utility and helps you with both Linux **and** Windows and the download size is so small there's absolutely no reason not to get it.

And as far as getting help with Windows and the mbr is concerned, there are many people on this forum with experience of dual-booting Windows with Linux and the problems one can encounter with grub and the mbr which is why this is a good place to get the help the OP wants. Do you have a problem with that?

---

### Post by koshari on 2007-07-05
> Do you have a problem with that?

no sir, and i apologise again for questioning your absolute knowledge, 

if i even think to do so in the future please let me know so i can perform sone kind of shock theropy on myself in the vein hpoe that i will never refer someone to google again.

---

### Post by freebird54 on 2007-07-05
Smile when you say that! :)

I think that all that was meant is that, while technically a correct answer, it was a bit terse for this particular forum.  After all, you did include the search term too!

No shocks needed....

---

