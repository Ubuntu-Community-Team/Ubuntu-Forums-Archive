---
title: "[SOLVED] Moving folders and files from one user's home to another's"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-31
When I installed Ubuntu, I only set up one user (as the administrator): "Owner". Now I've been experimenting with the multiple users functions: something I never have bothered to set up/deal with  on previous systems. So now I have set up two more users: "Me" and "Anonymous". Mainly so my name was the default for high scores in Tetravex ;) 

All of my music, files, etc., were under Owner - and I wanted to move them all from "Owner" to "Me". I was under the impression before I began this that the main administrator you set up on install, "Owner" (in my case) could do anything to anybody's files, but I guess I was wrong. 

When I tried moving the files from and logged in as Owner to Me, I didn't have permissions for Me. So I logged into Me and changed the permissions on the Me folder to read & write for everybody (for the time being) and went to Owner to move the folders and files from there. When I dragged everything I wanted from Owner to Me (music, etc.) it copied them instead of moving them, which kind of sucks because it is a lot of data. So I moved the copies still on Owner to the trash, and logged into Me.

Well, all the folders and files were there now but they are all still owned by Owner.

1. Am I missing the much simpler (and still within the GUI) method of doing this?
2. Is this the recommended way to handle something like music? i.e., in the future I may want access to the music folder from multiple users...
3. How do I change the ownership of those folders and files from Owner to Me?

On a side note now I get an error message on logging in talking about a file being ignored, it should be owned by the owner and have 644 permissions, etc. I assume this will be fixed once I change all the permissions back to default.

On another side note Ubuntu has crashed for the first time in all of this multiple user business, when I logged in from switch user, I put in my password, then I came to another screen (off of the screensaver) asking for my password, entered it, and it crashed. Earlier, when I had logged out from a user, instead of bringing me to the login screen, it just brought up a black screen with a - at the top left, CTRL+ALT+DEL got me out of that one though (guess it works here too sometimes).

---

### Post by Pragmatist on 2007-07-31
You can nearly always copy from anywhere to anywhere using **sudo**:
```
sudo cp -rf /home/owner /home/me
```

Whoops!  You want to move them:
```
sudo mv /home/owner /home/me
```

---

### Post by keyboardashtray on 2007-07-31
> **Pragmatist said:**
> You can nearly always copy from anywhere to anywhere using **sudo**:
```
sudo cp -rf /home/owner /home/me
```

Whoops!  You want to move them:
```
sudo mv /home/owner /home/me
```

But will that transfer ownership as well?

---

### Post by keyboardashtray on 2007-07-31
Should I just undo everything? Should I just restore the copies in the Trash back to Owner, and delete all the files from Me?

Or, if I create the names of the folders I want from Me in Me, and just copy or move the files from Owner into those folders, will Me then own the files?

---

### Post by aysiu on 2007-07-31
```
sudo mv /home/owner/* /home/me/
sudo chown -R me:me /home/me
``` would do it.

You can also press Alt-F2 and type ```
gksudo nautilus
``` and this will allow you to drag and drop files as you wish. Don't forget to change ownership on them as well.

---

### Post by Pragmatist on 2007-07-31
1.) Unless you know what your doing, or have a very good reason, you shouldn't be playing with multiple users.  Having a list of meaningless users to make the high-score list of a game boost your ego is not a good reason. :)

2.) I don't know how to manage users from a GUI, but I do know how from a command-line.

3.) Ubuntu does not create a root, or administrator, account when you install it.  "Owner" is not an administrator.  To have administrator privileges, you use a command called "sudo" (or "gksudo" if the command runs a GUI application.)

4.) There are many excellent tutorials on managing users.  Read one and it will make your life a lot easier.

5.) You can easily change ownership with the "chown" command.

Resources:
Man Pages--You read these by typing "man" in front of the command you want to know more about.  Look at the man pages for:
useradd userdel chmod chown chgrp

Find more resources by reading the thread "how to help yourself" linked from my signature.

---

