---
title: "ssh deamon"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by feiticeir0 on 2005-11-23
Hello all.

I've installed Ubuntu last night and as far it goes, i'm impressed...
Im not new to Linux, but new to Ubuntu and i've one question...
where is root ??? ;) 
I'm alredy familiar with the no root concept (since last night :D)..

My question is the following:
i've tried to start the ssh deamon but without sucess...
i've searched for ssh and the following apear:

OpenSSH (client and server) and SSH-Server.

witch one is the sshd ??
i've tried to exec /etc/init.d/sshd start and i get an error saying that the server keys are not generated...

how can i generate those keys ???

i've another question: 
how do i add and remove software from the runlevels ???

Cheers,

Bruno Santos

---

### Post by matthewv on 2005-11-23
By adding and removing software from runlevels, you mean from starting with that runlevel?? Just delete the links in /etc/rc#.d/ where # is the number of the runlevel

---

### Post by feiticeir0 on 2005-11-23
[QUOTE=matthewv]By adding and removing software from runlevels, you mean from starting with that runlevel?? Just delete the links in /etc/rc#.d/ where # is the number of the runlevel[/QUOTE]

Hi.
By adding and removing software from runlevels i mean that when starting ubunt (runlevel 5 - graphical) i want to start some services and others dont...

imagine i dont want the pcmcia services to start when im starting ubuntu (runlevel 5), how can i remove it ?

in Gentoo: rc-update [add | remove] service runlevel
Fedora/redhat/suse...: chkconfig --[add | del] service or chkconfig --levels [12345] service [on|off]

something like that...

---

### Post by odin on 2005-11-23
well I'm not sure if this is your what you need but there is a tool called rcconf.

just "sudo apt-get install rcconf"

to run it on a terminal just "rcconf"

see the man page cause maybe there you have a more accurate help to your needs.

hope this may help you out

---

### Post by odin on 2005-11-23
well this must look really stupid to you(posting 3 time a different thing about the same!!!)but I read in another thread about boot-up manager which looks great for your needs.

be sure you have the universe repo in our source.list and then 

sudo apt-get update
sudo apt-get install bum

to execute just run bum in a terminal or go to the sytem->administration menu,it should be there.

---

### Post by msr7x57 on 2005-11-25
I was just doing this - do you have "openssh-server" package installed? If you do it starts up automagically, and creates a "S20ssh" script in /etc/rc5d/ directory.

HTH

---

### Post by steve.horsley on 2005-11-25
How did you install the ssh server? I installed mine using the Synaptic GUI - under System / Administration. I didn't have to generate keys, so I assume the instaler did it for me. It also created te launcher in /etc/init.d and the symlinks to it. So if you installed it any other way, I suggest you remove it and install the openssh-server package. It works like a dream.

Steve

---

