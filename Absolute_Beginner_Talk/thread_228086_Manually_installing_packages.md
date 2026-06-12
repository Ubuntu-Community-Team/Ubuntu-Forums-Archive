---
title: "Manually installing packages"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by That Other Guy on 2006-08-02
I've got another computer with Dapper already installed on it, but need to install madwifi to get it back on the network (it's in a new location, wifi only).  From this computer, I've downloaded the restricted-modules package suitable for the other computer, and checked the 'download only' box.

Now, where is the file saved?  I know I've read it before, but I can't seem to come up with the right search terms to get the proper answer now.

Once I get everything to the second computer, do I use "sudo dpkg -i package_name.deb" to install it?

Many thanks.

---

### Post by nixclusive on 2006-08-02
> **That Other Guy said:**
> I've got another computer with Dapper already installed on it, but need to install madwifi to get it back on the network (it's in a new location, wifi only).  From this computer, I've downloaded the restricted-modules package suitable for the other computer, and checked the 'download only' box.

Now, where is the file saved?  I know I've read it before, but I can't seem to come up with the right search terms to get the proper answer now.

Once I get everything to the second computer, do I use "sudo dpkg -i package_name.deb" to install it?

Many thanks.

The downloaded stuff is normally saved in:
/var/cache/apt/archives

If you can't find it there, try:
```
locate <query>
```

where <query> is the (full/partial) filename.

If that doesn't work, try:
```
slocate -U
locate <query>
```

If that doesn't work, goto packages.ubuntu.org and download the file from there.

---

### Post by Metacarpal on 2006-08-02
Downloaded packages are stored in /var/cache/apt/archives

and you have your code spot-on - or you can just double-click it and let the package manager take care of that for you. :D

---

### Post by That Other Guy on 2006-08-02
Thanks for the quick info.

---

