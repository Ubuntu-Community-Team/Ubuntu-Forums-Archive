---
title: "USB Pen Drive Permission Denied"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-11-06
I have been using a 512 MB USB pen drive on my Ubuntu desktop for months with no problems.  This weekend I plugged it into my Thinkpad, also running Ubuntu, and when I put it back  onto my desktop, the permissions have changed and I can't access it.  I can, however, see everything on the drive when plugged into the laptop.

Seems as if Ubuntu changed the permissions on me.  How can I get them changed back for the desktop PC??  Thanks.

---

### Post by jpeddicord on 2006-11-06
With the drive plugged in, press Alt+F2. Type **gksu nautilus** and then type your password. Once open, go to /media. Right-click on usbdisk, and select Properties. Go over to the Permissions tab, and enable writing for all users.
In Dapper, you can do this by checking the nine boxes for Owner, Group, and Other. In Edgy, use the dropdown menus to select Read and Write (or equivalent) for Owner, Group, and Other.

Hope this helps! :p 

Jacob

---

### Post by landsg on 2006-11-09
When I type "gksu nautilus" in terminal, I get error message:
GnomeUI Warning**: While conntecting to session manager: Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

Ubunutu then opens Nautilus, but when I try to change permissions, it doesn't allow it.

---

### Post by drkjstr on 2008-04-14
```

gksu nautilus

``` 
That is used after your press ATL+F2. If you want to run it from terminal the command is:
```

sudo nautilus --browser

```

---