### Post by Pragmatist on 2007-07-31
> **aysiu said:**
> ```
**sudo mv /home/owner/* /home/me/**
sudo chown -R me:me /home/me
``` would do it.

[B]sudo mv /home/owner/* /home/me/

[/B]Be aware that this will move all the files in /home/owner to /home/me  whereas:

**sudo mv /home/owner /home/me**
 
will make a directory in /home/me called owner  You will have a directory /home/me/owner  and it is identical in contents to the folder that was previously called /home/owner

This is an important difference.  If you have a lot of files in /home/owner they will be scattered all over /home/me rather than in a separate directory.

---

### Post by aysiu on 2007-07-31
I thought the idea *was* to move all the files to /home/me, as opposed to /home/me/owner

It's hard to tell from the OP's post, though.

---

### Post by keyboardashtray on 2007-07-31
> **aysiu said:**
> ```
sudo mv /home/owner/* /home/me/
sudo chown -R me:me /home/me
``` would do it.

You can also press Alt-F2 and type ```
gksudo nautilus
``` and this will allow you to drag and drop files as you wish. Don't forget to change ownership on them as well.

Thank you Aysiu! Chown did the trick - I had to break my pledge to always find the non-console alternative, but I guess that was inevitable :)

---

### Post by keyboardashtray on 2007-07-31
> **Pragmatist said:**
> 1.) Unless you know what your doing, or have a very good reason, you shouldn't be playing with multiple users.  Having a list of meaningless users to make the high-score list of a game boost your ego is not a good reason. :)

2.) I don't know how to manage users from a GUI, but I do know how from a command-line.

3.) Ubuntu does not create a root, or administrator, account when you install it.  "Owner" is not an administrator.  To have administrator privileges, you use a command called "sudo" (or "gksudo" if the command runs a GUI application.)

4.) There are many excellent tutorials on managing users.  Read one and it will make your life a lot easier.

5.) You can easily change ownership with the "chown" command.

Resources:
Man Pages--You read these by typing "man" in front of the command you want to know more about.  Look at the man pages for:
useradd userdel chmod chown chgrp

Find more resources by reading the thread "how to help yourself" linked from my signature.

Well, the reason I've been toying with it is twofold - one, that I wanted to create a non-admin option on here for security reasons, and the other is that I'm possibly going to be putting Ubuntu on friends/relatives computers, who may want multiple users, and I want to get through the experimenting on my PC so I know what I'm doing on theirs.

"I only have to stay one lesson ahead of the student." M. Simpson

---

### Post by aysiu on 2007-07-31
> **keyboardashtray said:**
> Thank you Aysiu! Chown did the trick - I had to break my pledge to always find the non-console alternative, but I guess that was inevitable :)
Well, if you create a "browse as root" icon, you won't have to use the terminal. Just set up an icon for the command ```
gksudo nautilus
``` right-click on the folder, and you should be able to change the ownership through the GUI.

---

### Post by keyboardashtray on 2007-07-31
> **Pragmatist said:**
> [B]sudo mv /home/owner/* /home/me/

[/B]Be aware that this will move all the files in /home/owner to /home/me  whereas:

**sudo mv /home/owner /home/me**
 
will make a directory in /home/me called owner  You will have a directory /home/me/owner  and it is identical in contents to the folder that was previously called /home/owner

This is an important difference.  If you have a lot of files in /home/owner they will be scattered all over /home/me rather than in a separate directory.

Thank you for clarifying this Pragmatist, I did want to move them to /home/me but it is always good to know more - I guess my question title should have focused on ownership more than moving, since I had already moved them. It was more, how do I move them right (next time)? 

But anyway, I've moved them all my original screwed up way and just changed the owner, that takes care of it for me.

---

### Post by keyboardashtray on 2007-07-31
> **aysiu said:**
> Well, if you create a "browse as root" icon, you won't have to use the terminal. Just set up an icon for the command ```
gksudo nautilus
``` right-click on the folder, and you should be able to change the ownership through the GUI.

Excellent - I'll keep that in mind for next time.

---

