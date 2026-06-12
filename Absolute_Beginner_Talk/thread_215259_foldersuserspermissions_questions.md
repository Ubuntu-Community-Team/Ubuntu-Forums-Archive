---
title: "folders/users/permissions questions"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by drarem on 2006-07-13
i have a question on users and permissions - I have a /home/gwendell set up, along with the default install - kubuntu.

Where should I be placing programs, files, etc (like ET, QUAKE4, etc) - the /usr/.. or the /home/gwendell/.. ?

What permissions do i need to be wary of giving?

I know the instructions generally say install in /usr/local/games... what is the point of my having a gwendell user?  Extra security or just space?  Or should I install in the user directory and leave the default usr stuff alone?  

If it helps, I'll be running apache2/mysql/php with opened ports from time to time.

Thanks.

---

### Post by TLE on 2006-07-13
The short explanation is that it is a multiuser system, therefore:
- your home folder is for *your users* files
- everything outside of your home folder is for stuff that should be available to all users

If your are the only user of the system for some things it won't matter, but IMHO it is worth sticking with the designed structure. So I think you should install your games in one of the system folders you mentioned, and keep only personal files and personal settings in your home folder.

Regarding permissions it is the same deal as above. You may (I don't know) be able to install something in your home folder with standard user permissions, but I don't think it is a goos idea. Istalling software in one of the system folders for every user to use is an administrators task and so you need to get root permissions to do so. But you only take the permissions while you perform the task, so you needn't be worried about sequrity if that was what you meant.

Hope this is sort of clear, otherwise repost and we'll figure it out.
Regards TLE

---

### Post by aysiu on 2006-07-13
What's the point of having a C:\Documents and Settings\gwendell in Windows or a /Users/gwendell in Mac OS X?

Every system has users. There are user files, and there are system files.

---

