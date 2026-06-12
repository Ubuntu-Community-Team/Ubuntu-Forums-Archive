---
title: "[SOLVED] Porting Desktop through SSH ?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-06
Ok. A scenario. 

I have two desktop computers. One with a monitor (of which I am using), and a second one, without a monitor. Both run Ubuntu, and the one I am using (with the monitor) is running Feisty Fawn. The other desktop (without the monitor) is running Dapper Drake.

Now, desktop pc #2, without the monitor, has openssh-server on it.
I was wondering if there was some way to port the entire desktop of pc #2 (without the monitor) to pc #1 (with the monitor), so I would be using the monitor I have for pc #2 which doesn't have a monitor.

I want to be able to have it display the entire desktop, and not just certain applications, like using the -X command in ssh. Is there any way to port the entire desktop interface of pc #2 over to the monitor, which is connected to pc #1 ?

Here, I even made a diagram in Dia to further explain myself, as I am probably confusing.

Anyone know how to do this?

Dr Small

---

### Post by irish_flu on 2007-09-06
Yep!  Use X forwarding (like you mention with the "-X command above) and run "gnome-session" as the app.

---

### Post by Dr Small on 2007-09-06
Umm, well that didn't work so well.
I tried it, a error message came up saying that gnome-session had too many sessions running, and then it somewhat had the desktop in the middle of the screen with what looked like *everything* (icons, windows, controls, menus, bars) all scrunched up in one little tiny comgloberation. 

So, I was thinking, is there some way to do it with "Remote Desktop"? Because I have never played with that any, and don't understand it altogether :P

Edit, I did get it to work this time, as I tried "sudo ssh -X user@host", and then "gnome-session".
But I'd still like to know if remote desktop would be better.

Dr Small

---

### Post by n3tfury on 2007-09-06
you can use VNC with or without SSH:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC)

---

### Post by asmoore82 on 2007-09-06
> **Dr Small said:**
> Umm, well that didn't work so well.
I tried it, a error message came up saying that gnome-session had too many sessions running, and then it somewhat had the desktop in the middle of the screen with what looked like *everything* (icons, windows, controls, menus, bars) all scrunched up in one little tiny comgloberation. 

So, I was thinking, is there some way to do it with "Remote Desktop"? Because I have never played with that any, and don't understand it altogether :P

Dr Small

[SIZE="4"]**if**[/SIZE] the connection does **not** need to be encrypted,
you could run 'gdmsetup' on the headless machine and enable XDMCP remote login.

Then you could use Xnest on the regular computer to open a session on the headless computer.

EDIT: a working "Xnest" substitute is already on Ubuntu: 'gdmXnestchooser' is what you would need.

---

### Post by reckless2k2 on 2007-09-06
ok...first of all....kill gdm on the desktop that has no monitor attached to it that you plan to SSH into. 

SSH in normal without X. then sudo chmod -x /etc/init.d/gdm

then restart that box with sudo shutdown -r now

now you that box is not wasting resources running an xserver that you don't plan on attaching a monitor to anytime soon. 

sounds like you've got sshd_config setup right on that machine. make sure ssh and sshd on both machines say xforward yes. it's just easier that way. then sudo /etc/init.d/ssh restart

so now on the machine with monitor you jump over to another console. you can have several running. so.....at your desktop now just hit

ctrl + alt+f2

you are at another console. (ctrl+alt+f7 will bring you back to the original) 

login as yourself and password. then type

xinit -- :1 vt12 (this starts X session on server 1. you are running F7 on :0) vt12 binds :1 to key F12. you can flip back and forth between F7 and F12 now...get it?

so now in that xwindow type

ssh -X ipoftheothermachine

once in the other machine type

startx


TA DA!!!!...in. now you can have machine 1 or F7 and flip to machine 2 on F12. get it?

just so you know...gnome sucks with most of those protocols.

---

### Post by tgalati4 on 2007-09-06
>ssh -2 -Y yourusername@yourmachinename
yourmachinename>gnome-panel

---

### Post by MetalMusicAddict on 2007-09-06
Here's how I connect to my server: **ssh -X USER@IP/HOST xfce4-panel** You can even put that in a launcher and it will prompt you for the password. Obviously add your info in the **USER@IP/HOST** part.

Now that command gets me the pic below. Notice the XFCE panel at the bottom. Everything can be accessed via the panel as if it were a actual XFCE desktop on my Gnome desktop

---

### Post by n3tfury on 2007-09-06
how do these other methods differ from using VNC out of curiosity?  i'd very much like to do the same kind of setup for a headless ubuntu file server i'm setting up.

---

### Post by Dr Small on 2007-09-06
[quote=reckless2k2]
so now in that xwindow type

ssh -X ipoftheothermachine

once in the other machine type

startx
[/quote]

I got eveything to work as far as "startx". It is feeding me errors about it doesn't have authority to make x server files and whatnot.

I did not do the "sudo chmod -x /etc/init.d/gdm", because I still want to be able to have x to run (as I will take this to the shop soon), and plus I want to use XDMCP, so by not running the above command, is that fouling things up?

Edit, instead of using "startx" i used "gnome-session", and it worked, but I can't close the terminal or I lose that X session :p

Dr Small

---

