---
title: "New Linux Convert"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by Assneck on 2005-09-13
Howdy, I recently got disgusted with Windows XP and decided to try Linux.  I haven't thrown the Winblows out the window yet, still doing the dual boot thing, but I definitely like the Linux so far....anyway now to business

I've got no idea what I'm doing in Linux.  I've had a semester of C++ 5 years ago and I know my way around windows backwards and frontwards tho.  Currently I'm trying to install Quake 3 Arena onto the Linux partition and I'm lost.  So far I've downloaded the demo1.11 file with extension .x86.gz.sh and the point release to 1.32 with extension .86x.ru.  I also have a 1.17 download with extension .sit.  I've got absolutely no idea how to install any of these packets.  I've also got the Q3A install CD for Windows.  Is there a specific CD i need for Linux or do i have the correct combination?  

Keep in mind i'm used to autorun and installshield....

What do I need to do?

EDIT: BTW i'm using Ubuntu, GNOME 2.12.0

---

### Post by poofyhairguy on 2005-09-13
This thread should still apply:

[http://ubuntuforums.org/showthread.php?t=63906&highlight=quake](http://ubuntuforums.org/showthread.php?t=63906&highlight=quake)

I have never tried but I hope you get it to work.

---

### Post by Assneck on 2005-09-13
[QUOTE=poofyhairguy]This thread should still apply:

[http://ubuntuforums.org/showthread.php?t=63906&highlight=quake](http://ubuntuforums.org/showthread.php?t=63906&highlight=quake)

I have never tried but I hope you get it to work.[/QUOTE]

hmm ok thanks for the help, now I'm getting a weird error.

chmod 777 /home/mike/linuxq3demo-1.11-6.x86.gz.sh
chmod: cannot access `/home/mike/linuxq3demo-1.11-6.x86.gz.sh': No such file or directory

Am i typing the path wrong or what? I put it in the home/mike/ directory.

I get either that or a "Permission Denied" when I use the sudo command.

---

### Post by Nequeo on 2005-09-13
It's probably just a silly typo. Try using 'tab completion'.

Type:

chmod 777 /home/mike/linux

Then just hit tab a few times. It should show you a list of all files beginning with 'linux' in that directory. Add in a couple more letters, and hit tab again. Once you've narrowed it down to only one possibility, it will fill in the rest of the file-name for you automatically.

On the other hand, if all it does is beep at you, then there aren't any files beginning with 'linux' in /home/mike.

Try using 'ls' (short for 'list') to see the contents of a directory.

And with that out the way, welcome to Ubuntu! As long as you're not afeared of the command-line for the occaisional tweak, you'll do fine. It's a bit of a shift in philosophy though. Linux gives you much more power over your computer than Windows, with the only downside being that you have to tell your computer what to do, rather than having your computer ask you what you want. 

Cheers!

---

### Post by Assneck on 2005-09-13
[QUOTE=Nequeo]It's probably just a silly typo. Try using 'tab completion'.

Type:

chmod 777 /home/mike/linux

Then just hit tab a few times. It should show you a list of all files beginning with 'linux' in that directory. Add in a couple more letters, and hit tab again. Once you've narrowed it down to only one possibility, it will fill in the rest of the file-name for you automatically.

On the other hand, if all it does is beep at you, then there aren't any files beginning with 'linux' in /home/mike.

Try using 'ls' (short for 'list') to see the contents of a directory.

And with that out the way, welcome to Ubuntu! As long as you're not afeared of the command-line for the occaisional tweak, you'll do fine. It's a bit of a shift in philosophy though. Linux gives you much more power over your computer than Windows, with the only downside being that you have to tell your computer what to do, rather than having your computer ask you what you want. 

Cheers![/QUOTE]


ok i think i just installed the game and the point release to different directories! doh!  I can't install the point release to the same directory because the program tells me I don't have permission to do this.... I'm trying to install to /usr/local/games/

Am I not entering the root password someplace?  and how do i even know what the root password is?

---

### Post by Hobbsee on 2005-09-14
> and how do i even know what the root password is?

It's the password you put in at the installation :)  ie. it is the same password as the first user on the system.

---

### Post by Assneck on 2005-09-14
[QUOTE=Hobbsee]It's the password you put in at the installation :)  ie. it is the same password as the first user on the system.[/QUOTE]

yea thats what i've been using, but i wasnt sure if it was sticking because sometimes it would return an error when i was prompted for it, sometimes not.  Is there a way to add it someplace so I don't get prompted for it?  Also i'm trying to change my screen resolution to 1280x960 and the highest option available is 1024x768.  
I was trying to edit the xorg.conf file with the following:

```
Modes "1024x768" "800x600" "640x480" "1280x960" 
``` 

It won't let me because it says the file is read-only.  How do I fix this?  And do I need to install drivers for an ATI Radeon 9800Pro and would that make this easier? (I have the drivers downloaded as well)

---

