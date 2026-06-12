---
title: "My script is in home/myname/bin why cant I execute it?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-10-07
I have been following this guide: [http://linuxcommand.org/wss0010.php](http://linuxcommand.org/wss0010.php)
and from what I understand if I place my script called my_script in home/myname/bin the script is suppose to run by itself if I write my_script in the terminal. The thing is. It doesent. What am I doing wrong?

---

### Post by odinfromvalhalla on 2006-10-07
make sure you chmod +x your script. that will make it executable.

---

### Post by pgatrick on 2006-10-07
Did you add that directory to the path?

---

### Post by aysiu on 2006-10-07
If you have a script called *myscript* in /home/myname/bin, you need to do this to execute it: ```
cd ~/bin
chmod +x my_script
./my_script
```

---

### Post by jincast90 on 2006-10-07
> **pgatrick said:**
> Did you add that directory to the path?

Yeah Im pretty sure I did. I did this command:

export PATH=$PATH:home/myname/bin

---

### Post by pgatrick on 2006-10-07
> **jincast90 said:**
> Yeah Im pretty sure I did. I did this command:

export PATH=$PATH:home/myname/bin

Should be export PATH=$PATH:**[color=red]/[/color]**home/myname/bin :p

---

### Post by jincast90 on 2006-10-07
Strange It works perfectly fine. But when I shutdown the terminal and start it up again it doesent work anymore. Then I type in export PATH=$PATH:/home/myname/bin again and it works fine. Isint there anyway I can make it remember it for the next time I open up the terminal?

---

### Post by jincast90 on 2006-10-07
Oh I think I know how.. I think it says in the guide. Im too tired to try anymore. Ill try again tommorow.

---

### Post by pgatrick on 2006-10-07
Yeah, it's in the guide. :p

---

### Post by jincast90 on 2006-10-08
Ok now I have a problem again. If you look in the guide [http://linuxcommand.org/wss0010.php](http://linuxcommand.org/wss0010.php) I am supposed to edit my .bash_profile the thing is I cant find this file. The closest I get to it, is a file called dot.bash_profile. Is this the same? Atleast I tried to add the link PATH=$PATH:home/myname/bin to dot.bash_profile but It was read only. What should I do? I am totally lost now.

---

### Post by odinfromvalhalla on 2006-10-08
just create a file .bash_profile in your root folder (not /root but ~/) and add there the things needed.

---

### Post by jincast90 on 2006-10-08
> **odinfromvalhalla said:**
> just create a file .bash_profile in your root folder (not /root but ~/) and add there the things needed.

When you say /root you mean places->computer->filesystem right? Because I tried to make a file called .bash_profile in there, but its just not possible? Do I need to be superuser/rootuser to do so?

---

### Post by odinfromvalhalla on 2006-10-08
by root folder i mean your home folder:

i.e.: for user odin the root folder is /home/odin

try the following:
ALT+F2
the run window will appear. 
type gedit .bash_profile
gedit will open. add there everything you need. make sure you save the file in your home folder!!

---

### Post by jincast90 on 2006-10-08
Its still not working. This is how my .bash_profile looks like after I have added export PATH=$PATH:/home/myname/bin:

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

export PATH=$PATH:/home/myname/bin


So what I have I done wrong now?

---

### Post by jincast90 on 2006-10-09
Bump.

Still have´nt figured it out.

---

### Post by macphisto on 2006-11-01
I had the same problem, ~/.bash_profile didn't work, however adding "export PATH=$PATH:~/bin" (without the quotes of course) to ~/.bashrc did work for me.

---

### Post by ScarySquirrel on 2008-03-07
I had the same problem, after reading the [same article]("http://www.linuxcommand.org/wss0010.php").
I'm going to try adding "export PATH=$PATH:~/bin" (without the quotes of course) to ~/.bashrc.
I'll see if it works. 
P.S. Thanks for posting this.

---

