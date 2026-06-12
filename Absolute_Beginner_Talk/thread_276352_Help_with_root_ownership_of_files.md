---
title: "Help with root ownership of files"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Buickman on 2006-10-12
I'm not just a newbie, I'm an extreme newbie. Started off with DOS in the 80s, and now I feel like I'm relearning all over again.

Anyway, I just installed ubuntu on this system. Actually, this is about the 5th install. What I'm trying to do is dive right into games, in particular Doom 3 and Quake 4. If successful, then I can make the complete transition from XP. I found some directions and an installer. Wish I could remember where, it was during the 4th install and didn't save the link. The file name is;

quake4-linux-1.3-2.x86.run

The directions on the site recommended installing in /usr/local/games/quake4/q4base

I get to /usr/local/games and it will not let me create anything due to root having ownership. I have SUSE linux installed on another system which will allow me to do these things. I am able to log on as root, but at that point I'm stuck, and not sure what to do from there other than stare at the blinking cursor.

How do I change ownership of files from root to my primary user (me)?

Also, as a second problem, when I go to either restart or shutdown, the system seems to start doing just that, the screen goes blank, then it just seems to hang there. It didn't do this on the previous installs, just this last one. Any advice with that would also be helpful.

Thanks.

---

### Post by UnknownVariable on 2006-10-12
Use the **chown** command if you want to change ownership of a folder / files to a different user or group.

I don't believe that's recommended however, as one of the points of linux is to have a separated system / personal folder hiearchy.

If you're just creating the folder, or extracting files, navigate through the directories in the terminal.

**cd** changes your directory.
**dir** lists folders and files in the current directory.
**mkdir** creates a directory.
**rm** removes directories / files.
**tar** untars files.

Use **man cd** (or replace **cd** with another command) to read the manual about the command. Use the up and down arrows to scroll, and page up / page down to scroll by pages. To exit the manual and continue with your commands, press **q**.

:)

---

### Post by aysiu on 2006-10-12
Please do not change ownership of anything. You're likely to render your system unusable--those ownerships and permissions are there for a reason.

This will explain what you should do:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Buickman on 2006-10-12
Thanks.

Actually, I think I'm getting way ahead of myself. I'm going to slow down and start reading more of these threads. I've got one of my systems on Suse Linux right now, and I want to get this one (my gamer) setup on ubantu, but I know I need to get everything right, like the drivers and such. I've just got more reading to do. Like I said, this system's sole purpose in life is to be a gamer.

P4 Prescott 630 3.0G, o/c to 3.8 (water)
Asus P5P800SE MB (I need a better moboard, but this is a great overclocker)
ATI X850XT agp

Any links/advice for this thing would be great.


Eventually I'll get the wife's converted over. She's gonna hate my guts when it happens. ;)

---

