---
title: "[SOLVED] RealPlayer really stuck on desktop"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by DaleFarrell on 2007-12-05
I've tried every command and suggestion I could find. I don't remember how got realplayer downloaded, but I cannot access the file in any way. This is the message I get " Cannot move "/home/dale...RealPlayer" to the trash because you do not have permissions to change it or its parent folder."  Or "you are not the owner, so you can't change these permissions. The package manager has no entry. I would be happy to just move it, rather than delete it. My install can't be so different from others who have said they deleted this app from their desktop.  Hayelp please.

---

### Post by thelatinist on 2007-12-05
```
sudo chown username:username filename
sudo rm -f filename 
```

---

### Post by DaleFarrell on 2007-12-05
I pasted in and typed in your script and got this    

dale@dale-laptop:~$ sudo chown username:username RealPlayer
chown: `username:username': invalid user

---

### Post by thelatinist on 2007-12-05
Sorry, I should have been clearer.  You should replace "username" with your actual user name.  Also, unless you are in the folder that contains the file RealPlayer, you will need to give the correct path to that file.

If you are trying to delete the file RealPlayer on the desktop and your username were 'dale' you would type:

```
sudo chown dale:dale ~/home/dale/Desktop/RealPlayer
sudo rm -f ~/home/dale/Desktop/RealPlayer

```

As always, change the paths and usernames to the actual path and username you need.

---

### Post by DaleFarrell on 2007-12-06
I was too tired to try those when they came in. Now, before I execute, so to speak, I have 4 questions.
1. The first line will navigate me to the proper directory-right?
2. The last line will remove the icon and the program from the desktop file-right?
3. If I wanted to only get ownership so I could move the app to somewhere beside the desktop
    what might be?
4. You have the second command neatly underneath the first. When I enter them can I simply add the second line after the first? I cant seem to get the blinking cursor to drop down.

I'm not learning this stuff fast enough. File navigation should be ultra basic. I bought the Ubuntu Linux Bible, but my impatience leads me to post questions instead of studying. My shame will get the better of me soon. Dale.

---

### Post by forestpixie on 2007-12-06
the first line gets you ownership
the 2nd removes it

if you want to do 3 - just do the first

4 - no you need to do each separately

be aware that using rm does exactly that - it won't be in trash - and generally it'll be gone with the wind

---

