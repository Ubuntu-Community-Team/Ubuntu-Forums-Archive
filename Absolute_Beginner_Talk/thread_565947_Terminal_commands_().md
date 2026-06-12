---
title: "Terminal commands (?)"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Mr_JMM on 2007-10-02
[SIZE="3"][FONT="Tahoma"]Hi,

Apologies, I don't know the correct terminology so please do feel free to correct me.

I was wondering if the commands(?) that we type into the terminal are the same throughout Linux distributions? I appreciate there may be some Distro specific commands but as I'm new to Linux and am trying out several different distributions I thought I'd ask (certainly hope so otherwise LOTS of late nights ahead ;-) )

Cheers,

James.[/FONT][/SIZE]

---

### Post by w4ett on 2007-10-02
Here is a listing of commands:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

They commands and structure are pretty much consistant between distros

---

### Post by rsambuca on 2007-10-02
All of the bash commands are transferable between distros.  Specific commands like apt-get are running 'apt' commands, which will be specific to debian based distros, for the most part (although apt may be installed on other systems as well).

Just a friendly note that in the Ubuntu Forums Code of Conduct they ask you to refrain from using colours for your entire posts. It is meant more for highlighting specific words or phrases for emphasis.

---

### Post by RedSquirrel on 2007-10-02
It depends on what you're trying to accomplish. For basic things such as changing directories, renaming files, and so on, the commands are generally the same.

Some commands are specific to a particular distribution (or a group of distributions). For example, the commands you issue to install software from repositories will differ depending on which package manager is used. Commands that relate to other aspects of system configuration may be different as well.

---

### Post by Mr_JMM on 2007-10-02
Cool. Three replies so quickly!! Many thanks.

Ok. So "Bash" commands are general Linux commands. Is there a complete list of Ubuntu specific commands (on the forum -did a brief search or other electronic media)?

---

### Post by odiseo77 on 2007-10-02
> **Mr_JMM said:**
> Cool. Three replies so quickly!! Many thanks.

Ok. So "Bash" commands are general Linux commands. Is there a complete list of Ubuntu specific commands (on the forum -did a brief search or other electronic media)?

bash commands are the same between different linux distros, but what may vary among them are the commands related with the packaging system, so, debian-based distros like ubuntu and others use dpkg/apt-get/aptitude for package maintenance; rpm based distros (RedHat, Fedora, SuSE, etc), use rpm (and some might even use apt-get for .rpm packages), etc.

As for guides on the command line, I'd suggest:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

and:

[http://tldp.org/](http://tldp.org/)
(this one also has all type of tutorials, howtos, and such).

Regards.

---

### Post by PokieCarlwin_is_borked on 2007-10-29
hi 
first of that last link is amazing, but it didn't solve my problem.  I'm trying to  " :~$ rmdir /subscribe2 "   and all the files and dir in subscribe2, but this command only works for empty "dir"s is there a cool way to get rid of it all or must i enter each separate dir and delete everything individually?

---

### Post by Inxsible on 2007-10-29
> **PokieCarlwin_is_borked said:**
> hi 
first of that last link is amazing, but it didn't solve my problem.  I'm trying to  " :~$ rmdir /subscribe2 "   and all the files and dir in subscribe2, but this command only works for empty "dir"s is there a cool way to get rid of it all or must i enter each separate dir and delete everything individually?
```
rm -rf /subscribe2
```What this does
rm = remove
options: r = recursive = meaning for all files in the directory and sub-directory.
f = force

---

### Post by stchman on 2007-10-29
> **PokieCarlwin_is_borked said:**
> hi 
first of that last link is amazing, but it didn't solve my problem.  I'm trying to  " :~$ rmdir /subscribe2 "   and all the files and dir in subscribe2, but this command only works for empty "dir"s is there a cool way to get rid of it all or must i enter each separate dir and delete everything individually?

Use the rm command.  To remove a directory and all its subdirectories try the following command.  Assume there is a folder called junk in your home folder with several subdirectories with files in the folders.

```
rm -r -f ~/junk
```

Let me explain each part.

rm =  remove command
-r = does the command recursively (subdirectories included)
-f = force the command no matter what the permissions may be
~/ = this is a shortcut to the currently logged in users home directory


Now the force command wont work if you do not OWN the folder.

---

### Post by PokieCarlwin_is_borked on 2007-10-29
thanks guys but problem cont.
  
/plugins$ rmdir -r -f subscribe2/
rmdir: invalid option -- r


i tried -rf earlier w/ the same responce ~/ gave me no tab completion so i didn't try it.  I'm not sure if this is an issue but i am ssh  and that system is debian, which i thaought was where ubuntu was derived -> same commands?

---

### Post by sandysandy on 2007-10-29
thats neat.

can u advise on which are the important commands a beginner must learn.

regards

---

### Post by jmoorse on 2007-10-29
> **PokieCarlwin_is_borked said:**
> thanks guys but problem cont.
  
/plugins$ rmdir -r -f subscribe2/
rmdir: invalid option -- r


i tried -rf earlier w/ the same responce ~/ gave me no tab completion so i didn't try it.  I'm not sure if this is an issue but i am ssh  and that system is debian, which i thaought was where ubuntu was derived -> same commands?

Ensure you are using the:

rm

command  with the -rf switch, and not the rmdir

---

### Post by Inxsible on 2007-10-29
> **PokieCarlwin_is_borked said:**
> thanks guys but problem cont.
  
/plugins$ rmdir -r -f subscribe2/
rmdir: invalid option -- r


i tried -rf earlier w/ the same responce ~/ gave me no tab completion so i didn't try it.  I'm not sure if this is an issue but i am ssh  and that system is debian, which i thaought was where ubuntu was derived -> same commands? The command is rm not rmdir

EDIT : Whoops ! didnt see the next page :(

---

### Post by Inxsible on 2007-10-29
> **sandysandy said:**
> thats neat.

can u advise on which are the important commands a beginner must learn.

regards
Try this link [Linux Commands]("http://linuxcommand.org/")

---

### Post by PokieCarlwin_is_borked on 2007-10-29
unfortunately, 

 rm subscribe2/
rm: cannot remove `subscribe2/': Is a directory

---

### Post by Inxsible on 2007-10-29
> **PokieCarlwin_is_borked said:**
> unfortunately, 

 rm subscribe2/
rm: cannot remove `subscribe2/': Is a directory
You are not reading the commands properly in your haste. it is ```
rm -rf /subscribe2
``` and NOT ```
 rm subscribe2/
```

---

### Post by PokieCarlwin_is_borked on 2007-10-29
I'm DUMB and you are SOOO right thank you!  two lessons learned one in terminal and the other in READING!  LMAO:lolflag:

---

