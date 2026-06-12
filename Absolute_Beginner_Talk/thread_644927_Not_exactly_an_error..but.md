---
title: "Not exactly an error..but"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-19
Id like to figure this out as the other issues i can spend other time on later...WWhen my pc boots up, i get a message after grub loads im assuming "you passed an undefined mode number" When i hit spacebar it boots normally though loading to the kde desktop.  Why would it do this, and is my system in need of a reinstall just for one issue that seems maybe easy to fix?  I was able to fix other issues last night partly

---

### Post by LaRoza on 2007-12-19
> **sox fan Matt said:**
> Id like to figure this out as the other issues i can spend other time on later...WWhen my pc boots up, i get a message after grub loads im assuming "you passed an undefined mode number" When i hit spacebar it boots normally though loading to the kde desktop.  Why would it do this, and is my system in need of a reinstall just for one issue that seems maybe easy to fix?  I was able to fix other issues last night partly

What is the grub line?

---

### Post by sports fan Matt on 2007-12-19
I'll reboot and write it down and get back to you..Im assuming this is under grub but i'll confirm to make sure:)

---

### Post by sports fan Matt on 2007-12-19
looks like this i think: kenel/boot/vmlinuz-2.622-14-generic root=uuid-f398940c-50954b31 i think and then it cuts off..Im not sure..easy or hard to fix in your opinion?

---

### Post by Inxsible on 2007-12-19
> **sox fan Matt said:**
> looks like this i think: kenel/boot/vmlinuz-2.622-14-generic root=uuid-f398940c-50954b31 i think and then it cuts off..Im not sure..easy or hard to fix in your opinion?
that simply tells you what kernel you are using and it also tells you the UUID of the root drive where Linux is installed.

That is not an error message.

---

### Post by sports fan Matt on 2007-12-19
ok..Thats understandable...Where could i find out why that is being thrown out at boot..the machine starts and grub fulls loads cause it gets as far as there then that pops up, and im not sure why...

---

### Post by Inxsible on 2007-12-19
> **sox fan Matt said:**
> ok..Thats understandable...Where could i find out why that is being thrown out at boot..the machine starts and grub fulls loads cause it gets as far as there then that pops up, and im not sure why...The grub is the display where you choose which OS to load (if you have multiple OSes installed)

Does it happen after you choose the OS or before?

---

### Post by sports fan Matt on 2007-12-19
It occurs before the blue Kubuntu loading screen with the progress bar, but only Kubuntu is installed, (I got rid of gnome in favor of KDE)

---

### Post by Inxsible on 2007-12-19
ok. I would say don't worry about it.

I get a 'Failed to allocate memory resource 00000000:@2600000' message every time i boot into Ubuntu.

Does no harm. It also doesn't require me to press any key for it to go forward. It might just be that its trying to load a package out of order but eventually gets it right.

I still haven't found out why i get the above message, but at least its not giving me any problems. But you are right, it would sure be nice to know :)

---

### Post by sports fan Matt on 2007-12-19
You know...I just removed a broken Sun Java 5.0 plug in I think package when I tried to reinstall opera and get it unlocked..Perhaps this is why the usr directory of opera was locked and couldnt open it?  And yeah its a relief to say theres no harm involved..Its kind of nice to know others from tine to time get errors and makes me not look as much as a noob as i figured..after all, i rebuilt pc's for 4 years in high school:)

---

