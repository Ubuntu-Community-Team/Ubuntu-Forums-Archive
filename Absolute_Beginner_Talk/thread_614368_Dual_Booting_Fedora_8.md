---
title: "Dual Booting Fedora 8"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-15
I'm thinking of dual booting Fedora 8 with my Ubuntu, but still am unsure about this, anyone who has tried and or runs Fedora 8 do you think this is a good decision?

---

### Post by jordanmthomas on 2007-11-15
If you want to try out Fedora 8, then it's a fine idea.
Why would you think it is a bad idea?

---

### Post by RobotoWorks on 2007-11-15
Well I herd its totally different from Ubuntu, I really like the Ubuntu feel and I dont want anything too different.

---

### Post by jordanmthomas on 2007-11-15
The only main difference is that Fedora has a bunch of really cool system administration tools that are a wee bit different than Ubuntu's, and some system configuration files are in different places.

That, and instead of debs you use rpms and you use a different package manager.
If you're used to Ubuntu you shouldn't have too much trouble familiarizing yourself to Fedora.

Since you're doing a dual boot, if you don't like Fedora it's just a matter of not using it / reformatting its partition.

**edit**
also, one more difference you'll probably notice quickly is that you use the root account and not sudo by default (for administration stuff).  You can go back to using sudo if you'd like, though.

---

### Post by RobotoWorks on 2007-11-15
Okay I'll try it, can you give me a link to a live cd download?

---

### Post by jordanmthomas on 2007-11-15
I may be mistaken since I haven't used Fedora since Fedora 7, but I believe the LiveCD is not an installation disk.  The only way to install it is to use the installation disk.

[http://fedoraproject.org/get-fedora.html](http://fedoraproject.org/get-fedora.html) 

Also, don't get offended by this, but what's up with people asking for links when it would be faster to find it yourself than to wait for me to find it and then give you the link?

---

### Post by RobotoWorks on 2007-11-15
In order to dual boot, which one of the choices should I pick to order?

---

### Post by jordanmthomas on 2007-11-15
You'll want the installation DVD.
If you don't know which you need, odds are you want the i386 version.

---

### Post by RobotoWorks on 2007-11-15
Do I just install it, or do I download it and then burn it onto DVD?

---

### Post by Adramelech on 2007-11-15
Live cd is can install also.

---

### Post by RobotoWorks on 2007-11-15
Oh, how do I dual boot though?

---

### Post by jordanmthomas on 2007-11-16
When you install, let it install Grub to the MBR and it should pick up your Ubuntu installation and configure it for you.

Make sure you know which partitions you are installing to, just like you had to know when installing Ubuntu.

---

### Post by RobotoWorks on 2007-11-16
Umm...okay...like I really understood that...

---

### Post by jordanmthomas on 2007-11-16
Well, before you go installing new operating systems, partitions are something you **need** to understand.  If you don't, you will end up deleting all your Ubuntu stuff.

The easiest way would be to use your Ubuntu LiveCD, fire up gparted, and make a free partition to install Fedora into.  When you install Fedora, it should either automatically set up the dual boot for you or ask you how you want to do it.  Fedora has a very friendly installer.

---

### Post by RobotoWorks on 2007-11-16
How do I create partitions?

---

### Post by jordanmthomas on 2007-11-16
You use gparted to resize (shrink) a partition.  Then, there will be free space after it.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Don't worry about formatting the free space.  Fedora will do it for you.

---

