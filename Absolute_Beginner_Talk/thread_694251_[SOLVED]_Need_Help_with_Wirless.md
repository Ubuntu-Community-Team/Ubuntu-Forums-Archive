---
title: "[SOLVED] Need Help with Wirless"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-02-11
I can not get my wireless card to be seen in network settings.  
I have an acer spire 5100-5300 with an atheros wireless card.
I have tried to get madwifi to work but I cannot.  I really don't know what I am doing please help [and if you could write in a way a preschooler would understand I would appreciate it]

---

### Post by LookTJ on 2008-02-11
Type:
```
lspci
```
and post the name of the card.

---

### Post by oedha on 2008-02-11
what type of atheros.......5007 can be done by ndiswrapper

---

### Post by OldNewb on 2008-02-11
this came up when I typed lspci

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

the sticker says it is AR5BXB63

---

### Post by OldNewb on 2008-02-11
...

---

### Post by oedha on 2008-02-11
wait...i'll look for AR5BXB63......in google??
what's the output of :==> sudo lshw -short -class network ?
maybe it can tell the atheros type

---

### Post by OldNewb on 2008-02-11
H/W path             Device     Class       Description
=======================================================
/0/100/4/0                      network     Atheros Communications, Inc.
/0/100/14.4/1        eth0       network     RTL-8139/8139C/8139C+

---

### Post by oedha on 2008-02-12
maybe this link will help you
[http://ubuntuforums.org/showthread.php?t=679649&highlight=atheros](http://ubuntuforums.org/showthread.php?t=679649&highlight=atheros)

---

### Post by OldNewb on 2008-02-13
Thanks for the help.

This link and the one you put up helped alot

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by oedha on 2008-02-13
done ?
is this solved ?
if yes...could you please scroll up and click on thread tool...then mark this as solved...thank you :)

---

