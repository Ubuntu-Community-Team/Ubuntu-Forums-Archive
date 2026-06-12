---
title: "Installed Ubuntu. Need to configure users"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by e_james on 2006-06-22
I have now installed Ubuntu 6.06 on my Toshiba Tecra S1 notebook in dual boot with Windows XP Pro. The installation overwrote Ubuntu 5.10 which had somehow got corrupted (I think it might have been a live CD). There are some surprising changes. First I couldn't log in. It never asked me to create a user and password. I fixed this by booting up as single user and creating a user. (Actually 2 users, 1 "system" both using the same password). Now I can log in. I'm using it right now to write this message. The problem is I can't configure anything e.g. wireless networking, mounting FAT32 drives. I keep getting told I'm not allowed to do it. The only passwords I know don't work.

This is one of the error messages

"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Obviously there's a lot I don't know. One step at a time. Can anyone assist please?

---

### Post by mlind on 2006-06-22
[QUOTE=e_james]I have now installed Ubuntu 6.06 on my Toshiba Tecra S1 notebook in dual boot with Windows XP Pro. The installation overwrote Ubuntu 5.10 which had somehow got corrupted (I think it might have been a live CD). There are some surprising changes. First I couldn't log in. It never asked me to create a user and password. I fixed this by booting up as single user and creating a user. (Actually 2 users, 1 "system" both using the same password). Now I can log in. I'm using it right now to write this message. The problem is I can't configure anything e.g. wireless networking, mounting FAT32 drives. I keep getting told I'm not allowed to do it. The only passwords I know don't work.

This is one of the error messages

"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Obviously there's a lot I don't know. One step at a time. Can anyone assist please?[/QUOTE]

boot as single user again and add yourself to group called **admin**

In fact, add yourself to all these groups
```

adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin

```

```

adduser *user group*

```

---

### Post by e_james on 2006-06-22
Before I reboot to do that, do these groups already exist or do I need to create them?

---

### Post by ProjectGod on 2006-06-22
they already exist.

---

### Post by mlind on 2006-06-22
you should see those groups by viewing /etc/group

```

less /etc/group

```

plugdev could be missing, but it should be if you installed from Dapper final.
(If it's missing, it's nothing to worry about)

---

### Post by e_james on 2006-06-22
The "admin" group was missing, so I created it as a system group and added my user to all the groups listed. I can now access my Windows drives but most of the System Administration functions are still blocked by the same error message. Obviously I am still mssing something. Any suggestions?

---

### Post by mlind on 2006-06-23
[QUOTE=e_james]The "admin" group was missing, so I created it as a system group and added my user to all the groups listed. I can now access my Windows drives but most of the System Administration functions are still blocked by the same error message. Obviously I am still mssing something. Any suggestions?[/QUOTE]

admin group was missing? hmm.. that's not normal. If I were you I would try reinstalling.

---

