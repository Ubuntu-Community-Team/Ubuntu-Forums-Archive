---
title: "Editing xorg.conf for trackpad..."
date: 2008-01-16
forum: Apple Intel Users
---

### Post by Quidam Phoenix on 2008-01-16
I'm sorry for posting this for what probably seems like the billionth time, but my issue was a little different so hopefully someone can help me out.

I understand that I should type sudo gedit /etc/X11/xorg.conf, however when I do that all that happens is my cursor moves down a line in the terminal, nothing else. No editing to do, nothing.

I've tried gedit /etc/X11/xorg.conf, which opens the file, however without root priviledges.

Trying gksudo hasn't helped me either, I still am unable to edit and save the file.

???

On a side note, in System->Adminstration, I do not have a Users and Groups option. I know better than to spend my time trying to get the root account activated, as sudo should be fine if it'd work! I do want to create another account without admin priviledges, and even though I can still access it using the search feature, where did my lovely link go?!

Thanks, Tom.

---

### Post by xeth_delta on 2008-01-16
Try nano
```
sudo nano /etc/X11/xorg.conf
```

you save with Control-O and exit with Control-X

---

### Post by Quidam Phoenix on 2008-01-16
Somehow that isn't working.

First of all, i can substitute gedit for nano without issue right?

However, when I type that line, the terminal just moves my cursor down a line, with no text appearing, (Except the usual time date stuff, etc).

Pressing Ctrl + X does nothing here...

---

### Post by Quidam Phoenix on 2008-01-16
Edit: xorg.conf WILL display itself when I leave out sudo, for both nano and gedit. Somehow addng sudo to the beginning of the command makes nothing happen...

---

### Post by xeth_delta on 2008-01-16
In that case it does seem it is a problem with sudo. Are you a member of the sudoers group?

---

### Post by benanzo on 2008-01-17
Is your normal user allowed to do administrative tasks like open the Synaptic Package Manager or adjust the date and time?

Go to **System -> Administration -> Users and Groups**  You should be prompted for a password if you're doing this as your normal user.  If you're running as root then you wont be.
Select your normal user and choose **Properties** on the right.
Now on the **User Privileges** tab make sure that **Administer the system** is checked.  Then log out and back in.  That should be sufficient to give your normal user the ability to edit system files like xorg.conf.

Also, you could try just launching Nautilus as root and then navigating to the file you want to edit.  Normally you shouldn't have to do this but it's worth a try if you're having problems.

```
gksudo nautilus /etc/X11
```

That will launch a file window in the **/etc/X11** directory so you should be able to just double-click **xorg.conf** and edit it.

---

### Post by Quidam Phoenix on 2008-01-17
Well you're definitely right with sudo being the issue here. My account is in fact set up with admin priviledges, however even creating new accounts of this type and using them yielded the same result with sudo-ing in a terminal window.

In the end, seeing as it was a fresh installation, I just reinstalled it (this time not updating with a prepackaged kernel for my macbook), and haven't had any issues since. sudo gedit /etc/X11/xorg.conf works like a charm.

Unlike the instructions for Santa Rosa Macbooks, the volume, backlight, etc, keys do work properly. I could care less if I can't press Function+F5 (or F6, whatever!) to get a numpad.

Thanks to all who tried to help.

-Tom.

---

