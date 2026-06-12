---
title: "HowToStart a Script (fileOperations)WhenLinux start up (main startup of the machine)?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-11
I looked in init.d
and also in rc0.d

how does it work?

I just would like to do ...
some mount stuffs a bit 
and also chmod 666 /dev/dsp
chmod 666 /dev/dsp1
  
each time that my pc restart ? How is it posisble ?

thank you very much 
patrick

---

### Post by grinchy on 2005-10-11
As in you just want to run a script when the system starts?

go to System>Preferences>Sessions and have a look around
(Sorry not writing this from ubuntu so can't be precise)

---

### Post by davmac on 2005-10-11
There are a couple of ways to do this. As grinchy mentions, you can use the system->preferences->sessions to add your script. This will run your script just when you log in.

If you want to run it for everyone who logs onto the machine, put the script in the /etc/init.d folder, and type "sudo update-rc.d myscriptname defaults" to add it to the start up sequence.

HTH,

Dave Mac

---

### Post by SilentCacophony on 2005-10-11
System>Preferences>Sessions>Startup, then add the script names. For info on scripting:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Also, for mounting, you can add entries in */etc/fstab* to make them take effect at every boot, or issue **sudo mount -a** to mount what's in that file from the current session.

---

### Post by patrick295767 on 2005-10-11
[QUOTE=grinchy]As in you just want to run a script when the system starts?

go to System>Preferences>Sessions and have a look around
(Sorry not writing this from ubuntu so can't be precise)[/QUOTE]

I installed Ubuntu as server ... 
and I am using fluxbox (rather fast).
 
I'll try to find where is "System>Preferences>Sessions" in my menu... i hope I'll find it... 

thank you

---

### Post by patrick295767 on 2005-10-11
[QUOTE=davmac]
If you want to run it for everyone who logs onto the machine, put the script in the /etc/init.d folder, and type "sudo update-rc.d myscriptname defaults" to add it to the start up sequence.
[/QUOTE]

I'll try this ... and will let you know about my progress !
  
  
Btw, since u know much, if I wanna start a script-bash file (root privilege) at start of tty-console   and    start of X-server for the user ?
What should I do ?
  
Thank you very much,
(That's not very common questions)

Patrick

---

### Post by rimmer on 2005-10-11
[QUOTE=patrick295767]I installed Ubuntu as server ... 
and I am using fluxbox (rather fast).
 
I'll try to find where is "System>Preferences>Sessions" in my menu... i hope I'll find it... 

thank you[/QUOTE]

Well there is another less profi way to access the gnome desktop through flux.

Add this to your flux menu or just the command in a shell.    
```

[submenu] (System)
[exec] (Login Nested) {gdmflexiserver --xnest}
[end]

```
And It is not a real answer to your question but I have found that it helps sus things out a little more if your using an other desktop
A little of topic I know !

---

### Post by patrick295767 on 2005-10-12
[QUOTE=rimmer]Well there is another less profi way to access the gnome desktop through flux.

Add this to your flux menu or just the command in a shell.    
```

[submenu] (System)
[exec] (Login Nested) {gdmflexiserver --xnest}
[end]

```
And It is not a real answer to your question but I have found that it helps sus things out a little more if your using an other desktop
A little of topic I know ![/QUOTE]


Thank you very much !! Even difficult questions can be reply !!
I will try this evening 

I really like Linux Community !!

---

### Post by patrick295767 on 2005-10-12
errata: replied

---

### Post by patrick295767 on 2005-10-12
[QUOTE=davmac]
If you want to run it for everyone who logs onto the machine, put the script in the /etc/init.d folder, and type "sudo update-rc.d myscriptname defaults" to add it to the start up sequence.

[/QUOTE]



I tried sudo update-rc.d myscriptname defaults
and it's workign damn great !!!

Thank you very much...
I can now start my scripts !!
This script is running when i switch on the PC 
but also when I do : halt or reboot.

My next plan is to use 2 scripts : one at the shutdown and one when PC is switched on... 
I still dont know how

Thank you again !

Pat'

---

### Post by davmac on 2005-10-12
Patrick,

Have a read up about runlevels - there are what control the scripts that run during different types of start up and shutdown.

Then when running update-rc.d, instead of using the "defaults" option you can specify which runlevels should trigger the script.

I've not had a go at doing this myself so can't give you specific examples.

AFAIK Ubuntu's use of runlevels is the same as Debian's and you can read more about it at [http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)

HTH,

Dave Mac

---

