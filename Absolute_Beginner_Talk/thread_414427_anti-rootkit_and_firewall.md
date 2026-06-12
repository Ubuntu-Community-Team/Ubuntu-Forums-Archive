---
title: "anti-rootkit and firewall"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by DO55 on 2007-04-19
hi

1- i use this code to install chkrootkit  
> sudo apt-get install chkrootkit rkhunter
[http://ubuntuforums.org/showthread.php?t=380674&highlight=chkrootkit](http://ubuntuforums.org/showthread.php?t=380674&highlight=chkrootkit)

after i  paste this code and wait until it finsh from downloading i try to find the software in the applications list but i cant find it !! why ?



2-do i need firewall or the firewall in ubuntu is enough ?

3-dose the firewall enable by default, ?

---

### Post by Sef on 2007-04-19
> 1- i use this code to install chkrootkit
Quote:
sudo apt-get install chkrootkit rkhunter
[http://ubuntuforums.org/showthread.p...ght=chkrootkit](http://ubuntuforums.org/showthread.p...ght=chkrootkit)

after i paste this code and wait until it finsh from downloading i try to find the software in the applications list but i cant find it !! why ?

To find it, try this:  System > Preferences > Main Menu

> 2-do i need firewall or the firewall in ubuntu is enough ?

3-dose the firewall enable by default, ?

The firewall in Ubuntu is enabled by default and it is enough.

---

### Post by autocrosser on 2007-04-19
Open a terminal & either type:
sudo chkrootkit  or sudo rkhunter

to run (they only run in a terminal--you could create a custom launcher for them if you want/need to)

Firestarter is the default firewall...it runs in the background without a GUI. You can just install Firestarter which will give you a bright, shiny GUI to use. It's all you really need:)

---

### Post by DO55 on 2007-04-19
Sef  

i did not find it  but the method from autocrosser  work great 


autocrosser  
thanks with anti-rootkit

but i did not understand you when you said  "Firestarter is the default firewall.. You can just install Firestarter "

you said its default but why i need to install it again ? 
do you mean there is two type of Firestarter GUI and non-GUI ?
and how can i install it ?

---

### Post by n3tfury on 2007-04-19
> **DO55 said:**
> Sef  

i did not find it  but the method from autocrosser  work great 


autocrosser  
thanks with anti-rootkit

but i did not understand you when you said  "Firestarter is the default firewall.. You can just install Firestarter "

you said its default but why i need to install it again ? 
do you mean there is two type of Firestarter GUI and non-GUI ?
and how can i install it ?

ubuntu comes *with* a firewall, but the actual *GUI* he's referring to is Firestarter, which doesn't come with Ubuntu.

---

### Post by DO55 on 2007-04-19
now i understand 

i try to search Firestarter in add/remove  but i cant find it

---

### Post by n3tfury on 2007-04-19
open up a terminal and do

```
sudo aptitude install firestarter
```

or just install it via synaptic

---

### Post by DO55 on 2007-04-19
i run the code  but i cant find firestarter in applications list

---

### Post by autocrosser on 2007-04-20
Should be in System>Administration:)

You might need to log out & back in (but I don't think so)

And the "good" command for rkhunter:

sudo rkhunter -c

Will do a complete scan....

---

### Post by DO55 on 2007-04-24
thank you all :)


in preferences > icmp filter 
do i need to enable icmp filtering ?
do i need to let Firestarter work in task bar or just close it ?
how can i send it to task bar ? when i press x its close (i cant the see the  icon  it in the task bar )


**im just using the computer for opeing web pages and download files and torrent 
and im usind router

---

### Post by autocrosser on 2007-04-25
FireStarter has a very good website explaining all the options.

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by eentonig on 2007-04-25
I think you're a bit confused.

Firestarter is just a front-end/GUI which allows you to configure you FW. You don't need it to run your firewall, but in that case, you would need to configure your FW settings by hand in the configfiles.

However, in my opinion... you don't need to do anything. When you install a fresh windows, it listens on all kind of open tcp (application~server) ports. Even if you don't actually need them. This allows for bad people to connect to these open 'doors' and make use on their weeknesses.

When you install Ubuntu, there are NO server programs/open tcp ports installed by default. So if anyone tries to connect to your pc from the outside, he nocks on the door but nobody answers.

---

### Post by Patrick K on 2007-04-25
Firestarter is the GUI frontend for iptables which is the default (and installed) firewall for Ubuntu (and most other distros). You do not need Firestarter to be protected. Iptables can be completely configured from the command line. Firestarter is just a user friendly way to access iptables features. It doesn't add any more functionality it just writes to the configuration files  for you. You do not need it to be running to be protected. Once you have made any changes you can close it and the iptables firewall with use those changes. 

Here is the user documentation. At the bottom is the manual in pdf format. It's not enthralling reading but not bad for a user manual.
[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

