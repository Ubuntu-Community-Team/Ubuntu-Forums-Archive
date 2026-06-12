---
title: "admin password?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by antony11 on 2007-11-04
Ok I want to edit a file but it tells me its read only. The only way to reset the permissions is as admin. So what I want to know is what is the admin username and password? Ubuntu doesn't give the option of setting it up when installing?

---

### Post by qpieus on 2007-11-04
the admin pw is the same as your user pw.

---

### Post by taurus on 2007-11-04
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Perfect Storm on 2007-11-04
if it's text file you need to edit, you can do this;

```
sudo nano <path>/<file>
```

example:
sudo nano /etc/X11/xorg.conf

---

### Post by antony11 on 2007-11-04
thanks folk. What I want to do is edit my smb.conf file in a hope that I can get this box talking to the rest of my network as Im convinced that my problem is just a lack of understanding of the system. I have noticed that in the smb.conf file  the domain/workgroup name is not the same as   that used for my network hence the reason for wanting to change it.

Unless of course there is a much easier way to set this all up?

---

### Post by Perfect Storm on 2007-11-04
Is this the one?

```
sudo nano /usr/share/samba/smb.conf
```

[ctrl]+[o] = save
[ctrl]+[x] = exit

---

### Post by antony11 on 2007-11-04
the command line Ive used (since reviewing the article mentioned above) is:

sudo gedit /etc/samba/smb.conf

I presume this is the one I want or is it the one mentioned on post above?

---

### Post by Perfect Storm on 2007-11-04
Yes.

---

### Post by antony11 on 2007-11-04
Umm! Im just looking at the file /etc/samba/smb.conf and its a very BIG file. Most of it is commented out so just what do I need in there and what dont I?

---

