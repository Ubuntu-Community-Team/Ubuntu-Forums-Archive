---
title: "I've searched and can't find answer.  Remote Graphical Desktop"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by NoOne2 on 2006-08-26
I have my pieces and parts Unbuntu machine sitting on my desk and I'd like to regulate it to the floor.

What I want to do is access it, via a graphic desktop on my PC, basically the Ubuntu Desktop session in a window on the PC.

Can't I just find a X client for XP and have it connect back to my machine?  I'm thinking thats the way to go but am having a very hard time finding a freeware XP X Client.

I know what I'm looking for but I must be missing the correct word when I'm searching.

Thanks!

---

### Post by Pragmatist on 2006-08-26
> **NoOne2 said:**
> I have my pieces and parts Unbuntu machine sitting on my desk and I'd like to regulate it to the floor.

What I want to do is access it, via a graphic desktop on my PC, basically the Ubuntu Desktop session in a window on the PC.

Can't I just find a X client for XP and have it connect back to my machine?  I'm thinking thats the way to go but am having a very hard time finding a freeware XP X Client.

I know what I'm looking for but I must be missing the correct word when I'm searching.

Thanks!

This should do the trick:

[http://x.cygwin.com/](http://x.cygwin.com/)

Also, check these out as well:
[http://www.cygwin.com/](http://www.cygwin.com/)
[http://www.colinux.org/](http://www.colinux.org/)

---

### Post by zinner on 2006-08-26
> **NoOne2 said:**
> I have my pieces and parts Unbuntu machine sitting on my desk and I'd like to regulate it to the floor.

What I want to do is access it, via a graphic desktop on my PC, basically the Ubuntu Desktop session in a window on the PC.

Can't I just find a X client for XP and have it connect back to my machine?  I'm thinking thats the way to go but am having a very hard time finding a freeware XP X Client.

I know what I'm looking for but I must be missing the correct word when I'm searching.

Thanks!


Or u could install tight-vnc.

[http://www.google.com/search?hl=no&q=tight+vnc&btnG=Google-s%C3%B8k&lr=](http://www.google.com/search?hl=no&q=tight+vnc&btnG=Google-s%C3%B8k&lr=)


..The info is out there...

---

### Post by NoOne2 on 2006-08-26
Ok...I have the files and try to compile it with no luck at all.

Is there a primer somewhere on compiling/Making programs?

One of my big issues with Linux/Unix is the lack of tutorials which cover the very basics.  Plenty of how-to's but nothing that explains the reasoning behind each step.  There is a lot of assumptions when you read the directions for most of this software.

Thanks

---

### Post by 505 on 2006-08-26
You don't need to compile anything. In ubuntu, first enable remote desktop. Go to System->Preferences->Remote Desktop and select 'Allow'. Uncheck ask for confirmation, and it's best to set a password.

Now, in Windows download [RealVNC](http://www.realvnc.com/), the free version is good enough. Start the program, enter you Ubuntu's IP address, and you should have your desktop.

(The connection between Windows and Ubuntu is not secured. If you want encryption, you have to run in over SSH, and your Windows machine needs Putty to do that. There are tutorials on the internet on how to do that.)

---

### Post by bodhi.zazen on 2006-08-26
Compile what? I think all the programs to date in this post are for Windows and do not need to be compiled.

General steps:

1. Download source code.

2. Extract form archive (tar).

3. cd into new extracted folder.

4. READ the README.

5. In a terminal:
./.configure
make
sudo make install

I advise you use checkinstall rather then install.

sudo checkinstall

You will need to install checkinstall with apt-get or synaptic.

You will likely need to install the Linux headers and some development files.

Read any error messages, they will tell you what else you may need to install (dependencies).

---

### Post by NoOne2 on 2006-08-26
Thanks.  I was under the impression I also needed to install the VNC software on the Linux side.

Its working fine, thanks again.

I'd still like to understand the make/install process better and would prefer to do remote X so that I can just leave the computer in the corner, no monitor or anything else.

I tried Cgywin but am not sure how to setup the Unbuntu side to export an X session.

I'm familiar with export:display but again I want to login, not just export a session.

---

### Post by bodhi.zazen on 2006-08-26
Use ssh to log into Ubuntu.

Windows ssh client = Putty.

configure Ubuntu ssh to forward  (I think this is the default behavior).

In Cygwin, Look at X, use Fullscreen option.

---

### Post by NoOne2 on 2006-08-26
Ok...I've gotten Putty but how do I configure the Untuntu side to accept a SSH login?

I've read on SSH, including the Putty docs but nothing on how to configure the other end.

I've read I need to install some kind of SSH client.

I appreciate the information and the help but as I've said there is a huge gap in instructions for Linux in that there are so many assumptions about what someone knows.  I get a lot of "type this" directions but what I want to know if the reasoning why things are the way they are since once you understand a process it is a lot easier to figure out on your own.

Like you said login using SSH.  I assume your talking about picking the SSH option in Putty, which I've tried but keep getting an error about connection refused which I assume is because I do not have the Linux side setup.

---

### Post by bodhi.zazen on 2006-08-26
Putty is your ssh client.

Add your youself to the ssh group (in Ubuntu) to enable log in.

---

### Post by NoOne2 on 2006-08-26
Where do you do these things?

I've tried to edit the ssh_config file, can't save it, even logged in as the admin.

Everytime I try to run 'ssh -F ssh_config' I get the list of commands...I have never used any of these programs before so I need the step by step.

---

### Post by 505 on 2006-08-26
You also need to install SSH on your Ubuntu computer, I don't think it is installed by default. Just type 'sudo apt-get install ssh'

---

### Post by NoOne2 on 2006-08-26
Ok I added myself to the SSH group, found that part.

I installed the SSH side also from your command.

I can login but now just get a shell.

---

### Post by mdecler2 on 2006-08-26
There are some options that you should be able to configure in puTTY to allow X capabilities. Unfortunately, I have hardly been able to get this "X forwarding" option to work with puTTY. However, I have been able to forward X using ssh in Cygwin. I believe the command would go something like this:
```
ssh -X username@IPaddress
```

To reiterate, look through the options pane that appears in the puTTY window on the left side before you try to login, find the "x forwarding" option and fiddle with that.
If all your efforts are unsuccessful, I suggest to then try Cygwin with openSSH installed with it and read the man pages about the -X option.

---

### Post by bodhi.zazen on 2006-08-26
You can ssh via Cygwin, less options then Putty.

In Putty, one of the options is X forward. Choose this before you log onot Ubuntu.

Once you log onto Ubuntu

```
export DISPLAY=192.168.1.50:0 #enter your Windows IP address, use :0
startx
```

---

### Post by inhumanbean on 2006-08-26
I use cygwin. Just install cygwin and then you can connect to the desktop using somthing like this:

X :1 -query <hostname>

where hostname is the hostname or ip address of the ubuntu box. Also make sure you enable remote connections System->administration->login Window
click on the remote tab and select something other than "remote desktop is disabled"


Good luck!

---

