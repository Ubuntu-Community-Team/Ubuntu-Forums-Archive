---
title: "Autologin to XFCE?"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2006-01-10
Alrighty, I'm about to install XFCE on my old computer. I've been searching on how to autologin and start XFCE automatically, but I can only find stuff on how to make GDM/KDM or even XDM to that, which I won't be installing. Is there any (easy) way to accomplish this?

---

### Post by Nanaki on 2006-01-11
Anyone? :(

---

### Post by carlosqueso on 2006-01-11
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)  Does this help?  Of course, you'd want to use ```
exec xfce4-session
``` at the bottom of your configuration file.

---

### Post by Thirsteh on 2006-01-11
Sorry, nevermind this post, didn't read the original post thoroughly.

---

### Post by aysiu on 2006-01-11
[QUOTE=Nanaki]I can only find stuff on how to make GDM/KDM or even XDM to that, which I won't be installing.[/QUOTE] Can you explain what you have against installing GDM?

---

### Post by patrick295767 on 2006-01-11
[QUOTE=aysiu]Can you explain what you have against installing GDM?[/QUOTE]
  
He's certainly against ram use (i dont know if it's really taking a lot)...
 
Anyhow, to make it !
So, we'll use the script of the boot /etc/rc2.d
  
Make a file : 
/etc/init.d/S98autologin.sh
or 
/etc/init.d/S75autologin.sh
```
#!/bin/bash
echo "Hi, I am gonna try to start the session ... " 
su username
startx
```
  
Then, u may do the symbolic link (ln -s) 
or use rox to do it : 
/etc/init.d/S98autologin.sh        to /etc/rc2.d/S98autologin.sh  
  
I have no linux to check if it's working... 
 I just thinking, not accurate reply.
 
U may try and let us knwo if it's working. 
   
----------------------------------
easier way:
```
apt-get -f -y install gdm
```
```
sudo gdmsetup
```
  
Then, u may set up v. easily the autologin 


--------------------------------
Give me a feedback if u managed !
  
Greetz

Pat'

---

### Post by patrick295767 on 2006-01-11
[http://www.ubuntuforums.org/showthread.php?t=64557&page=8](http://www.ubuntuforums.org/showthread.php?t=64557&page=8)

---

### Post by Nanaki on 2006-01-11
> **carlosqueso][https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)  Does this help?  Of course, you'd want to use ```
exec xfce4-session
``` at the bottom of your configuration file.[/QUOTE]

Thanks, this solves the XFCE4 problem, but it doesn't autologin I guess?

[QUOTE=aysiu]Can you explain what you have against installing GDM?[/QUOTE]

128MB RAM has something against it.  said:**
> ...

I know squat about Linux, but wouldn't I have to put the password anywhere in that script?

---

### Post by patrick295767 on 2006-01-11
[QUOTE=Nanaki]Thanks, this solves the XFCE4 problem, but it doesn't autologin I guess?



128MB RAM has something against it. ;)



I know squat about Linux, but wouldn't I have to put the password anywhere in that script?[/QUOTE]
  
AAAAhh, so instead of su
u may enter gksu if I recall well or sthg like that
  
I already asked this question at the beginning .... 
It's possible

Greetz'

---

### Post by patrick295767 on 2006-01-11
[http://ubuntuforums.org/showthread.php?t=97944&highlight=script](http://ubuntuforums.org/showthread.php?t=97944&highlight=script)

---

### Post by aysiu on 2006-01-11
[QUOTE=Nanaki]
128MB RAM has something against it. ;)[/QUOTE] I have an old eMachines computer with 128 MB of RAM, and it works fine with Xubuntu and GDM.

---

### Post by patrick295767 on 2006-01-12
```
gksu -u UserName startx
```
  
for instance:
((when root)
```
 gksu -u UserName xterm
```
works
  
Let me know ab. ur progresses !
  
Greetz'

Pat'

---

### Post by patrick295767 on 2006-01-12
ERRATA
In my previous Post, please replace su by sudo
then u get
```
gksudo -u UserName xterm
```
  
Oup's 
sorry

---

### Post by patrick295767 on 2006-01-12
[QUOTE=aysiu]I have an old eMachines computer with 128 MB of RAM, and it works fine with Xubuntu and GDM.[/QUOTE]
  
Me, with the old pc,300Mhz AMD & 64MB ram, it's rather impossible ...
  
I guess I'll have to get some additional ram from Compaq web site. Costs a lot maybe...

---

### Post by patrick295767 on 2006-03-02
you managed with this post ... did you solve ur prob ??

Greetz

---

### Post by Nanaki on 2006-03-02
I forgot about this. Due to exams, I kinda stopped working on it. Maybe I'll try it again in the near future. I'll first see how well Gnome runs.

Thanks for your help, nevertheless. :)

---

### Post by patrick295767 on 2006-03-02
gksu 
and gksudo   are with X
   
   
u may use : 
su 
or ```
sudo -u username  ls ~
```
  
I made a script right now with using such thigns ... 
it works very fine

Greetings 

Pat'

---

### Post by diebels on 2006-03-09
For automatic startup, without password:
~$ sudo gedit /usr/bin/auto_login
insert: (where YOUR_USERNAME is the user to log in)
```
#! /bin/sh
/bin/login -f YOUR_USERNAME
```

make it executable:
~$ sudo chmod +x /usr/bin/auto_login

change inittab:
~$ sudo gedit /etc/inittab
replace the line:
```
1:2345:respawn:/sbin/getty 38400 tty1
```
with:
```
1:2345:respawn:/sbin/getty -n -l /usr/bin/auto_login 38400 tty1
```

make xfce start when you 'startx'
~$ gedit ~/.Xclients
insert:
```
startxfce4
```

Insert startx command with test for running X in .bashrc (put it on the top of the file):
~$ gedit ~/.bashrc
```
case `/usr/bin/tty` in /dev/tty[0-9]*)
        XPID=$(/bin/pidof xinit)
        if [ -z "$XPID"] ; then
                startx -- -dpi 120 -nolisten tcp; exit
        fi
esac

```
-- -dpi 120
and
 -nolisten tcp
is optional

Remove gdm from runlevel 2:
~$ sudo rm /etc/rc2.d/S13gdm

---

