---
title: "Beginner fighting bash shell, shell winning.....Please help I want to love Ubuntu"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kaelinsanity on 2007-02-20
Hi, thanks for reading this.  I'm having some real beginner issues..I just downloaded a file, put it on the desktop ( and several other places for posterity ) and text commands such as 

find put-my-filename-here

return no results.

The prompt I'm at reads

shawn@desktop:~$

I've been having a reasonable amount of trouble navigating the file system from the text interface(bash shell?), but I've learned enough to try commands like sudo and sudo -i for root access etc....

I feel like I'm missing some very very basic information about navigating the directory because i can give the command

dir 

at the aforementioned prompt, and the system returns

backup desktop examples setups

which makes perfect sense to me, but if i issue the command

cd /setups

the system returns

-bash: cd/setups: no such file or directory

I've tried many syntax variations, as well as prompt variations,adding sudo, being the root etc.  I'm getting these commands out of a Linux for Dummies book, and all the other commands work.  I can make and delete directories, man, I even managed to configure dual monitors, but this has got me loosin my mind.
I'm really feeling unintelligent at this point, because I've done a fair amount of reading about Linux/Ubuntu over the past three days, and found plenty of easy to come by info on solving other seemingly more complex issues, but this has got me stuck.

Please give me some direction so that I can better understand why I can see directories, but can't get into them. And why I can't access a file I just downloaded.  (and if your reply starts.....because you're a dummie.....I can deal with that....  :)   )

---

### Post by Bachstelze on 2007-02-20
Given that setups is a subdir of the current dir, you need to type *cd setups* to cd to it. In Unix-like systems, / means the top-level ("root") directory, so /setup would be a subdir of / called setups, not a subdir of the current dir.

---

### Post by kaelinsanity on 2007-02-20
um...that was one of the variations I tried.....just tried it again, no good.

---

### Post by Maestro23 on 2007-02-20
Get you feet wet with commands/file structure:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Just takes time, hang in there.:)

---

### Post by kaelinsanity on 2007-02-20
I'll definately check those out, but here's a line by line for you 

shawn@desktop~$ dir
backup desktop examples setups
shawn@............$ cd setups
-bash: cd: setups: no such file or directory

I've read some basic guides already, and they seem to say that the above shouldn't happen.

---

### Post by Bachstelze on 2007-02-20
That's really weird... Anyway, in Linux, you don't use dis but *ls*. Also, are you sure setups is a dir ?

---

### Post by kaelinsanity on 2007-02-20
the shell lists it as one, and file manager has it as a folder.......

---

### Post by Bachstelze on 2007-02-20
YOu must be doing something wrong. Please copy/paste *exactly* what ls returns.

---

### Post by kaelinsanity on 2007-02-20
shawn@down-with-the-man:~$ ls
Backup  Desktop  Examples  Setups
shawn@down-with-the-man:~$ cd backup
bash: cd: backup: No such file or directory
shawn@down-with-the-man:~$ cd setups
bash: cd: setups: No such file or directory
shawn@down-with-the-man:~$ cd desktop
bash: cd: desktop: No such file or directory
shawn@down-with-the-man:~$

---

### Post by Bachstelze on 2007-02-20
Hehe, you're not in Windows anymore, dude. **S**etups is not the same as **s**etups ;)

---

### Post by Maestro23 on 2007-02-20
> **kaelinsanity said:**
> shawn@down-with-the-man:~$ ls
Backup  Desktop  Examples  Setups
shawn@down-with-the-man:~$ cd backup
bash: cd: backup: No such file or directory
shawn@down-with-the-man:~$ cd setups
bash: cd: setups: No such file or directory
shawn@down-with-the-man:~$ cd desktop
bash: cd: desktop: No such file or directory
shawn@down-with-the-man:~$

Case Sensitive.

cd Backup

cd Desktop

etc....

---

### Post by kaelinsanity on 2007-02-20
AmAzing.....I'd have sworn that I tried that variation...but so far so good...HEHEHE indeed....case sensitivity dually noted.....Thanks....now about that missing file.....holy crap it worked,  Thanks for your persistance in resolving this with me.....I'm gonna go nap now....good night.

---

### Post by Maestro23 on 2007-02-20
> **kaelinsanity said:**
> AmAzing.....I'd have sworn that I tried that variation...but so far so good...HEHEHE indeed....case sensitivity dually noted.....Thanks....now about that missing file.....holy crap it worked,  Thanks for your persistance in resolving this with me.....I'm gonna go nap now....good night.

No prob.  Sleep well.:)

---

### Post by bradmayne on 2007-07-09
yes hymen to life is right your not in winblows anymore dorothy.  Your have to realize that README is not that same as readme etc.   Anyways just remember that we're all here to help if I told you some of the stuff that happened to me you would blow mile out your nose as you laugh.

---

### Post by hyper_ch on 2007-07-09
Btw, for finding files you do this:

```

locate FILE

```

If nothing is returned, you may need to update the list of files first:

```

sudo updatedb

```
It does auto-update itself at certain intervals but sometimes you need find new files that aren't included yet there.

---

