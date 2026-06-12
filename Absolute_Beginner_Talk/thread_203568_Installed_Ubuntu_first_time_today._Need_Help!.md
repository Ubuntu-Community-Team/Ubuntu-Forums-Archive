---
title: "Installed Ubuntu first time today. Need Help!"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-06-25
Ok so I just installed ubuntu today, and Im not so sure I find it as easy as everyone says as it is now. Ive got no problem installing the os or so, its the programs I install afterwords which gives me the headake. 

First:

Ive installed xmms player by putting some code into the terminal, all this went grate, and my xmms player plays music, but afterwords i thought "hey why not download some skins for it" so i downloaded a skin, and the instruktion to use it was very simple to put it in the directory: " /~xmms/skins/
But I cant find this directory, is it becouse i used the terminal to install the player? If so were would it be located.

Second:

Ive also tried to download some games: Stepmania and supertux. They both were on the deskop when i downloaded them. Afterwords I extrated them, and on the deskop were som new unarchived folders. But when i Open them, I only see some doucuments and pictures, it might be becouse i cant find the file to excute the game. Whats wrong here?

Hope you guys get what Im trying to explain here

Thanks in advance.

I

---

### Post by tony_tj3 on 2006-06-25
The way that i add skins is to add them to the folder /home/<username>/.xmms/Skins/, you can either copy it there, or move it there manually by entering the home folder, pressing <ctrl+h> (shows hidden folders), then looking for the folder .xmms, then skins. Then just drag and drop the skin into that folder.
	And as for games, i have never tried them, sorry.

---

### Post by bscbrit on 2006-06-25
The '~' symbol is shorthand for /home/<username> i.e. it is your home directory.  I think the actual directory is called .xmms which means it is a hidden directory.  In nautilus you have to select 'Show Hidden Files' under View before you can see it.  There will be something similar for KDE but I cannot remember what it is because I haven't used for a couple of years now.

---

### Post by IYY on 2006-06-25
> Ok so I just installed ubuntu today, and Im not so sure I find it as easy as everyone says as it is now. Ive got no problem installing the os or so, its the programs I install afterwords which gives me the headake.

Be sure to check out the Automatix script. It automates the installation of many common programs. Also, installing programs from source is sometimes a bit tricky on Linux, but most programs can be found in the repositories (go to the Synaptic program). 

> Ive installed xmms player by putting some code into the terminal, all this went grate, and my xmms player plays music, but afterwords i thought "hey why not download some skins for it" so i downloaded a skin, and the instruktion to use it was very simple to put it in the directory: " /~xmms/skins/
But I cant find this directory, is it becouse i used the terminal to install the player? If so were would it be located.

The directory is not /~xmms/skins but ~/xmms/skins. ~ is a shortcut to /home/yourusername/. Basically, all you need to do is enable hidden files.


```
Ive also tried to download some games: Stepmania and supertux. They both were on the deskop when i downloaded them. Afterwords I extrated them, and on the deskop were som new unarchived folders. But when i Open them, I only see some doucuments and pictures, it might be becouse i cant find the file to excute the game. Whats wrong here?
```

If you downloaded the source code, you will need to compile it. This is simple, but not the easiest way to do it. The easiest way would be through Synaptic. First, enable extra repositories:

[http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29)

Then, type

sudo apt-get install supertux

And your program is installed.

---

### Post by catlett on 2006-06-25
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) This is a great guide to help set up your system after install. This will help you with installing programs. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

If you are new to linux start by only adding applications from synaptic package manager ( it is under System<Administration) These are applications that will work for your system and do not need to be compiled.

---

### Post by Omnios on 2006-06-25
Hi welcome to the Ubuntu Linux community. As for .xmms skils the file with the skins has a . before the name .xmms in the home file system. Anyways the . in from of the filename makes it invisable so you have to open nautilus file brouser and choose View and click show hidden files. Now you will be able to see all the hidden files in Ubuntu. Hope this helps.

---

### Post by skale on 2006-06-25
For the second question, look in the folder for a README, which should tell you what to do. The website could have their own instructions as well. It generally involves copying a few files to different places or just executing a file.

---

### Post by jincast90 on 2006-06-26
Thanks alot for the help!

Now if you can answer one last little question.
How can i change my startpage in firefox? I use to be able to do it in windows, but its not the same in the linux distro 

Thanks.

---

### Post by stephen_lau on 2006-06-26
[QUOTE=jincast90]Thanks alot for the help!

Now if you can answer one last little question.
How can i change my startpage in firefox? I use to be able to do it in windows, but its not the same in the linux distro 

Thanks.[/QUOTE]

Um, same as in Windows - Firefox > Edit > Preferences > General Tab? :P

---

### Post by jincast90 on 2006-06-26
[QUOTE=stephen_lau]Um, same as in Windows - Firefox > Edit > Preferences > General Tab? :P[/QUOTE]

Your right!
Wow i wonder why that was so difficult for me :S

I feel so stupid ](*,) 

Thanks for the help!

---

### Post by Spleenie on 2006-06-26
[QUOTE=jincast90]Your right!
Wow i wonder why that was so difficult for me :S

I feel so stupid ](*,) 

Thanks for the help![/QUOTE]

Not stupid, just unfamiliar with new surroundings. We all learnt once :)

---

### Post by Nikusan on 2006-06-26
[QUOTE=jincast90]Your right!
Wow i wonder why that was so difficult for me :S

I feel so stupid ](*,) 

Thanks for the help![/QUOTE]

Perhaps because in windows it is **Tools** > Preferences.

---

### Post by skale on 2006-06-27
[QUOTE=jincast90]Your right!
Wow i wonder why that was so difficult for me :S

I feel so stupid ](*,) 

Thanks for the help![/QUOTE]
I think in windows it is Tools > Options or something.

---

