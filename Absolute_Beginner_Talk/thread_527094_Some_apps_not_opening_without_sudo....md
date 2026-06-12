---
title: "Some apps not opening without sudo..."
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by eyemou on 2007-08-16
(EDIT: I am running KDE/Kubuntu Feisty... not GNOME/Ubuntu. I forgot to mention that!)

For some reason, when I attempt to open some apps (Amarok and adept_manager spring to mind), via clicking on the task bar/kicker shortcut I have always been using, they aren't opening. The cursor changes to the bouncing app. icon, but after a while, nothing happens.

I looked at the running processes, and lo and behold, adept_manger, and amarok/amarokapp ARE running. However, they are not opening on the desktop.

Now, when I open a konsole window, and run either amarok or adept_manager from the command line, via sudo, it works. Huh?

What's weird is that those are the only two apps that I believe I have started experiencing this with. Others that I commonly use (firefox, ktorrent, konsole, kate), open with no problems whatsoever.

Any ideas?

Could this be related to a previous issue that I recovered from in where I inadvertantly deleted my main system/user account and had to re-add it via recovery mode? After re-adding my user, I added it to the group 'admin'. 

Could this be a groups issue? Are there any other groups that my main account should belong to, in addition to 'admin' and the group named for that particular account?

Thanks!

---

### Post by MaximB on 2007-08-16
it IS related !
If I understand you right, you have deleted your user account right ?
when you recreated it under the same name (or not, doesn't matter) you got a new user ID.
if you remember your old user id number you could change it to the new user and it will hopefully work.

if it was your first user after the "root" user your UID should be 1000.
try changing it in the user management in the advanced options.

---

### Post by Chaotic Thought on 2007-08-16
It sounds like a permissions problem, but it's easiest to diagnose from trying to run them from a terminal. Go to a terminal window and run them (but not as root). Does it give you an error message of some sort? This will lead you to your permissions problem.

---

### Post by eyemou on 2007-08-16
Thanks for the reply. I'll check when I get home form work, but I believe that the UIDs are the same - I deleted UID 1000, and that was the first UID available when I re-added the user. 

Are there any particular groups that I should be looking at?

For example, user 'rich' (the account in question), is presently a member of the groups 'rich' (by default) and 'admin' (I added it after re-creating the account).

Now, when I first set up the system, I am certain that I added the account to other groups, but cannot for the life of me remember which - and I am not sure if the system did so during the install.

(I've since started keeping notes about most of what I do. I wish I had at the time...)

Thanks!

---

### Post by eyemou on 2007-08-16
> **Chaotic Thought said:**
> It sounds like a permissions problem, but it's easiest to diagnose from trying to run them from a terminal. Go to a terminal window and run them (but not as root). Does it give you an error message of some sort? This will lead you to your permissions problem.

I'm not in front of that machine right now, but the error message in this thread:

[http://ubuntuforums.org/showthread.php?t=527089](http://ubuntuforums.org/showthread.php?t=527089)

Sounds an awful lot like what I was getting when trying to run it in the konsole (without sudo). I just wasn't able to determine what the error was, exactly...

---

### Post by Chaotic Thought on 2007-08-17
Uh oh, KDE errors... that reminds me one thing I definitely don't like about KDE apps in general. Amarok is great when it works, but when it doesn't, the error messages are incomprehinsible. Like one of the posters said, no one knows why that happens, but to try logging out and back in.

---

