---
title: "What's a session? Can I dual boot with another Linux distro?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by OneEyedMan on 2006-10-13
I've got a few simple questions on Linux in general. First off, what exactly is a "session"? I've heard the term here and there, and I'm noticing it on startup and logoff screens, but I'm not sure what it's there for or what it is/does.

Secondly, my spare box is running Zenwalk, and I wanted to know if I could dual-boot it to run another Linux distro as well. Puppy, for example. I think I've heard of this being done, but I'm not sure how to go about setting up a dual-boot with anything but Ubuntu/XP. Is it hard, or can it be boiled down for a beginner?

Thanks!

-J

---

### Post by bulldog on 2006-10-13
Session means from the moment you boot till you shut down is called a session.

Nothing important.

Sure,you can install another linux distro instead of windows.

Your bootloader should pick it up and add the necessary entry's.

---

### Post by Ben Sprinkle on 2006-10-13
You know on windows when you login and logout?
Same thing, means "Lock session" => "Lock computer"
Login = >Start session
Logout => End session
Hope that helps.

---

### Post by doobit on 2006-10-13
> **bulldog said:**
> 

Your bootloader should pick it up and add the necessary entry's.

Sometimes you may need to edit the bootloader's script to add the entry for the new Linux. The Developer's website usually has that information. Puppy and DamnSmall, and dyne:bolic, and maybe a few others out there that are made to be live distributions may have some unique ways to install as well, so look out for that.

---

### Post by linbetwin on 2006-10-13
A session starts when you log on and ends when you log off or restart/shut down your computer. So you can end a session and start a new one just by logging off and then on again, without the need to restart/shut down.

You can install multiple operating systems on your computer, not just two. It's not hard to do, but I can't explain it in detail here. Basically, you need to have at least one partition for every OS/distribution or you need to be able to create them (i.e. without destroying your data). The distribution you install last should be able to recognize all the others installed and allow you to boot from them.

---

### Post by OneEyedMan on 2006-10-13
So, if I'm running a distro on a single ext2 partition, will I need to create both a new partition for the second distro and a swap file paritition as well? When I did Ubuntu/XP, I created 2 or 3 new partitions for swap and storage, plus the Ubuntu partition.

-J

---

### Post by linbetwin on 2006-10-13
> **OneEyedMan said:**
> So, if I'm running a distro on a single ext2 partition, will I need to create both a new partition for the second distro and a swap file paritition as well? When I did Ubuntu/XP, I created 2 or 3 new partitions for swap and storage, plus the Ubuntu partition.

-J
I've never had multiple distros on one PC, but I think you can use a single swap partition for all distros.

---

### Post by Sef on 2006-10-13
> I've never had multiple distros on one PC, but I think you can use a single swap partition for all distros.


Yes, you can have a single swap for multiple distros.

---

### Post by jd65pl on 2006-10-13
You could have one partition for /home and one for a swap file, then you would be able to have a few linux distributions on the same disk all of which using a common home folder, you may find that quite useful in the future

---

### Post by migla on 2006-10-13
> **jd65pl said:**
> You could have one partition for /home and one for a swap file

Beware, I think, though: If you have the same username(s) for both distros with a shared /home, desktops and other things might get mixed up.

---

### Post by yman on 2006-10-13
I think that a session is when you log on with specific settings and everything you is part of the session and if you choose to save your sessions then next time you log in you can continue what you were doing. this is all spoken from a begginers mouth, so it needs verification.

---

### Post by steve.horsley on 2006-10-13
You can multi-boot fairly easily. You need a new partition for the / filesystem of each distro you install. If you want, you can have them all using the same partition for /home so that all the user data is there in all distributions. The advantage is ease of use, the disadvantage is the danger of bad clashes between the settings files of different versions of software.

GRUB is normally installed on the MBR, and uses a menu file located in /boot/grub. Remember that each new install will overwrite GRUB with one that uses its own menu file. Not really a problem since the installer always seems to find all other versions of Linux/windows, and puts them in the menu. You just end up with along list of boot options. I quad-boot Windows, Breezy, Dapper and Edgy.

---

