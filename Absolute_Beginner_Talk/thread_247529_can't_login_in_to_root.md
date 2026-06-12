---
title: "can't login in to root"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by moricgaut on 2006-08-30
When i first installed Ubuntu it didn't ask me anything about root or changing the password it just told me to add a user i chose one and to give a password so that what i did. Now in the term when i need root priviledges to run some commands i can't it will say you need to be a root. So i would type in the the command "su" and type nothing for the password since it never asked me to change. So then it says ivalid password. So i have no clue what the password is for my root. All the installation ever told me to do was to addd a user with a password and nothing with a root. :confused:  Help Me. Thanks!

---

### Post by Papa-san on 2006-08-30
Try using 'sudo' rather than 'su'

Ubuntu doesn't use a separate root user. Just use the user and pw you used in install...

---

### Post by Kilz on 2006-08-30
You can also use gksudo to launch graphical applications as root. Like 
```
gksudo nautilus
```
This will open up the nautilus file manager as root, it makes moving files around in the file system a little easier that typing.

---

### Post by AirRaven on 2006-08-30
Small note- if you *must* enable the root account, it's easily done.

This command allows you to change it:

```
sudo passwd root
```

It's not reccomended, since sudo works so much better for most things. Even so- it's still an option.

You can also access a root terminal by typing [FONT="Courier New"]sudo su[/FONT] or [FONT="Courier New"]sudo -i[/FONT]. You can also enable it as an option in the Application GNOME menu using the [FONT="Courier New"]alacarte[/FONT] menu editor.

---

