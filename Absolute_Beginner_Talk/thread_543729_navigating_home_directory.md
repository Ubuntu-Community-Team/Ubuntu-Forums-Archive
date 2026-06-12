---
title: "navigating home directory"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by nraney on 2007-09-05
Hello All,
I am a noob (this is my first post) and I'm trying to figure out ubuntu through the lessons on linuxcommand.org and ubuntuforums.org, but I hit a wall.

I can easily navigate the file system with the terminal but when I try to move around to the various folders in my home directory it retorts, "no such file or directory", even though the folders are clearly there (as I have proved with the ls command).  Can I not navigate my user files even though I'm logged in as that user?


All in all im trying to move a file from my desktop to etc/wpa/certs/ (which is a directory i created) and this is only the first step to installing a certificate to use the wireless at UT.  Once I get the basic navigation question answered I'm sure I will have to follow up on how to install the file. 

Thanks in advance for any help, I hope to learn Ubuntu quickly and will share knowledge gained by becoming an active member of the ubuntuforums.org community

N. Raney

---

### Post by RomeReactor on 2007-09-05
Hi. Can you please post how are you issuing the copy command? it may be useful to use TAB to autocomplete addresses in the terminal; start writing the folder or file name and press TAB.

---

### Post by nraney on 2007-09-05
actually I havnt even tried to move the file except for trying to drag it in with the file browser in which i get the message "error while copying to "etc/wpa/certs". you do not have permissions to write to this folder"

this is why i need to do it in terminal view with sudo. 

the problem is that the terminal wont let me move to the various folders in my home directory. for example this is my terminal:
nraney@nraney-laptop:~$ ls
1                                Chromeo - Rage.mpg       Desktop     Shared
Aug30physiology.odt              Chromeo - Tenderoni.avi  Examples    sirius
Chromeo - Fancy Footwork [2007]  Class                    Incomplete  wget-log
nraney@nraney-laptop:~$ cd ./class
bash: cd: ./class: No such file or directory
nraney@nraney-laptop:~$ cd /class
bash: cd: /class: No such file or directory
nraney@nraney-laptop:~$ 

still stuck,
n.raney

---

### Post by Lycaon on 2007-09-05
Hmm no clue if this helps BUT you are typing Class in lower case.
> nraney@nraney-laptop:~$ cd ./class
The results of your ls command give you **C**lass, and there it's with an uppercase C. 
Unix/Linux is always casesensitive in console. Maybe thats the only problem?

Greetz

---

### Post by Terl on 2007-09-05
The directory is named Class based on what I am seeing.  It is case sensitive so class is not the same as Class.  When you want to cd just do:  cd C then hit tab and it will auto-complete, if not hit the cd Cl then tab....

---

### Post by nraney on 2007-09-05
sweet. that worked.. ill get back if i have more problems

---

### Post by Lycaon on 2007-09-05
> **Terl said:**
> The directory is named Class based on what I am seeing.  It is case sensitive so class is not the same as Class.  When you want to cd just do:  cd C then hit tab and it will auto-complete, if not hit the cd Cl then tab....

and if you hit tab several time it will give you all the options (dir/files beginning with C) in the current directory:) Maybe handy to know:)

---

### Post by Terl on 2007-09-05
> **Lycaon said:**
> and if you hit tab several time it will give you all the options (dir/files beginning with C) in the current directory:) Maybe handy to know:)

Good call!  I forgot that part :)

---

