---
title: "Samba client - need to be able to access Windows share with any username"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Abik0101 on 2007-11-23
First, I wud like to say that I did indeed do a lot of searching for an answer for my specific question, but in the end came up short :-(

Well, I have a specific question.

I can access Windows (I think it is samba share) shares using "smb://myusername@server/folder". It only asks for my password and the workgroup since I already supply my username in the command.


But sometimes, my friends need to login into the Windows share using my Ubuntu laptop with their own userID and password. They are not familiar with Ubuntu. So is there any way to create a clickable short-cut so that everytime I double-click on it, it will ask for both username and password to access the Windows share?

I hope my question gives all details clearly. If not, plz do ask and post in additional info. Thanks for advance for replies.

The attached picture shows how I want it to look.

---

### Post by The Cog on 2007-11-23
Have you tried not giving the username? I think that might work. e.g. 
smb://server/folder

---

### Post by Abik0101 on 2007-11-23
> **The Cog said:**
> Have you tried not giving the username? I think that might work. e.g. 
smb://server/folder

Thx for the reply. Yes I tried that. The share does open, but it does so without asking for any authentication and consequently there is only read-only access for everyone (including me).

---

### Post by The Cog on 2007-11-24
Ah. 
Perhaps getting the share administrator to remove the publuc readability?

But it occurs to me that other people on your laptop should have their own login to your lappy and therefore their own home directory in which they can have their own short-cut with their own username in it. If for some reason htey must use your login on the laptop, I'm out of ideas.

---

### Post by Abik0101 on 2007-11-24
@Cog, does not depend on whose login my lappy uses to start up (btw, it is my own lappy and only I can login). Anyway, this is my first thread here and I would like u to know that I really appreciate that u have been helpful. :-)

Sorry, should have mentioned more details earlier, stupid me. Here it goes...

1. It is a public share
2. **Using Windows to login to the share**
The windows share **always** asks for a password when anyone tries to access it from Windows XP using "**\\ip-address**". If I use my authentication, I can read/write my own folder in the share but will have only read-access to all my friends' shares.

If my friend logs into the share (from my lappy or from anywhere else) using his authentication, he can read-write his own folder, but can only read everyone else' folders. Accessing this share from WindowsXP without a password is not possible as it gives an authentication failed message.

3. **Using Ubuntu to login to the share**
Whereas in Ubuntu, all of this doesn't happen. What happens is just I posted in the first post. It does not even ask for any password if I use just smb://server/folder.

Somebody help...

---

### Post by The Cog on 2007-11-24
Yes, I think Gnome tries ot do you a favour and log in using Guest or whatever if you don't give a username. In this case, that's working against you. I don't know how to fix that.

I had a play with KDE recently, and I remember that the KDE file explorer called dolphin had slightly different behaviour. It will pull in a lot of dependencies, but you could try installing dolphin and see if that's any better for you. Dolphin also accepts URLs in the smb://... style.

---

### Post by Abik0101 on 2007-11-25
Ok, I will try installing and using an alternative file manager. But won't be doing it right now 'cos have exams till Nov end. :-(

Will try then and post the results.

---

