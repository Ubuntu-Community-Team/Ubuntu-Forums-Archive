---
title: "What am I doing wrong??"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2006-01-25
I remember reading someone's post awhile back, saying how happy they were with linux/ubuntu, now that they were able to get through this [http://www.linuxcommd.org]("http://www.linuxcommd.org") tutorial. Recently I started doing the tutorial as well, but got stuck at the part explaining 'aliases' as seen here [http://www.linuxcommand.org/wss0020.php#aliases]("http://www.linuxcommand.org/wss0020.php#aliases")
I followed exactly what was there, but it didn't work. 

Could someone please help me with what I'm doing wrong? I can't or don't want to continue, because that wouldn't help me understand. Please help as I really want to learn the command line.

Thank you in advance

---

### Post by ubuntumaneh on 2006-01-25
what exactly didn´t work?
What do you want to do?
If you use the command:
alias l='ls -l'
then try it:
l 
press enter.

---

### Post by Il_Tuo_Nome on 2006-01-25
That's what didn't work

once I added the line "alias l='ls -l'" then pressed l, it would not perform the function it was suppose to "ls -l". 

I'm assuming it worked when you did it?

thanks for your help :D

---

### Post by earobinson on 2006-01-25
can you cut and paste the whole terminal interaction compleat with erros and all.

---

### Post by ekarni on 2006-01-25
Did you remember to reload the file containing the alias definition?  Type

$> source .bashrc

at the command line after saving your .bashrc file with your new command alias.  This happens automatically when you open a terminal window, so you can also just open a new one and see if the alias works there.

---

### Post by Il_Tuo_Nome on 2006-01-25
Maybe that's my problem. I was following the turial and added that line to .bash_profile. Am I suppose to be adding to .bashrc?

---

### Post by Il_Tuo_Nome on 2006-01-25
oh, and here is the error when I added to .bash_profile 

rosso@stucazz:~$ sudo gedit /usr/share/.bash_profile
Password:
rosso@stucazz:~$ l
bash: l: command not found
rosso@stucazz:~$

---

### Post by ekarni on 2006-01-25
.bashrc is where I've got mine and they work -- try them there

---

### Post by hillbilly on 2006-01-25
you can add it to either. But you have to source the file that you added it to.

.bash_profile is run whenever you login. .bahsrc is run whenever you source another bash shell. 

So you can add it into any of the file you want, but just source the file you added it to !!

---

### Post by Il_Tuo_Nome on 2006-01-25
ekarni,

sorry but which .bashrc? The only ones I have are bash.bash.rc, dot.bashrc.


Thanks for your patience

---

### Post by hillbilly on 2006-01-25
hey you are working on a bash shell arent you !! do > echo $SHELL, that will tell you which shell are working. 
if it is bash, then all you have to do is just create a .bashrc file.
> touch .bashrc
Then edit the .bashrc file and you dont have to do this with sudo, since you would(/should) be editing your own .bashrc !!

---

### Post by ubuntumaneh on 2006-01-25
Any ubuntu installation comes with bash as shell and .bashrc, isn´t it?
I know there is no .bash_profile, and if it were the case, he would have to create one. I think it is not necessary. Just edit .bashrc

---

### Post by hillbilly on 2006-01-25
:O !! hey i had .bash_profile and .bashrc with my default ubuntu installation  !!

Does anyone else have it this way ?? (I mean without these two files ?)

---

### Post by ekarni on 2006-01-25
Hmm, got me there - I'm not sure if the system looks for files with those names by default.  Let's take a step back and look at the whole thing.

In your home directory, type ls -a  This will display all files, including hidden ones that start with .  See if .bashrc exists.  If yes, go ahead and edit it.  If not, that seems odd to me!

Did you try what hillbilly suggested?  First, check to make sure you are using bash (default, I think) as your own user (not sudo).  If you've put the alias command in your .bash_profile, the easiest thing might be to source that file ($> source .bash_profile) and see if things work.

---

### Post by Il_Tuo_Nome on 2006-01-25
Thank you all very much, sorry for my saddness. I added it to .bashrc then reloaded it and bam. By the way, while in my /home/rosso I ls -a and both files were there, obviously I did  something wrong

Thanks a lot all, now I can continue that tutorial :)

---

