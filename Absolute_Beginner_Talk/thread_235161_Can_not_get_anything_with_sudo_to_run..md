---
title: "Can not get anything with sudo to run."
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by trident on 2006-08-12
DELETE.

Delete to the power of Pi.

---

### Post by taurus on 2006-08-12
What program did you try to run to get that error message?  Perhaps you don't belong to the right groups in /etc/group.  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here...

```

id

```
You need to belong to both adm & admin...

---

### Post by trident on 2006-08-12
System> Admin> Users and Groups

Output from ID (I'm the user BenT):

```
uid=1000(BenT) gid=100(users) groups=5(tty),6(disk),7(lp),10(uucp),20(dialout),21(fax),22(voice),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),60(games),100(users),102(lpadmin),106(usb),109(scanner),111(camera),1003(cdrecording)

```

---

### Post by taurus on 2006-08-12
> **trident said:**
> System> Admin> Users and Groups

Output from ID (I'm the user BenT):

```
uid=1000(BenT) gid=100(users) groups=5(tty),6(disk),7(lp),10(uucp),20(dialout),21(fax),22(voice),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),60(games),100(users),102(lpadmin),106(usb),109(scanner),111(camera),1003(cdrecording)

```
No wonder you can't run anything with sudo because you don't even belong to groups adm & admin?  Did you by any chance create BenT later (after the initial user when you installed it)?

You need to boot into recovery mode (from GRUB) and edit /etc/group to include BenT to both adm & admin...

```

nano /etc/group

```

---

### Post by trident on 2006-08-12
I did get into adm, but I can seemingly not find admin.

It's very odd.

---

### Post by taurus on 2006-08-12
Are you running Breezy or Dapper?  What is the ouput of this command, from a terminal, then?

```

more /etc/group

```

---

