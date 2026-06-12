---
title: "Grub Loses Windows - dual boot"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by OZTack on 2007-07-31
Hi - Not sure if this is a bug or if I em - bug ' ed it :D

Installed Feisty dual boot yesterday.

Short story - Grub did NOT show an option to boot to XP ( I have fixed that - see below)

Question is - Was it me or a bug in the process?

What I Did -

Have 2 HDD

1)  Dell utility Part | Win XP PART | Dell Restror Part
2)  NTFS Part for XP | Page file Part for XP

------------

I Used partition magic (v8 ) to Shrink HDD2 partitions to leave an EMPTY space (40gb).

ie  NTFS Data Part|XP  Page file Part| 40GB Empty space.
--------------------------

Rebooted and checked XP all ok....

THEN:

Booted live cd, Installed with GUIDED method to largest free space ( It selected HDD2 as expected)
All went well....

Chose to reboot ...

Grub menu came up - hit [ESC] - Only gave me the option to boot Ubuntu ( standard and recovery ) and a mem test.......

Booted ubuntu
edited the menu.lst for GRUB.
Added:- 

```
title Windows XP
root (hd0,1)     
makeactive
chainloader +1
```

Rebooted - Now it works....:KS
soooo


Did I do something weird? Is this a a bug?
I have read a LOT about a problem if you add windows AFTER Ubuntu , but this was a classical - migrating from Windows- dual boot install.....

It works now but I am curious.......and - if this is a 'bug' should I report it ?- dunno how that works - do I need corroboration by a third party or...?
 ):P

---

### Post by tchoklat on 2007-08-01
The install may not have seen XP on your other drive. The install does allow you to repartition with GPartEd which is preferable!


T

---

### Post by OZTack on 2007-08-01
> **tchoklat said:**
> The install may not have seen XP on your other drive. The install does allow you to repartition with GPartEd which is preferable!


Absolutely - question is why?.... I specifically did NOT create a new partition with Partition Magic because I didn't want to confuse the issue :) . I simply 'created' free space.... Not sure how that would cause a problem....?

The install DID identify both HDD and all old partitions during the install - just didn't add (?recognise) the orignal boot. I HAD assumed that the grub portion of the install would 'read' the old boot area to include those options.... But?

As I said - All working now :D just curious :???:


And wine country huh? That REALLY wine country or the Linux windows environment :lolflag:

---

