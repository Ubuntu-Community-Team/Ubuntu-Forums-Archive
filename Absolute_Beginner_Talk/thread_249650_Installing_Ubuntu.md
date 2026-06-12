---
title: "Installing Ubuntu"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Rinku on 2006-09-02
**Update:** I'm having a little trouble, tomorrow I'm going to put a extra HDD on my computer, so I decided to put in the live cd and try Ubuntu on my own computer, just to see if everything would go smoothly like with our other pc, well, im getting an error I believe.

It always stops at "Starting Enterprise Volume Management System" and keeps giving errors indefinetly. Help? :confused: 

I attached a picture so you see what I'm talking about.

=============================================================
[I][SIZE="1"]I've been trying Ubuntu on one of my computers at home (one we use to test OS's and so forth), and I've been liking it so far :KS 

I have a Windows XP Professional x64, (Intel Celeron 2.5GHz, 512 MB RAM, ATI Radeon Video card), I was wondering if I can install Ubuntu on my computer without losing my Windows and programs with it? I have a few internal HDD I could install.

Any ideas?[/SIZE][/I]

---

### Post by taurus on 2006-09-02
Yes, you can install Ubuntu on your machine without losing your XP.  Just tell the installer where to install it.  Be careful not to pick the harddrive that XP is on...  Then, install GRUB on MBR so you can boot either one of them, XP or Dapper, when you turn your machine on.

---

### Post by darkenedday on 2006-09-02
> **Rinku said:**
> I've been trying Ubuntu on one of my computers at home (one we use to test OS's and so forth), and I've been liking it so far :KS 

I have a Windows XP Professional x64, (Intel Celeron 2.5GHz, 512 MB RAM, ATI Radeon Video card), I was wondering if I can install Ubuntu on my computer without losing my Windows and programs with it? I have a few internal HDD I could install.

Any ideas?

When you install Ubuntu it will give you an option when you partition your HD it will give you an option to either use the free space that's already there (provided you have at LEAST 2gb) and an option to resize your current partition to make room for Ubuntu neither of these will overwrite windows, Ubuntu will also install GRUB which will allow you to select either ubuntu or windows on startup

---

### Post by aysiu on 2006-09-02
To be 99% sure you don't lose your XP, just defragment your drive and then follow these directions:
[Installing a dual-boot with the Desktop CD](http://www.psychocats.net/ubuntu/installing.html)
[Installing a dual-boot with the Alternate CD](http://users.bigpond.net.au/hermanzone)

To be 100% sure you don't lose XP, **back it up first**, then defragment and then follow these directions:
[Installing a dual-boot with the Desktop CD](http://www.psychocats.net/ubuntu/installing.html)
[Installing a dual-boot with the Alternate CD](http://users.bigpond.net.au/hermanzone)

---

### Post by Rinku on 2006-09-02
> **taurus said:**
> Yes, you can install Ubuntu on your machine without losing your XP.  Just tell the installer where to install it.  Be careful not to pick the harddrive that XP is on...  Then, install **GRUB on MBR** so you can boot either one of them, XP or Dapper, when you turn your machine on.

Thanks that prety much answers my question, sorry for the newb question but could you explain a little bit what is GRUB?

---

### Post by taurus on 2006-09-02
Help yourself!!!  ;) 

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by aysiu on 2006-09-02
> **Rinku said:**
> Thanks that prety much answers my question, sorry for the newb question but could you explain a little bit what is GRUB?
[quote=Wikipedia]GNU GRUB ("GRUB" for short) is a computer program for controlling how a computer starts, when multiple operating systems have been installed on one computer; it is a multiboot boot-loader software package from the GNU project. [/quote] More details here:
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

Bottom line--it allows you to choose whether you want to boot into Windows or Ubuntu.

---

### Post by Rinku on 2006-09-02
Thank you taurus, darkenedday and aysiu, i'll be checking all these links and info now, you guys rawk. :3

---

### Post by Rinku on 2006-09-03
I'm having a little trouble, tomorrow I'm going to put a extra HDD on my computer, so I decided to put in the live cd and try Ubuntu on my own computer, just to see if everything would go smoothly like with our other pc, well, im getting an error I believe.

It always stops at "Starting Enterprise Volume Management System" and keeps giving errors indefinetly. Help? :confused: 

I attached a picture so you see what I'm talking about.

---

### Post by Rinku on 2006-09-03
D:

---

### Post by Rinku on 2006-09-03
(;-; )

---

### Post by taurus on 2006-09-03
What's the spec of the computer with that error message then?

---

### Post by Rinku on 2006-09-03
Intel Celeron 2.53GHz
512MB of RAM
ATI Radeon Video Card
Pioner DVD-RW

Um, do you have a certain device in mind that you want to check?

---

### Post by taurus on 2006-09-03
Probably about your harddrive!!!

---

### Post by Rinku on 2006-09-03
40GB HDD, see the pic for details, and thanks <:3

---

