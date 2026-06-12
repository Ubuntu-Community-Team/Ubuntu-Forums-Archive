---
title: "Crash help ~"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-09-20
I crash my Ubuntu install !  I'm wondering if I can use the Live CD to retrive some of my files ?  I can see some of them, but I can't get them unless I'm root.  How do I do root on the live CD.  Help would be greatly appreciated ; )
Thanks ; )

---

### Post by stalker145 on 2007-09-20
> **MrKlean said:**
> I crash my Ubuntu install !  I'm wondering if I can use the Live CD to retrive some of my files ?  I can see some of them, but I can't get them unless I'm root.  How do I do root on the live CD.  Help would be greatly appreciated ; )
Thanks ; )

Depending on what exactly you want to do...

Just throw sudo in front of your desired command. For example:

Run Nautilus```
gksudo nautilus
```

To do root things in the terminal just throw that sudo in there. There should be no password required as it loads without you needing to log in, anyway.

Check back if you still need help.

---

### Post by Pumalite on 2007-09-20
Get a Knoppix Live CD (mounts the partitions automatically):[http://www.knoppix.org/](http://www.knoppix.org/)
Boot from it and backup /home, including 'Hidden Files' and all your data. Then do a clean install and restore home and your data.

---

### Post by MrKlean on 2007-09-20
Thanks guys.. I thot maybe I could do it from the Ubuntu Live CD; )  I'll try both to see which I like better ; )
Thanks again ; )

---

### Post by dn_desaku on 2007-09-20
If you dual boot Windows (I know, don't make fun of me), try installing the ext3 filesys on XP so you'll be able to recover you files via Windows. I don't think there is any Vista support 
(I wouldn't try, I think Vista is MS's worst creation ( although I use it ( I would install XP over it  but I can't get my hands on a copy and the PC is from Fry's ))). [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

