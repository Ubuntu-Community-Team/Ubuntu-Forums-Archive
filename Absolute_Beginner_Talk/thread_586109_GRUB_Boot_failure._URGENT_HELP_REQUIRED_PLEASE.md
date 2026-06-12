---
title: "GRUB Boot failure. URGENT HELP REQUIRED PLEASE"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by scrapmetal on 2007-10-22
Intel P 4 2gig 
 Ram 2 x 512 = 1024, 
 HD 1, 60gig 
 HD2 250gig 
 HD3 (ext USB) 300gig, 
 All hardware OK, stress tested as am hardware nerd.
 
 Loaded to HD 2, used 16% of 250 Gig for minimum load , no transfer of any documents included.
 GRUB ERROR 17, 
 
 XP Home Ed, loaded on HD 1, (have no OEM CD) not supplied by computer provider (computer provider gone bust)
 Xp home ed. error report NTLDR is missing. This was reported before Kubuntu 6.06.1 intel desktop install was done thought GRUB would pick up XP automatically.
 GRUB in search mode found XP on HD 1 but failed to provide dual boot. Am running on live cd now.
 
 I am 500 km from my computers and resources have to start journey home in 3 hours need help URGENTLY. Step by step would be very helpful as have short term brain injury, IQ up there still.
 
 Many thanks for bailing me out again and am waiting in anticipation regards Scrapmetal. Am staying live with this post.
 
 Still converting the masses  Ubuntu Rules

---

### Post by cfaulkner on 2007-10-22
hrmm, sounds to me that the boot order is messed up, i had this problem as well and the way I resolved it was I made Windows XP my hd1  and Linux my hd0.  Put grub on hd0, edited my /boot/grub/menu.lst  to reflect those changes.


you may have to boot into a live cd and make those changes as well..  Make sure your External HDD is not connected when you boot, otherwise it will mess up the Boot Order.

---

### Post by scrapmetal on 2007-10-22
thaks, will try that now.
anyone else out there?

---

### Post by scrapmetal on 2007-10-23
SOLVED:lolflag:

Was not GRUB, cross hard drive installation of XP was the source of all problems.
Thanks for the help.

---

