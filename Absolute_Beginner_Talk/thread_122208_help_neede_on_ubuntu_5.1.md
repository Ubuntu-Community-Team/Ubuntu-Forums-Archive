---
title: "help neede on ubuntu 5.1"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by sunnydayzrback on 2006-01-27
I installed Ubuntu 5.1. There r five folders named sda1,sda5,sda6,sda7,sda8 on my desktop. When i open any of these it says that the folder could not be opened and it says that i dont have the permission. All these folders are mounted.In the properties\permissions the owner is set as root and i cant modify it as its not accessable. What should i do do make them readable ? Can i store any thing in those folders .

And I have an unpartioned ( free space ) on my hard disk now can i partition it in ubuntu os. If so plz tell me how..

and when I am opening sites like mail.yahoo.com its opening but when i am trying to sign into my mail the progress bar is going blank and its not signing in should i modify anything to sign in?

---

### Post by mlissner on 2006-01-27
You need to switch to the root account. Log out, and then log in with the username "root". I believe that will work, but it may not because of a strange thing Ubuntu does with disabling the root account by default.

If that doesn't work log in as you normally would, and open a terminal window. In the window that pops up, type in:
sudo su passwd

It will prompt you for a password. Enter it and hit enter (it won't show up on the screen). Enter it again, and go through the instructions at the beginning of this post, logging in as root, and using the password you just set up.

Once you're in as root, you can do much damage to your system. Deleting these folders from your desktop may just be that, but at least you'll be able to. Somebody else want to chime in with if it's a good idea to delete them, and why they are there?

---

### Post by amohanty on 2006-01-27
> All these folders are mounted.In the properties\permissions the owner is set as root and i cant modify it as its not accessable. What should i do do make them readable ? Can i store any thing in those folders .

Can you post the contents of /etc/fstab. To view in terminal:
> cat /etc/fstab

> And I have an unpartioned ( free space ) on my hard disk now can i partition it in ubuntu os. If so plz tell me how..

For gnome: GParted
For kde:     QtParted

HTH
AM

Edit: > Log out, and then log in with the username "root"
I would advise against it, as that can be dangerous as mentioned by mlissner. Moreover if it is a default install the root user is disabled. I would also advise against:
> sudo su passwd
until you get more used to Linux and are comfortable with it.

You can access these drives by just setting some things in /etc/fstab.

---

### Post by aysiu on 2006-01-27
See the fourth link of my signature, unless they're not Windows partitions.

If they're Linux partitions, that's a whole different story.

The terminal to type commands is Applications > Accessories > Terminal

---

### Post by mlissner on 2006-01-27
Personally, I found the sudo step very cumbersome when I was starting out. Again and again I wanted to do things as root, but had enough trouble figuring out the format of the terminal without putting in sudo everytime, and hoping for the best....hence my advice to disable it.

Seems to me that you learn very quickly that a lot of damage can be done while root, but you have to be pretty deliberate to really damage something while root, so really, I think it's a pretty safe way to operate when doing a couple of things.

Then again, I'm new to this too, and I try not to operate as root very often or for very long.

---

### Post by aysiu on 2006-01-27
[QUOTE=mlissner]Personally, I found the sudo step very cumbersome when I was starting out. Again and again I wanted to do things as root, but had enough trouble figuring out the format of the terminal without putting in sudo everytime, and hoping for the best....hence my advice to disable it.[/QUOTE] That's why you create a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` It's actually less cumbersome than logging out of normal user, logging in as root, logging out of root, and logging back in as normal user.

For KDE, the command is ```
kdesu konqueror
```

---

### Post by amohanty on 2006-01-27
> Seems to me that you learn very quickly that a lot of damage can be done while root, but you have to be pretty deliberate to really damage something while root, so really, I think it's a pretty safe way to operate when doing a couple of things.

Although I agree with that. I too have enabled the root user, however XDM login for root is disabled, and root can only login into tty0. 
The reason I advise against it is becuase if things blow up in a new user's face  too often, it might leave a bad taste. Also it establishes good user practise. Peruse the alt.comp.sysadmin's list long enough and you will soon realize that the number of very knowledgeable sysadmins doing an rm -rf / is far higher than one thinks :)

AM

---

### Post by mlissner on 2006-01-27
Yeah, I just...JUST....learned that a second ago while reading one of the links at the bottom of your posts. I've been using Ubuntu for hours each night for a couple months now, and I've JUST discovered that trick...

You're right, that does solve some effort of logging in and out, but something about just being able to do things as root when you need to is very nice.

Looks like we're going to have to agree to disagree.

---

### Post by amohanty on 2006-01-27
> Looks like we're going to have to agree to disagree.

Always room for that :)

---

### Post by aysiu on 2006-01-27
[QUOTE=mlissner]
You're right, that does solve some effort of logging in and out, but something about just being able to do things as root when you need to is very nice.[/QUOTE] For all intents and purposes, *gksudo nautilus* is being root when you need to be. To each her own, though. If root works for you, cool.

---

