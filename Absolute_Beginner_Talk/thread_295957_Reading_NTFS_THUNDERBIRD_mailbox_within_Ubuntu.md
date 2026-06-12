---
title: "Reading NTFS THUNDERBIRD mailbox within Ubuntu?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Shlomir on 2006-11-08
Hi there,

I have a dual-boot machine running WinXP and Ubuntu. I use THUNDERBIRD as my main mail client. Is it possible for me to access my Thunderbird mailboxes that are sittingon my NTFS partitions within the Ubuntu EX3 session using the Linux THUNDERBIRD client? I tried it, but it seems to hang...

Cheers

Shlomir

---

### Post by aysiu on 2006-11-08
Yes, but you won't be able to modify them--just read them.

[Mount NTFS as read-only](http://www.psychocats.net/ubuntu/mountwindows)
[Howto Thunderbird/Firefox profile share XP & Dapper](http://ubuntuforums.org/showthread.php?t=203524&highlight=howto+share+thunderbird)

---

### Post by Shlomir on 2006-11-09
Thanks :mrgreen:

---

### Post by Shlomir on 2006-11-09
Sorry to reply so hastily...I trued these links...Firstly I redid the mount setting in fstab to allow RO access to the NTFS drives...This worked.. HOWEVER the problem still remain in Linux THUNDERBIRD...When I go into Propertie..Server Setting for my account and select the LOCAL DIRECTORY I point it to this newly created xe3-to-NTFS share-point that point to the NTFS share. OK.

The foldersd appear, however when I try to access them the load circle just gets lost in limbo and cannot read the mailboxes...any tips?

Many Thanks

Shlomir Bareket](*,)

---

