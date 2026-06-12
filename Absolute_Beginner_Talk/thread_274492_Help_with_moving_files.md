---
title: "Help with moving files?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Stevo687 on 2006-10-09
Hey guys,

I am a new ubuntu user. I have a dual partitioned hard drive with windows XP and Ubuntu. To play a version of the game "openTTD" I just downloaded, I need to import some files into the games data directory from my windows version of the game. I have managed to move the files into my Ubuntu desktop, but it will not let me move the files into the game directory itself, saying I don't have "the permissions" to do this. The target folder for these files says I am not the owner, as I have just checked, and therfore I cannot write files into it. How do I change this setting i.e. make me the owner?

Thanks for your time!

---

### Post by kidders on 2006-10-09
Hi there,

Who *does* own the location you want to copy your stuff into? Taking ownership yourself might not necessarily be a smart idea!

If you want to find out more about ownership and permissions, check out the man pages on **chmod** and **chown**. There are various other related utilities like **su** & **sudo**, that let you perform actions as other users.

---

### Post by kkellner on 2006-10-09
the simplest way to do this I think is to open Nautilus with sudo priviliges:
open a terminal and type:

sudo nautilus

<edit>you will have to enter your password here also.
that should open nautilus, then browse to the folder you're trying to get things into and drag 'em in.

---

### Post by kidders on 2006-10-09
Perfect suggestion, provided you're happy to make the superuser the owner of the copied files. :-)

---

### Post by alpv on 2006-10-09
Hello,

Try the following:

1) Open a Terminal window (shell)
2) Move to the folder of the files that you need to move.
3) Enter the following:

"sudo mv <file1> <file2> <file3> <dir>"

where <file1> <file2> <file3> are the files that you need to move, and <dir> is the games data directory (use the full path).

4) A prompt will ask you for a password. Enter the one for your username.

The files should be moved.

-Andrés

---

### Post by jshamash66 on 2006-10-09
I'm a new user too, but I'm pretty sure you can solve your problem by opening terminal and typing
```
sudo mv <location of files> <target folder>
```
where <location of files> is the full path where the files are stored (ex. /home/user/folder) and <target folder> is where you want them to go (ex. /usr/lib/gamedir) or whatever. Hope this works :)

---

### Post by Stevo687 on 2006-10-09
Wow guys lightning respones, thank you. I have moved the files into the desired folder now :)

As for the ownership problem, I'll talk to the guy who built me the computer.

Thanks for all your help!

---

### Post by kidders on 2006-10-09
Hey again,

Differing ownerships aren't necessarily a problem ... after all, you're not meant to actually *own* very many of the files outside of your own home directory. Chances are, things are set up just the way they're meant to be.

Glad you solved your problem though :-)

---

