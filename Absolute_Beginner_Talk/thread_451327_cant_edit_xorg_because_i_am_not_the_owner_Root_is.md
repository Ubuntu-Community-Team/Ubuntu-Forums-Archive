---
title: "cant edit xorg because i am not the owner Root is"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by duderduderini on 2007-05-22
Hi Guys.
I think i figured how to edit xconfig to get my monitor to work BUT i cant edit it.
There are 2 users me and root. If i try to log in as root it says i cant log in from here
I go to "Administration- Users and groups" and it lets me set the password of root but thats about it.
i try to edit the file and it is read only?
Say what... how do i do this
Thanks

---

### Post by Bachstelze on 2007-05-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-05-22
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
And use the same password that you log in with.

---

### Post by SuperAndy on 2007-05-22
type sudo prefixing your command

so, if you were editing xorg.conf with nano, you would type:

```

sudo nano xorg.conf

```

You will be promted for your password, and then nano will be opened with root privelages. This sudo prefix works for any shell command at all.

Hope that helps.

---

### Post by LaRoza on 2007-05-22
gksudo should be used instead of sudo for graphical apps.

---

### Post by taurus on 2007-05-22
> **SuperAndy said:**
> 
```

sudo nano xorg.conf

```


But you need to be in /etc/X11 first before you can run that command or it will display a blank (new) file.

```
cd /etc/X11
sudo nano -Bw xorg.conf
```

---

### Post by duderduderini on 2007-05-23
Hi Guys
I figured it out finally.. it was obvious. Thanks for your patience
Nick

---

