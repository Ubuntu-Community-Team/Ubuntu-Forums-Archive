---
title: "Trash Bin"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-04-22
when i delete the trash it doesnt show up on the trash bin i have on the desktop. where does it go and what should i do to get it to work again?

---

### Post by aysiu on 2007-04-22
Can  you supply some more information?

For starters, are you using Ubuntu, Kubuntu, or Xubuntu?

---

### Post by heimo on 2007-04-22
> **Benifited said:**
> when i delete the trash it doesnt show up on the trash bin i have on the desktop. where does it go and what should i do to get it to work again?

I don't get the question. When you delete what? Files? Or remove trashcan icon from desktop or panel?

---

### Post by josephus on 2007-04-22
if you are deleting files with the command line (e.g. rm <filename>) it doesn't go into trash bin, and those files can not be undeleted.

---

### Post by Benifited on 2007-04-23
by trash i meant files sry for not being more clear

---

### Post by nazish on 2007-04-23
hi benifited,

I think you have enabled the bypass the delete commandin your nautilus file manager. Let me help you restore things to normal

1. open you home folder
2. click on edit and goto preferences
3. goto behavior tab
4. In the last row labeled TRASH click the first choice which lets nautilus ask you for conformation before you delete a file

another reason why this problem occurs is that you login as one user and then logout and login as another user and then check trash. In linux each user has his own trash bin and is located at /home/username/.Trash/ check there for every user

if the problem is not still solved let me know
bye
regards,
naz

---

### Post by DancingSun on 2007-04-23
I think Benifited meant that he moved files to the trash bin, but the trash bin appears to be empty, ie., the icon is still an empty trash bin.

I have a similar problem, but I can open the the Trash Bin in Nautilus by clicking on the Trash Bin icon and still see the files that I just moved-to-trash, and empty them from there.

---

### Post by Benifited on 2007-04-23
> **DancingSun said:**
> I think Benifited meant that he moved files to the trash bin, but the trash bin appears to be empty, ie., the icon is still an empty trash bin.

I have a similar problem, but I can open the the Trash Bin in Nautilus by clicking on the Trash Bin icon and still see the files that I just moved-to-trash, and empty them from there.

yes this is what i meant but when i go to the trash bin there is nuttin there

---

### Post by ramjet_1953 on 2007-04-23
How did you get the trash bin onto the desktop?

If you just put the icon there it won't work.

Type in a terminal [COLOR="Red"]gconf-editor[/COLOR]

The Configuration Editor window should open.

Navigate the tree to:[COLOR="Blue"] apps>nautilus>desktop[/COLOR]

In the right panel you should see a list of things that can be made visible on the desktop.

Click on the button for [COLOR="Red"]Trash Icon Visible[/COLOR].

Viola! You now have a working trash can on the desktop.

Regards,
Roger :cool:

---

### Post by josephus on 2007-04-23
I think that your problem related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247)

if you go into ~/.Trash do you see your deleted files there?

---

### Post by Benifited on 2007-04-24
> **ramjet_1953 said:**
> How did you get the trash bin onto the desktop?

If you just put the icon there it won't work.

Type in a terminal [COLOR="Red"]gconf-editor[/COLOR]

The Configuration Editor window should open.

Navigate the tree to:[COLOR="Blue"] apps>nautilus>desktop[/COLOR]

In the right panel you should see a list of things that can be made visible on the desktop.

Click on the button for [COLOR="Red"]Trash Icon Visible[/COLOR].

Viola! You now have a working trash can on the desktop.

Regards,
Roger :cool:

hey thx alot bro it work :)

---

