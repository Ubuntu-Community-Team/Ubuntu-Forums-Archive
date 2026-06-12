---
title: "USing SCIM"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Abu_Dayya on 2007-12-18
Hi all

I was having problem typing with my native language (arabic), so I followed the directions on this link [https://help.ubuntu.com/community/SCIM?highlight=%28SCIM%29](https://help.ubuntu.com/community/SCIM?highlight=%28SCIM%29)

I got to the point where you should alter the "/etc/X11/xinit/xinput.d/scim" file. Then it says  "Save the file, then to be sure you won't be affected by previous configurations you can delete the folders .scim and .xinput in your home directory".

Now the arabic input works, but with the wrong locale. I want to use Arabic - Saudi Arabia, but its on Arabic - Egypt.

Later in that document, it says if you want to change the locale, you should edit the file #HOME/.scim/global and write your desired local. But I already removed the .scim directory. How can i edit it??


Sorry for the long post. I hope I was clear enough and you can understand and assist me..

---

### Post by Abu_Dayya on 2007-12-18
Anyone??

---

### Post by Abu_Dayya on 2007-12-18
Bump... Again

---

### Post by dstew on 2007-12-18
Look at [this]("http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html") for a way to change or restore your locale. A promising command is```
sudo dpkg-reconfigure locales
```

---

