---
title: "Little foxes spoil the vine!"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by penguin7009 on 2006-08-07
Hi all and thank you for this great place to use and discuss Ubuntu.  This was my first try at using Kubuntu.  I really like the looks of Kubuntu/Ubuntu and the amount of programs in the repository is mind boggling.  I keep running into small problems which keep me from actually using Kubuntu.

The first problem is the way in which Ubuntu uses the "root" system.  This root as user is really confusing and un needed.  The usual way Linux sets up a root folder with a root password and home account and then a user home and user account is light years easier than the Linspire/Ubuntu system.  If I wanted to add wallpaper to my /usr/share/wallpaper files I can usually just find the files>root files and type in the root password and copy the files I want.  I still haven't found a way to do that in Ubantu even after using the command line to make a root password.

The power management system is broken in Kubuntu.  One cannot start the screensaver system because the power management system does not work.  There are several other problems I can't seem to solve.  Ubuntu is a really great distro.  With the amount of money and all the folks working on the project I know that these problems will get solved in time.

Thanks for listening.

penguin7009

---

### Post by wombat20 on 2006-08-07
I am completely confused by your title, but anyway...

The command you're looking for is probably something like:
```

sudo cp ~/wallpaper/*.* /usr/share/wallpaper

```
You can also setup a SuperUser nautilus/konqueror window from your menus, but you should be pretty careful with it if you do.

The sudo system is intended to allow easy configuration without the business of logging out and in again, where people can end up running as root too often.  The following link may be helpful.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kebes on 2006-08-07
You can also use "sudo -s" to go into a superuser terminal for awhile. You can use this to avoid typing "sudo" over and over before each command.

You can create a superuser account in Ubuntu, in which case it becomes identical to any other Linux/Unix environment. However this is not really needed if your general user account has sudo privileges: just use "sudo" or "sudo -s" whenever required.

---

### Post by cantormath on 2006-08-07
you do not what to run as root all the time.  Its dangerous, especially if you are not weathered in linux.
Its not like windows, where its ok to log in as administrator all the time.

you only want to use root when you have to.  you dont want to be logging in as root into gnome.  If you need to use root, you can in terminal:

```
sudo <whatever command>
```
and when it asks for password, it that of the user you are logged into.  Note:only users added to admin can do this, so if you make another user after install, you need to take that into consideration. man sudo and check it out.
you can also
```
sudo -i
```
or
```
sudo -s
```
and you will be root in that terminal.  Check it
```
whoami
```
it should say root.

Another thing, you can edit the Applications menu, and click the root terminal icon to show up in system tools.

---

### Post by cantormath on 2006-08-07
to super user nautilus:
in terminal
```
laptop$:\ sudo nautilus
```

---

### Post by Tortanick on 2006-08-07
How risky is it really to be root, do you still have to click the wrong thing to do dammage?

---

### Post by bscbrit on 2006-08-07
While you are root the OS will not stop you from doing serious damage to installed software whereas, if you are only a user, the most you can do is damage your own user area.  If you did this as user, you can still get back in to correct the damage.  If you were root, you might end up having to re-install again with a loss of all of your data.  Sure, you will have to incorrectly tell the computer what to do to cause the damage but, if you are like every other user I've ever met, accidents do happen....

---

### Post by Tortanick on 2006-08-07
I was raised in the great redmond dustbowl, back home you just said sudo nautilus is perfectly safe :D Thank you.

---

