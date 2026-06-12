---
title: "how do i make command line shortcuts?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by bbqbaker on 2006-02-25
like if i want to typw www at the command line, id like it to bring me to /var/www

instead of having to write the full path. also, id like to be able to type ebash and it execute sudo gedit /usr/.bashrc

is this called using aliases?

---

### Post by heimo on 2006-02-25
[quote=bbqbaker]is this called using aliases?[/quote]

Yes. And you can find examples in .bashrc Make changes and run
```
. ~/.bashrc
```

---

### Post by bbqbaker on 2006-02-25
can i do something like this?

alias home = 'cd /home/koloa'
alias www = 'cd /var/www'
alias bash = 'sudo gedit /home/koloa/.bashrc

---

### Post by heimo on 2006-02-25
[quote=bbqbaker]can i do something like this?[/quote] 

Couple problems there. You should probably avoid using names which are already in use (bash), you probaly don't need an alias for going to your homedir (you can use cd without parameters or ~ sign) and you can't have spaces around equal sign. But yes, your basic idea is correct.
```
alias home='cd /home/koloa'
```  Instead of this, it's normal to just type *cd *or when you need to refer to your home directory otherwise, you can use ~, for example, making a backup copy of your /etc/X11/xorg.conf file to your home directory: 
```
cp /etc/X11/xorg.conf ~
``` 
```
alias www='cd /var/www'
``` That's fine.

```
alias edbash='gedit ~/.bashrc'
``` You should not need root access to that file if it's owned by your user, so no sudo there, and if you really need root access to any GUI program, use gksudo (in Gnome) or ksudo (in KDE). For command line programs, use sudo. But do not learn a bad habbit of prefixing everything with sudo as it's [Bad Thing]("http://www.catb.org/jargon/html/B/Bad-Thing.html").

Kyrals [Terminal for Beginners]("http://www.ubuntuforums.org/showthread.php?t=73885") is excellent thread for learning more about using command line. I would say that anyone who goes through that and learns the tricks there, is not command line beginner.

---

### Post by Madpilot on 2006-02-25
yes, but I'd modify those a bit:

alias home='cd && /home/koloa'
alias www='cd && /var/www'

The first 'cd' moves you back to your own user directory, so you're always starting from the same place, and the '&&' means "do the first command, then do the 2nd if the first one succeeds"

---

### Post by Trab on 2006-02-25
thats the basic idea... to run longer scripts, i would suggest writing a bash script...
```

sudo gedit /bin/(command name here, make it origonal!)

```

put in the commands you want here (seperate by enter or the | caracter)
then 
```

sudo chmod 755 /bin/(file name agian!)

```
i find this easier, and a bit cleaner... never liked aliasing much...

---

### Post by heimo on 2006-02-25
Good addition Trab. One suggestion, which may be helpful, is to put your personal bash scripts in ~/bin (that's bin directory under your home directory) and include this directory in your PATH environment variable. If I'd like scripts to be accessible for everyone in the system, I'd probably put them to /usr/local/bin 

I don't remember what's the default PATH in Breezy, but you should be able to change it in ~/.bashrc using something like:[FONT=monospace]
[/FONT]```
export PATH="~/bin:$PATH"
```

In the development version of Ubuntu (Dapper Drake, 6.04) PATH will be defined system wide in /etc/environment
[https://wiki.ubuntu.com/OneTruePath](https://wiki.ubuntu.com/OneTruePath)

---

