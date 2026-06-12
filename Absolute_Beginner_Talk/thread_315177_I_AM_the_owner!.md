---
title: "I AM the owner!"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by mrSlush50 on 2006-12-08
How do I convince Ubuntu that I am the owner of every single file and folder on the entire hard drive all at the same time?  

I'm trying to delete/alter/move/modify stuff and I keep getting told "you are not the owner, so you can not edit these permissions"

apparently this is a very basic operation, but every thread I've found on it has contained some sort of explanation which flew completely over my head.

It's MY computer, why is it such a hassle to modify stuff on it?

---

### Post by bodhi.zazen on 2006-12-08
LOL welcome to Ubuntu.  This is done for security reasons. Linux != windows.

To perform these tasks use sudo. ```
sudo <command>
```To do them graphically```
gksudo nautilus
```

Changing the permissions system wide is not a good idea.

For more information: [sudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2006-12-08
Technically, you are only the owner of your own $HOME directory but root can remove or modify anything else on the system.  That's the why Unix is and you don't want to change the permissions around or you would get a one sick machine.  So, if you need to remove something that requires special permission, use the sudo command...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by seijuro on 2006-12-08
Also just a quick blerb for anyone who says well that's dumb of linux. Windows does blah blah blah... If you take a close look at the windows task list not all processes are run by the user either some are identified as system, etc. So you don't "own" everything in that instance either.

---

### Post by steve.horsley on 2006-12-08
Try to realise that you are performing two distinct roles. Most of the time, you are acting as a normal user, staying within your home directory. Occasionally, you take on the responsibilities of the administrator and then you "borrow" the identity of root (the unix administrator account). They are distinct roles, and it is unsafe for you to take on root's identity all the time.

Even MS have realised this (finally), and implementd the same sort of scheme in vista.

---

### Post by john262 on 2006-12-08
There are other Linux distros that are not nearly as restrictive as this. For instance, if you boot into Puppy Linux by default you are root and you have all root privileges. You don't even have to use a root password. You can set one up if you want to but by default the root password is blank.

I have used Puppy quite a bit and I haven't ever had any security problems operating all the time as root.

To be fair to Ubuntu however, I am also trying it out and it isn't that much of a hassle to adapt to it's scheme either.

But my point is that if you don't like the way Ubuntu is set up there are other distros to choose from.

---

### Post by pissedoffdude on 2006-12-08
you can just do a "sudo nautilus" (without quotes) but be careful because you can really mess up your machine

---

### Post by Old Pink on 2006-12-08
```
sudo chmodd 777 / -r
```^^ makes you root of all files.

***NOT ******RECOMMENDED***[I][B]/REFERENCE ONLY - ONLY USE IF YOU ARE EXTREMELY CONFIDENT IN YOUR KNOWLEDGE OF THE UBUNTU FILESYSTEM, AND WHAT YOU SHOULD/SHOULDN'T MESS WITH.

YOU HAVE BEEN WARNED - THIS WILL GIVE YOU _EXTREME_ POWER, I WON'T BE HELD RESPONSIBLE FOR ANY POWER YOU ABUSE.
[/B][/I]

---

### Post by taurus on 2006-12-08
> **Old Pink said:**
> ```
sudo chmodd 777 / -f
```^^ makes you root of all files.

***NOT RECCOMENDED***
:-k  :-k  :-k 

That sure one quick way to trash your system, making everything -rwxrwxrwx!!!

---

### Post by Old Pink on 2006-12-08
> **taurus said:**
> :-k  :-k  :-k 

That sure one quick way to trash your system, making everything -rwxrwxrwx!!!

It's only a quick way to destroy your system ***if ***you abuse the power you gain from the command. If you remain sensible and use the power only to avoid frequent password requests, then you'll be fine. :) 

I did say, I do NOT recommend it. At all. Just answering the question.

---

### Post by taurus on 2006-12-08
Personally, I wouldn't even post that command here at all because somebody sure will run it and find out later their system is behaving strangely...

---

### Post by Doug11 on 2006-12-08
As mentioned before, just a security issue. How many times in m$ did we think we were just cleaning up some files and the next thing you know your machine won't boot because one of these files you deleted is part of the boot process. I know it's happened to me.

---

### Post by Old Pink on 2006-12-08
> **taurus said:**
> Personally, I wouldn't even post that command here at all because somebody sure will run it and find out later their system is behaving strangely...Warning updated:> **Old Pink said:**
> [I][B]NOT RECOMMENDED/REFERENCE ONLY - ONLY USE IF YOU ARE EXTREMELY CONFIDENT IN YOUR KNOWLEDGE OF THE UBUNTU FILESYSTEM, AND WHAT YOU SHOULD/SHOULDN'T MESS WITH.

YOU HAVE BEEN WARNED - THIS WILL GIVE YOU _EXTREME_ POWER, I WON'T BE HELD RESPONSIBLE FOR ANY POWER YOU ABUSE.
[/B][/I]@Doug11: Cool avatar, nice to see another Pink Floyd fan. :)

---

