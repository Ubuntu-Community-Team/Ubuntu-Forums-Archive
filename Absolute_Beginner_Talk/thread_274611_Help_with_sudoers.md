---
title: "Help with sudoers"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by psychkiku on 2006-10-10
Hi Guys,

Sorry to ask a silly question but I am having some issues with sudoers. I have read numerous different posts from different forums but I still have not been able to accomplish my task.

This is what is happening: I run ubuntu 6.06 on my laptop and everything runs smoothly. I have firestarter installed and I wish to run the GUI frontend duing bootup.I know that firestarter shouldload during boot and the GUIis just for show but I would like it to load. I have read posts telling me to add my user to the sudoers file so I can run the firestarter service and not have to enter a password for root. I added my entry to the sudoers files as follows:

username ALL=NOPASSWD: /usr/sbin/firestarter

Then I added the command to the startup list in the sessions dialog box as follows:

sudo firestarter --start-hidden

I also tried the relative path as well (/usr/sbin/firestarter ....) in the sessions dialog box.

Anyways this did not work when I rebooted the firestarter GUI did not load and either did firestarter.

I decided to check that the sudoers was edited correctly by adding a simple command of:

username ALL=(ALL) ALL

I tried doing something that required root priviledges and it did not work. Am I doing something wrong. Some helpwould be appreciated.

Thanks

ps sorry about the rant.

---

### Post by kerry_s on 2006-10-10
The sudoers is a read only file. To make the changes you can make it writeable, but as soon as your finished you have to change it back to read only or it will break sudoers.

So the steps->
sudo nautilus /etc
right click sudoers,make writable
open with gedit and make your changes
right click and change back to read only

Now if your already stuck and can't access sudo, use failsafe or
you can boot from the livecd and fix it by changing it back to read only or if you have a nother linux install you can do it from there.

---

### Post by 5-HT on 2006-10-10
[quote=psychkiku] Then I added the command to the startup list in the sessions dialog box as follows:

sudo firestarter --start-hidden [/quote]

That is where I believe the problem lies.

To get the Firestarter GUI to start automatically in Dapper a little fooling around is needed. 
Your sudoers file should be good. To test it, can you start Firestarter from a terminal with *sudo firestarter? *
The problem is with getting the Firestarter GUI to start automatically.
Instead of simpply adding *sudo firestarter --start hidden* to the sessions startup list you'll need to make an executable script containing the following text and add the script to the startup list:

```
#!/bin/bash
xhost +local:
sudo firestarter --start-hidden --display :0.0
sudo -k
exit 0 
```Name and save the script somewhere (e.g. ~/scripts/firestarter_start.bash), make it executable
```
 chmod +x ~/scripts/firestarter_start.bash 
```and add the script to the startup list.

Hope that helps

[quote=psychkiku]
I know that firestarter shouldload during boot and the GUIis just for show...[/quote]

*should* load, but does it? [https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647](https://launchpad.net/distros/ubuntu/+source/firestarter/+bug/59647)

---

### Post by hw-tph on 2006-10-10
kerry_s, that is exactly the way *not* to do it. To edit the sudoers file you use the command **sudo visudo**. This will make sure that the syntax is correct when you save it so you do not break sudo altogether. You can use the VISUAL or EDITOR environment variables to use the editor of your choice.


Håkan

---

### Post by psychkiku on 2006-10-10
Hi Thanks for the reply but that does not really help me. I am able toedit the sudoers file with visudo and can save it. When I check the properties of the file after editing it they are read only. 

Thanks anyways

---

### Post by psychkiku on 2006-10-10
Thanks HT-5,

I think my sudoers file is not working properly. I tried the command:

sudo firestarter

Here is the output:

psychkiku@chiwilinux:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5557): Gtk-WARNING **: cannot open display:

Any ideas?

---

### Post by petri on 2006-10-10
> Any ideas?

Yes, just forget about it. In Linux you just don't need a firewall or should I say you don't need to see the GUI all the time. It does not function the same as windows where you have to answer and check out it all the time (ZoneAlarm). 

Relax and use your time more efficiently. Are you running a server or something like that (with internet) you need to configure your **iptables** (with Firestarter, GuardDog) and then again forget it. Instead of firestarter icon visible add Weather report so you can see when you can go out :rolleyes:  8)

---

### Post by 5-HT on 2006-10-10
> **psychkiku said:**
> Thanks HT-5,

I think my sudoers file is not working properly. I tried the command:

sudo firestarter

Here is the output:

psychkiku@chiwilinux:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5557): Gtk-WARNING **: cannot open display:

Any ideas?

Does that happen with any graphical application that requires root privileges (e.g. synaptic, the administration utilities) or just with firestarter?

Best thing to do is, using visudo, undo any changes to made to /etc/sudoers and add only this one line (adding your username) to the bottom of the file
```
username ALL=(root) NOPASSWD: /usr/sbin/firestarter/ 
```

Then, try to start the Firestarter GUI: ```
gksudo firestarter 
```
If you get the same error, enter this in a terminal ```
 xhost +local: 
```. Firestarter should then start from the terminal without needing a password and you can continue with the rest of my ealier guide.

---

### Post by petri on 2006-10-10
And guys, why are you all advicing **psychkiku** to use sudo wiht a graphical prgram? Read [https://help.ubuntu.com/community/RootSudo#head-0c932eb3f1619126fc8307ee7690f462552d34ec](https://help.ubuntu.com/community/RootSudo#head-0c932eb3f1619126fc8307ee7690f462552d34ec)
and ***Example # 2*** That will surely keep yourselves out of trouble too. \\:D/ 


Never use sudo with a graphical programs!

---

### Post by 5-HT on 2006-10-10
> **petri said:**
> And guys, why are you all advicing psychkiku to use sudo wiht a graphical prgram?  Because it is required in this case in order for the guide to work. If you can find a way to get the Firestarter GUI to load automatically without a password on session startup and without using sudo then please let us know. 


> **petri said:**
>  Never use sudo with a graphical programs!   It's always best to avoid launching graphical apps with sudo, but not always necessary (e.g. gedit).Thanks for the warning though, it is one to be aware of.

---

### Post by psychkiku on 2006-10-10
Thanks heaps guys, the advice from HT-5 worked. I added the script and it has worked. Thansk heaps to all of you.

Apreciated.:-D

---

### Post by kerry_s on 2006-10-10
> **hw-tph said:**
> kerry_s, that is exactly the way *not* to do it. To edit the sudoers file you use the command **sudo visudo**. This will make sure that the syntax is correct when you save it so you do not break sudo altogether. You can use the VISUAL or EDITOR environment variables to use the editor of your choice.


Håkan


Yeah, your right, that is the way it should be done. I have a bad habit of just going straight to it if i'm already in root file manager. I really got to start doing it the right way. ;)

---

### Post by TheWizzard on 2006-10-10
a script to launch firestarter at bootup is crazy, useless and a serious security tread! 
> I know that firestarter shouldload during boo
nope. firestarter does not load during bootup. firestarter is not your firewall! iptables is. 
firestarter is an iptables configuration tool. there is no use to make scripts to start this tool at bootup.

---

