---
title: "password problem"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-09-13
When I use the sudo command and enter my password, it accepts it and goes on with the job.
However, if I issue the su command and enter the same password, my password gets rejected.
This also happens when I try to remove a printer and the KDE Daemon asks for my password.
I have only ever used one password on this system, so what could be happening? 
Does anyone know?

---

### Post by splintercellguy on 2007-09-13
On Ubuntu, the root account is disabled, so you cannot directly login AS root, but you can gain root privileges via sudo. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tonymoloney on 2007-09-13
OK. Thanks. But how do I remove a printer when I have to supply a password?

---

### Post by Wim Sturkenboom on 2007-09-13
Have you tried *sudo -s*. It gives you a shell with root privileges.

With regards to *su*, that needs the root password, not your password. As already mentioned, the root account is disabled by default.

---

### Post by bodhi.zazen on 2007-09-13
sudo -i is preferable to -s

-i = new shell (using root's environmental variables)

-s = same shell (using you user environmental variables)

Check it out :

> 
bodhi@VirtualUbuntu:~$ [color=blue]sudo -s[/color] 
[color=red]root@VirtualUbuntu[/color]:~# echo $HOME                                                                                                     
[color=blue]/home/bodhi[/color]
root@VirtualUbuntu:~# exit
zsh: can't write history file /home/bodhi/.zhistory

bodhi@VirtualUbuntu:~$ [color=red]sudo -i[/color]                                                                                                       
[color=red]root@VirtualUbuntu[/color]:~# echo $HOME
[color=red]/root[/color]
root@VirtualUbuntu:~# exit
logout
bodhi@VirtualUbuntu:~$

See the difference ? Both -i and -s give a shell with root access, but the environmental variables with that shells are *very different*.

:twisted:

---

### Post by tonymoloney on 2007-09-13
Thanks for the responses.
This problem came about while I was trying (unsuccesfully) to install a Brother DCP110C printer on my system.
I am now trying to remove the printer that managed to find its way into the system by going to System Settings (on the Start menu)/Printers then on the printer that shows up, I am right clicking and selecting Remove.
This results in me being asked for a password (in a GUI) and I have no choice other than to put in my only password, which is then rejected.
I am trying to remove this printer because I have found another method of installing it which just might work.
At this time, I have actually queued several jobs to the printer, but the first one has been sitting there for a couple of days just saying Processing.
How can I do this in a terminal?

---

### Post by bodhi.zazen on 2007-09-13
Obviously an (annoying) bug ...

You can temporarily activate root :

In a terminal :```
sudo passwd
```

Enter a new root password (twice)

Now re-try you gui , this timme enter your new root password.

When done, open a terminal

```
sudo passwd root -l
```
*that is a small -l

---

### Post by Wim Sturkenboom on 2007-09-13
I think the first code in above post must be *sudo passwd root*.

And  bodhi, thanks for highlighting the -i option (I did not know about it but know the difference between su and su - ).

---

### Post by bodhi.zazen on 2007-09-13
> **Wim Sturkenboom said:**
> I think the first code in above post must be *sudo passwd root*.

And  bodhi, thanks for highlighting the -i option (I did not know about it but know the difference between su and su - ).

If you leave out the root in "sudo passwd root" it will default to root (because you ran the command as root via sudo).

In a terminal if you enter : "passwd" you will change your password.

If you enter "passwd <user>" you will change the password for the <user>. You must either know the <user> password or run a root "sudo passwd <user>".

su = new shell as root (interactive, non-login).

su - = new log in shell as root (interactive, log in).

~/.bashrc file runs every time you open a new non-login bash shell such as xterm / aterm, and ~/.bash_profile runs only with login shells i.e when you first log in into system.

so, su will run .bashrc
su - runs .bash_profile

Most do not customize these two much so there is not much difference. Many put just

> source ~/.bashrcin .bash_profile.

These are shades of gray.

Here is a run-down of the various shells :

> Bash executes startup files differently than other shells. The Bash behavior is a compromise between the csh principle of startup files with fixed names executed for each shell and the sh "minimalist" behavior. 

An [color=blue]interactive[/color] instance of Bash started as a [color=blue]login shell[/color] reads and executes ~/.bash_profile (the file .bash_profile in the user's home directory), if it exists.

An [color=green]interactive non-login[/color] shell reads and executes ~/.bashrc.

A [color=red]non-interactive shell[/color] (one begun to execute a shell script, for example) reads no fixed startup file, but uses the value of the variable $ENV, if set, as the name of a startup file.

[http://www.linuxjournal.com/article/2784](http://www.linuxjournal.com/article/2784)

---

### Post by Wim Sturkenboom on 2007-09-14
> **bodhi.zazen said:**
> If you leave out the root in "sudo passwd root" it will default to root (because you ran the command as root via sudo).Makes sense, thanks for that explanation.

---

