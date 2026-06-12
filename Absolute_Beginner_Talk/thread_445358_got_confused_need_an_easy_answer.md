---
title: "got confused need an easy answer"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-05-15
My challenge is to remotely access my ubuntu desktop from work using a windows computer
my home computer is also behind a router firewall.
how do I do this?
I did some previous reading bumped into something called VNC which really confused me
is there a guide for this somewhere?

thanks in advance,
Gevorg

---

### Post by Dr Small on 2007-05-15
```
sudo apt-get install openssh-server
```
This will install SSHd.

Now, open firestarter, go to "Policy", and click down in "Allow Services".
Go up and click "Add rule", select SSH under name, leave the rest of the settings the same, and click "Add".

Set up your router for port forwarding on port 22 to your network IP, get Putty and put it on a pen drive, go to your Work Windows Computer, plug in the pen drive, run putty, connect to your IP and you are now remotely connected to your openssh-server, at your computer ;)

Dr Small

---

### Post by reidms on 2007-05-15
Hello-

First of all I just think you need to forward your ports on your router for the remote access that you will use(Which ports depend on what protocol you are using)

VNC is a way to view your desktop from another computer.  It shows what you would see if you were actually on the computer.

Check this link out mate!

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Access)

Hope this helps!

---

### Post by FuturePast on 2007-05-15
And if you wanted you could run VNC through an SSH-tunnel.

---

### Post by reidms on 2007-05-15
The SSH method will work, but it will not provide GUI(Graphical User Interface- like point click)

However SSH is quite handy for just running commands on a machine remotely(like updating Ubuntu while at work, or shutting down the computer)

---

### Post by Gmbrdilos on 2007-05-15
see, I am getting confused again :)
I want to use it like I would use it if I was home (see the desktop so to speak)

---

### Post by Dr Small on 2007-05-15
> **Gmbrdilos said:**
> see, I am getting confused again :)
I want to use it like I would use it if I was home (see the desktop so to speak)
I prefer CLI better, that's why I recommended SSHd, as it allows you to run commands in the command line, and still see you files with ls, cd and such. :)

Dr Small

---

### Post by reidms on 2007-05-15
> I want to use it like I would use it if I was home (see the desktop so to speak)

You want to go with VNC then mate :)

From ubuntuguide.org
Do this to your Ubuntu machine
```
 How to configure remote desktop (not secure)

    * Read #General Notes 

    Warning! Remote Desktop will only work if there's a GNOME login session 
    Leaving computer with an unattended GNOME login session is not secure 
    Use (System -> Lock Screen) and switch off the monitor when computer is left unattended 

    * System -> Preferences -> Remote Desktop
    * Remote Desktop Preferences 

Sharing ->
Allow other users to view your desktop (Checked)
Allow other users to control your desktop (Checked)

Security ->
Ask you for confirmation (Un-Checked)
Require the user to enter this password: (Checked)
Password: Specify the password

```

Do this to the windows
```
 How to connect into remote Ubuntu desktop via Windows machine

    * Read #General Notes 

    e.g. Assumed that remote Ubuntu machine have configured Remote Desktop 
    Read #How to configure remote desktop (not secure) 
    Remote Ubuntu machine: 192.168.0.1 

    * If you have a router remember to open the appropiate port. The default one is 5900 

    This process is called port forwarding port forwarding 

    * Download DotNetVNC: Here or RealVNC Here 

    this is a free DotNet version that require the DotNet framework available from microsoft here 
    The RealVNC website was created and maintained by the original developers of VNC during their time at AT&T. RealVNC comes in Free, Personal, and Enterprise editions - the latter two costing money. 

    * Open the VNC client you have chosen, and insert the connection string formatted like this <LINUX BOX IP><:DESKTOP NUMBER>|<::PORT> 

    In example use: 192.168.1.2:0 or 192.168.1.2::5900 to connect to desktop 0, to connect to desktop 1 use 192.168.1.2:1 or 192.168.1.2::5901 and so on 
```

---

### Post by Gmbrdilos on 2007-05-15
thanks for the guide,
I decided to choose a client called tightvnc (which is pretty much the only one running from a USB drive that I have found, if you know better let me know)
and I kinda got confused on the last line of the guide, about the connection string

---

### Post by reidms on 2007-05-15
What type of router do ya have?

---

### Post by Dr Small on 2007-05-15
No matter what router he has, he can go to:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

find his router, and specific instructions on how to set up port forwaring ;)

Dr Small

---

### Post by Gmbrdilos on 2007-05-15
I have a 2wire 1070-B Gateway that came with my SBC internet service.

---

### Post by Dr Small on 2007-05-15
[http://www.portforward.com/english/routers/port_forwarding/2wire/1070-B/default.htm](http://www.portforward.com/english/routers/port_forwarding/2wire/1070-B/default.htm)

---

### Post by reidms on 2007-05-15
> **Dr Small said:**
> No matter what router he has, he can go to:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

find his router, and specific instructions on how to set up port forwaring ;)

