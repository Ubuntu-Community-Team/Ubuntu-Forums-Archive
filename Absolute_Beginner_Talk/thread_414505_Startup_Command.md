---
title: "Startup Command"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by an4rew on 2007-04-19
system>preferences>sessions

i've added Azureus,Gaim and a couple other programs there but i have left the command box empty because i don't know what to do.

Could anyone give me an example of how one of my apps should look because i want to be able to do this myself in future.

thanks.

---

### Post by Tundro Walker on 2007-04-19
> **an4rew said:**
> system>preferences>sessions

i've added Azureus,Gaim and a couple other programs there but i have left the command box empty because i don't know what to do.

Could anyone give me an example of how one of my apps should look because i want to be able to do this myself in future.

thanks.

Here's the way I'm reading your question (so if it doesn't seem like I'm making sense, you'll know why...hehe)...

What you're asking is not HOW to add startup entries to the sessions manager so they'll auto-boot...THAT you know.  What you want to know is what COMMANDS to enter so you can get the darn things to work, right?

Right!

Ok, Unbuntu follows the Linux generic file system setup, so a lot of the programs you want to run will get their executable files installed in a few, key locations that you can look in.  Plus, when the executables are in these specific locations, you should just be able to type in the single command and it'll work...you shouldn't have to change to the folder that has that command in it...

EG: the "/usr/bin" folder will have a lot of executables that all users should be able to run.  I installed "tilda", the quake-style console dropdown (which I use a lot...probably my most fav app).  In a terminal, all I have to type is "tilda" to get it to run, since it's located in "/usr/bin" along with tons of other useful stuff.

Folders you should check out are..

/usr/bin (common executables)
/usr/sbin (common system executables)
/bin (system-wide executables...I think you have to be root)
/sbin (system-wide executables that are usually for admin/system use only)
/opt (sometimes extra software installs itself here...EG: Swiftfox)

Folders to ignore are /etc, which mostly has config files, and /var, which mostly has system variables (so they system can remember what's going on in certain places).

I have yet to figure out a command to type in that would LIST ALL EXECUTABLES A USER CAN RUN.  (I'm capping that, in the hopes that it catches somebodies eye who knows an answer.)

Anyways, after looking in these areas, see if you can find the app you want to run.  Then, open a home terminal, and type in the command.  You should get the program running w/o needing to switch to its folder.  If it goes good, then just enter that command name into your "Command" field on the auto-starting app in your Sessions.

Hope this helps...

---

