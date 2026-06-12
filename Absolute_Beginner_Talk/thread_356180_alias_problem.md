---
title: "alias problem"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by denver38 on 2007-02-08
i have some problems with making aliases (i'm using kubuntu)
-After writing pico .bashrc (or nano .bashrc) in dennis@dennis-laptop:~$, the file .bashrc opens up in my terminal
then, I edited it by adding: 
# my personal aliases
alias cp='cp -v -i' 

and 'saved' it by clicking settings->save as default
did i save it incorrectly?

btw, why can't i just open nano (just as e.g. OOo) by going to /bin/nano , i thought is was a text editor?
and why can't i see the file .bashrc in my homedirectory (that would be useful because i copied it several times)?

tnx a lot
dennis

---

### Post by thatref on 2007-02-08
i would like to know it too

---

### Post by KentS on 2007-02-08
> **denver38 said:**
> i have some problems with making aliases (i'm using kubuntu)
-After writing pico .bashrc (or nano .bashrc) in dennis@dennis-laptop:~$, the file .bashrc opens up in my terminal
then, I edited it by adding: 
# my personal aliases
alias cp='cp -v -i' 

and 'saved' it by clicking settings->save as default
did i save it incorrectly?


Looks correct to me. Did you start a new shell before trying out your alias? The file isn't read unless you start a new terminal, or type
```
source .bashrc
```
in a terminal.

>  
btw, why can't i just open nano (just as e.g. OOo) by going to /bin/nano , i thought is was a text editor?

What do you mean? /bin/nano is probably given in your path variable, so you should be able to open nano anywhere by just typing
```
nano
```

> 
and why can't i see the file .bashrc in my homedirectory (that would be useful because i copied it several times)?


The '.' before a filename means the file is hidden. To see these files listed you need to add the option '-a', eg. 'ls -a'.

---

### Post by denver38 on 2007-02-08
tnx for the reply
well, I tried already the source .bashrc code, and even rebooted my pc, but it seems like I'm  not saving the file in a correct way
after I added some aliases, i go to settings, save as default, and I also tried save sessions profile, but when I reopen the file the code is still the way it was before i edited it.

---

### Post by KentS on 2007-02-08
When I work in nano or pico I save the file by pushing 'o' while holding in the 'ctrl' button. That works well for me. You can try another editor, eg. vim. Type
```
cd
vim .bashrc
```
In vim push 'esc' and then 'i'.
Do the changes. Push 'esc', ':', 'w', 'q' and then 'return'.
Type
```
source .bashrc
```
And see if it works.

---

### Post by denver38 on 2007-02-08
tnx a bunch !
it works well with ctrl-o

---

### Post by tc101 on 2007-02-08
I am also having a problem with aliases.  I am just learning to do this.  I edited my .bash_profile file, saved it and rebooted.  The 3 lines at the end are what I added.  None of the 3 aliases I added work.  What am I doing wrong?

Here is the complete .bash_profile with my 3 aliases at the end

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

alias l='ls -l'
alias today='date +"%A, %B %-d, %Y"'
alias backup='/home/tomcarr/scripts/backup

---

### Post by KentS on 2007-02-08
> **tc101 said:**
> I am also having a problem with aliases.  I am just learning to do this.  I edited my .bash_profile file, saved it and rebooted.  The 3 lines at the end are what I added.  None of the 3 aliases I added work.  What am I doing wrong?

You might want to add your aliases to your .bashrc file instead of your .bash_profile file. There's no need for rebooting after editing your .bashrc file. Just open a new terminal window, or type 'source .bashrc' in your current shell.

> alias backup='/home/tomcarr/scripts/backup

I'm not sure what you actually want with this alias. '/home/tomcarr/scripts/backup' is just a directory ending with a filename(?). You haven't said what you want the command 'backup' to do with this file/directory. Do you for example want to move to it (cd /home/tomcarr/scripts/backup)? To run executable files that are not given in your path you have to type a '.' in front of the filename (eg. './home/tomcarr/scripts/backup') And there's another problem. I you are in the directory '/home/tomcarr' and give the command './home/tomcarr/scripts/backup' (backup), it will be interpreted as ''./home/tomcarr/home/tomcarr/scripts/backup'. That file doesn't exist. I think the best way of adding such a command is either to edit your path variable to include '/home/tomcarr/scripts', or to place the file backup in a directory already in your path variable, eg. '/bin', '/usr/bin', or something. That should allow you to execute the program without the '.', or by giving the directory. It should work like you want your alias to behave.

---

### Post by tc101 on 2007-02-09
> You might want to add your aliases to your .bashrc file instead of your .bash_profile file. There's no need for rebooting after editing your .bashrc file. Just open a new terminal window, or type 'source .bashrc' in your current shell.


That works fine.  Thanks for your help KentS.  I wonder why it doesn't work to put them in the .bash_profile file?

> I'm not sure what you actually want with this alias. '/home/tomcarr/scripts/backup' 

I should have made that more clear.  I have a shell script named 'backup', located in a directory named '/home/tomcarr/scripts'.  The alias runs the script, which does a backup.  It works fine now that I up the alias in .bashrc but I still want to understand why it doesn't work in  .bash_profile.

---

### Post by harakiri1976 on 2007-02-13
Hey, I'm having a similar problem with alias, just like you.
I create an alias just like you did before. And the problem is that when I close the shell and open it again the Alias command has been lost. I am not going to ask you if I HAVE TO SAVE it! That's obvious, as i can see. I'm gonna need your help to learn how can I save an ALIAS Command. I am using BASH Shell.

Thank You!

Please feel free to mail me: [email]harakiri1976@gmail.com[/email]

---