### Post by mlentink on 2007-09-06
> **MetalMusicAddict said:**
> Here's how I connect to my server: **ssh -X USER@IP/HOST xfce4-panel** You can even put that in a launcher and it will prompt you for the password. Obviously add your info in the **USER@IP/HOST** part.

I'm your fan, that's for sure. Just what I was looking for

---

### Post by reckless2k2 on 2007-09-06
well if you "close" the session then it won't run anymore. if you opened that session in vt12 then you can flip back to your machine at vt7. 

machine 1 - you are logged in to that desktop of machine 1. it's running on vt7 (F7)

machine 2 - you ssh into machine 2 from vt12 (f12) and start the desktop


NOW

machine 1 desktop is on F7 - ctrl+alt+f7 is machine 1

machine 2 desktop is on F12 - ctrl+alt+f12 is machine 2

if you close the session on f12 it will close out machine 2 desktop. 

got it?


also, startx should run everything fine if you have it bound to gnome-session. i might've missed if you are using xfce desktop. i use fluxbox over ssh because it works the best in my opinion. so instead of startx (because it's bound to gnome-session), i run startfluxbox when i ssh in to that remote box. 

sounds to me like you are already there but you don't understand that machine1 is running on one x server on that box and machine 2 is running on another x server on that same box.

it takes a little to grasp because of windows way of thinking. it took me a little time to untrain myself. sounds like you are there though already but you don't realize it.

---

### Post by Dr Small on 2007-09-06
I have it figured out now.
As a matter of fact, I had two other machines on different x servers, so I could switch back and forth between them with F7, F11 and F12. It works wonders :)

Thanks again for all of your help !

Dr Small

---

### Post by reckless2k2 on 2007-09-06
now your getting the idea. linux is multi-user at it's core. you don't have to logout either to go to another desktop. for instance, my wife is always on F7 so i don't want to knock her off if i'm at that machine. i just jump over to another console and startx on a different console for that machine. then i also ssh into other machines as well on other consoles. 

F7 - wife on local machine
F11 - me on local machine
F12 - me ssh to remote machine

similar to what you are doing now. it's all pretty simple. you can run gnome on one console as user A and run xfce on another console as user B for that machine.

have fun.

"upstate ny" - you'd have to run vnc through ssh to be "encrypted". in that case, vnc takes longer...more commands....why not just run X over ssh. safer..faster....the way it's typically done.

---

### Post by n3tfury on 2007-09-06
> **reckless2k2 said:**
> 

"upstate ny" - you'd have to run vnc through ssh to be "encrypted". in that case, vnc takes longer...more commands....why not just run X over ssh. safer..faster....the way it's typically done.

nice! thanks "yardley, pa, usa"

---

### Post by reckless2k2 on 2007-09-06
hahahaha....

no problem "upstate ny". i gather there's enough info here to already be running X over ssh already or using multiple consoles/terminals. 

the only time it gets a little sticky is when you want to run x over ssh from a windows box. in that case i suggest xwinlogon on the windows box. it's super easy to use and sshd is already setup on the linux box. since you've been using the linux commands for ssh, the xwinlogon gui should be cake. 

run "display number" other than 0 always just in case. 1 or 2

command = gnome-session, startkde, startfluxbox, etc for the desktop. 

the rest of the stuff is simple and or untouched. if you run X over ssh across the internet....USE COMPRESSION

here's the download page for xwinlogon if you ever need it:

[http://sourceforge.net/project/showfiles.php?group_id=124679](http://sourceforge.net/project/showfiles.php?group_id=124679)

---

### Post by n3tfury on 2007-09-06
YOU my friend are the MAN.  excellent info and bookmarked.  going to setup this weekend.  also, thanks for the xwinlogon because i dual boot one of my laptops with XP and that could very well come in handy.

---

### Post by reckless2k2 on 2007-09-06
no problem. feel free to hit me up if you have any problems.

---

### Post by Dr Small on 2007-09-06
> **n3tfury said:**
> YOU my friend are the MAN.  excellent info and bookmarked.  going to setup this weekend.  also, thanks for the xwinlogon because i dual boot one of my laptops with XP and that could very well come in handy.
He definatly does have some good info worth bookmarking. lol
I most likely will add a few of these commands to my FACL (frequently accesses command list) :D

Dr Small

---

### Post by reckless2k2 on 2007-09-06
well i'm glad i can be of help to at least 2 people. i'm giving back. doing my part. hahaha

---

### Post by Dr Small on 2007-09-06
I even tried this:

!! WARNING, DO NOT TRY THIS AT HOME !!
```
Ctrl+Alt+F2
$ sudo xinit -- :1 vt12
$ gnome-session
```

Just incase you have no idea what that does, it loads gnome-session as root! Very dangerous, but also very helpful if you are doing alot of administrator tasks and don't want to keep using gksudo ;) :p

Dr Small

---

### Post by pasta514 on 2007-11-09
> **n3tfury said:**
> how do these other methods differ from using VNC out of curiosity?  i'd very much like to do the same kind of setup for a headless ubuntu file server i'm setting up.

I have attempted to do the same using VNC.  I have tried no other method, yet.  After finally getting it working I was reasonably happy, until I yanked the graphics card out of the headless machine to save the power and to use the card elsewhere.  Guess what?  It doesn't work now... :( I suppose since VNC forwards the actual desktop if there is no desktop to display it can't be forwarded.  Just a guess...

Good thread.  I'll be trying these other options next.

---