Dr Small

Yep- was gonna look it up for em- but ya beat me to it :D


Tell us if you have any further problems!

---

### Post by Gmbrdilos on 2007-05-15
I know how to do port forwarding, done it before
I just don't understand what am I supposed to type in the field that says VNC server on my vnc veiewer
do I just type my IP or something with it?

---

### Post by reidms on 2007-05-15
Correct!

At your home computer find your ip by going to a site like whatismyip.com

---

### Post by Dr Small on 2007-05-15
I've never used VNC, but I assume that the server would be your IP, like the host / server for sshd is your IP. :D

Dr Small

---

### Post by trak87 on 2007-05-15
> **reidms said:**
> The SSH method will work, but it will not provide GUI(Graphical User Interface- like point click)

Not to argue the point made, but for the sake of clarity it is possible to run gui programs when connecting from Linux to Linux via ssh. Use the -X -Y options and you can run any remote graphics program:

Log in with something like this:

```
ssh -X -Y name@192.168.1.125
```

Now try running gedit!

---

### Post by reidms on 2007-05-15
> **trak87 said:**
> Not to argue the point made, but for the sake of clarity it is possible to run gui programs when connecting from Linux to Linux via ssh. Use the -Y (or -X, but -Y seems to be more secure) option and you can run any remote graphics program:

Log in with something like this:

```
ssh -Y name@192.168.1.125
```

Now try running gedit!

I was not aware of the -X or -Y

Learned something new :D

But he is connecting from a windows computer :/

---

### Post by Dr Small on 2007-05-15
> **trak87 said:**
> Not to argue the point made, but for the sake of clarity it is possible to run gui programs when connecting from Linux to Linux via ssh. Use the -Y (or -X, but -Y seems to be more secure) option and you can run any remote graphics program:

Log in with something like this:

```
ssh -Y name@192.168.1.125
```

Now try running gedit!
Yes, but that won't run GUI programs in Putty on a Windows Pc will it?
I thought you had to have x or something...

Dr Small

---

### Post by Gmbrdilos on 2007-05-15
> **reidms said:**
> Correct!

At your home computer find your ip by going to a site like whatismyip.com

thanks, just tried from neighbor's laptop, works great.
and a question: do I have to stay logged in on the home computer to use it at work?


@trak87
I just came out of state of confusion, don't drag me back in there :lol:

---

### Post by Dr Small on 2007-05-15
> **Gmbrdilos said:**
> thanks, just tried from neighbor's laptop, works great.
and a question: do I have to stay logged in on the home computer to use it at work?


@trak87
I just came out of state of confusion, don't drag me back in there :lol:
Yes, the computer will have to be logged on, and turned on to make a connect from work, or from the neighbors :D

Dr Small

---

### Post by reidms on 2007-05-15
Glad to see everything worked out alright!

Good luck mate!

---

### Post by trak87 on 2007-05-15
> **Dr Small said:**
> Yes, but that won't run GUI programs in Putty on a Windows Pc will it?
I thought you had to have x or something...

Dr Small

Correct. I don't know how it's done with Windows. I was just pointing out something similar and very cool with Linux. That's why I tried to convey the "clarity" intention, but I wasn't very clear.:wink:

Also, I think -X and -Y should be used together. I edited my previous post to convey this.

---

### Post by Dr Small on 2007-05-15
> **trak87 said:**
> Correct. I don't know how it's done with Windows. I was just pointing out something similar and very cool with Linux. That's why I tried to convey the "clarity" intention, but I wasn't very clear.:wink:

Also, I think -X and -Y should be used together. I edited my previous post to convey this.
I used -X and it worked for me ;)
There is another Ubuntu system in our family, and I ssh'ed to my computer with ssh -X nick@host and then ran gedit. Surprisingly, it worked :)

Dr Small

---

### Post by n8bounds on 2007-05-15
anybody know how to remotely login to an X server session....sorta windows terminal server type?

---

### Post by Gmbrdilos on 2007-05-17
ok I bumped into a problem now, I can conect and view the screen fine, I can even move arround the mouse. But clicking doesn't work. I made sure that I allowed the computer to be controlled reomotely but still nothing.

---

### Post by n8bounds on 2007-05-17
have u looked at the real console?  sometimes vnc is accepting your remote inputs and not updating your remote vnc viewer screen....try using x11vnc instead of the built-in vino/gino vnc server or whatever gnome calls it, its much more predictable

heres my ~/.x11vncrc file:
```

-display :0
-noxdamage
-shared
-forever
-loop
-passwd ReaLyS3cur3P@$$w0rdz
-accept xmessage -center -buttons 'yes:0,no:4' Allow remote VNC connection now?

```

are u using a composting windows manager?  that complicates things (x11vnc with -noxdamage decomplicates them a little)

you should have xmessage, but if you don't be sure to install it also

---

