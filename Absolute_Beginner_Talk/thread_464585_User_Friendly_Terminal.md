---
title: "User Friendly Terminal"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-06-04
For you who arent in the know, you can create you own commands by using alias. Basically, you add alias command='set of commands' to the end of your bashrc file. Im thinking about writing a more user friendly bashrc with some helpful aliases for new people. Right now I'm trying to compile a list of common commands and wanted you guys to post some common used and useful commands for me to turn into aliases.

Thanks,
Nekiruhs

---

### Post by Nekiruhs on 2007-06-04
So far I have:

install = sudo apt-get install
remove = sudo apt-get remove
removecompletely = sudo apt-get remove --purge
restorevideosettings = sudo dpkg-reconfigure xserver-xorg

---

### Post by Nekiruhs on 2007-06-04
Now i have added;

removerestrictions='sudo chmod 777'
delete='rm'
deletefolder='rm -r'
lockdownfile='sudo chmod 700'

---

### Post by Feba on 2007-06-04
I'd change the last one to "reconfigurex" or even just "resetx"

Other than that, I think simplifying the terminal too much is doing people a disservice, in the long run, unless you make universal changes to the shell across any OS that uses it.

---

### Post by daimaru on 2007-06-04
i mean its nice and all that you can shorten the input to install or remove , but whats the point really? if you make up aliases peoples would still have to learn your assigned names. so wouldnt it be better that they actually learned the real commands? 
or are you just looking for commands that you can use ?

---

### Post by Nekiruhs on 2007-06-05
> **daimaru said:**
> i mean its nice and all that you can shorten the input to install or remove , but whats the point really? if you make up aliases peoples would still have to learn your assigned names. so wouldnt it be better that they actually learned the real commands? 
or are you just looking for commands that you can use ?
Im trying to make it less cryptic to new users. im pretty sure ```
deletefolder /home/name/mydocs/
```
is clearer than```
sudo rm -hRi /home/name/mydocs/*.*
```

---

### Post by Nekiruhs on 2007-06-05
Now I have:
 
alias gototrash='cd ~/.Trash'
alias emptytrash='rm ~/.Trash/'
alias makeshortcut='ln -s'
alias gotodesktop='cd ~/Desktop'
alias gotohome='cd ~'
alias sendtohome='mv ~/'
alias focrequit='killall -9'

---

### Post by Feba on 2007-06-05
Maybe, but how is it anymore clear than "clearfolder" "deletepath" "deletedir" "deleteall"? The fact is, users are going to have to learn commands, they might as well learn standard ones they can apply to other systems. Imagine you teach a programming language, but you try to substitute things. Let's take a simple example, python. you think  "print" isn't clear enough, because the user might think it will actually print a result. So you change it to "output". That one simple change wouldn't be a problem for someone used to it, the user would get used to it, but someone who doesn't learn any other way is going to try to write on another machine, and it's going to become useless, and they won't know why. The shortest path isn't always the quickest in the long run.

---

### Post by Nekiruhs on 2007-06-05
Allright, you got me there. But im also working on some scripts and some functions to include. Those would add extra functionality. Besides, if its easier for them now, how many linux boxes are they going to come across? I'll also make it clear in the installer that these are not true and supported commands. Besides, BASH is kinda universal isn't it, in theory, you could do the same thing to Fedora or SUSe with very little modification, right?

Besides, all I was asking is if anyone could contribute some useful commands. Ill turn them into functions, scripts and aliases.

---

### Post by arsenic23 on 2007-06-06
I normally have tons and tons of aliases on my various installs.  Mostly they're for specific tasks that only happen on that machine, or they are for a string of several commands that I find I use alot.

For instance, I found that I used the clear command almost every time I went back to my home directory, and that I also cleared often when I was using ls in the same directory more then once.  To that effect, every machine I own has the following aliases:
```
alias cl="clear&&ls"
alias cll="cd ~/ &&clear&&ls"
alias clll="clear&&ls -al"
```

Likewise, 
```
alias sudoupdate="sudo apt-get update && sudo apt-get upgrade"
alias acs="apt-cache search"
```made it onto all of my PCs just for the sake of saving keystrokes.  Again, most of my aliases are more then one line of input; I really don't see the purpose of changing one command to another.  The only reason I shortened 'apt-cache search' is because when I first started using Linux regularly, I got tired of typing 'apt-cache search' over and over and over again while I was looking for software to fill my needs.

---

### Post by meng on 2007-06-06
The whole point of having Linux is to allow individual users to customize the system as they see fit. So by definition, it doesn't make sense to criticize what Nekiruhs is doing simply because other users may not like it or find it helpful. If, however, it's wrong or insecure, then criticize away!

---

### Post by arsenic23 on 2007-06-06
> **meng said:**
> The whole point of having Linux is to allow individual users to customize the system as they see fit. So by definition, it doesn't make sense to criticize what Nekiruhs is doing simply because other users may not like it or find it helpful. If, however, it's wrong or insecure, then criticize away!

I don't think anyone was saying that it was wrong for someone to change their commands around using aliases.  What was being gotten at was that if you persuade a lot of people to use alot of different aliases in place of the original commands then you may cause various problems for them later on down the road.  

For instance:  When I first started using netstat I always called it with '-vn --tcp' and could not think of a reason why I wouldn't want those flags.  So I made an alias 'netstat -vn --tcp' and called it 'getips', which I used over and over again.  Several weeks later, while on my laptop away from home, I typed getips into my terminal.  "Oops, I don't have that alias on this laptop!" I said to mayself, "That's ok, I'll just type ip... no wait..."  I couldn't remember the original command because I'd made an alias that had no reference or clue towards its real name, netstat.

So while there is nothing wrong with replacing your commands with whatever aliases you want, it's important to remember that teaching people who are just starting out with linux to do this could cause problems for them.  Instead of learning linux, they'd be learning their own shortcuts.  Even so, some people may still prefer to do this, it just seems fair to warn them of the pros and cons of the situation.

---

### Post by nonewmsgs on 2007-06-06
i think it's a great idea. if a user would find it easier to learn whole words and use alias more power to them.  what i would find very useful is something for installing a tarball and rpm.

---

