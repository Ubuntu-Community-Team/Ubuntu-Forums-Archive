---
title: "Where is smbmnt?"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Bjoern on 2006-01-06
Hello,

I'd like to mount a Windows Share from Ubuntu. I think smbmnt would be the tool to use? However, I can't find it on the system. The Samba package is installed. Also, I was able to access the share from within Nautilus, so something like smbmnt seems to be available. But I need to link it into my file system, a Nautilus share is not enough.

Many thanks in advance!


Bjoern

---

### Post by bjourne on 2006-01-07
Install smbfs and you get smbmount and smbumount

---

### Post by derspiess on 2006-03-12
Hi, can someone tell me exactly what I need to do to install smbfs?

TIA,
derspiess

---

### Post by taurus on 2006-03-12
```

sudo apt-get install samba

```

---

### Post by howie_23 on 2006-03-19
Whenever I go to install smbfs I get an error message that says:

package smbfs is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source
E: package smbfs has no installation candidate

I think I already have Samba installed.  I'm a n00b at Linux so sorry if I'm asking a stupid or obvious question.

---

### Post by taurus on 2006-03-19
If you already have samba on your machine, then just configure /etc/samba/smb.conf so you can mount your Windows!!!

---

### Post by bobpaul on 2006-03-22
[QUOTE=taurus]If you already have samba on your machine, then just configure /etc/samba/smb.conf so you can mount your Windows!!![/QUOTE]

No, that's wrong. You can't "mount your Windows!!!!" unless you have smbfs install. With only samba you can use the Gnome VFS (which will utilize smbclient) to browse samba shares, but if you actually want to mount a network share to a local folder using the mount command you need smbfs. I just encountered this problem today, and apt-get installing smbfs was the answer.

howie_23: you probably need to enable universe. In Breezy, do
[LIST]
[*]from the Applications menu: Add Applications
[*]from settings Settings: Repositories
[*]Click Settings Button
[*]Mark "Show disabled software sources"
[*]Mark all of the repository checkboxes.
[*]Click OK
[/LIST]

then try again. Remember, you don't need smbfs unless you want to mount rather than just browse with nautilus (eg Network from the Places menu)

---

