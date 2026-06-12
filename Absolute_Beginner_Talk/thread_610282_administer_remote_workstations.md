---
title: "administer remote workstations"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by rtoobtoo on 2007-11-11
I have successfully removed windows in the office and converted every single PC to ubuntu.. We have 10 workstation now running ubuntu.. 

i know the user's familiarity with ubuntu will develop in time, but my problem now is if some users in those 10 workstations ran into trouble or wanted to install something , i have to go directly to that machine to administer his/her PC.. imagine doing that for all other 9 workstations !

can i manage the user's desktop on our LAN without leaving my own desk? 

im thinking of VNC... is it possible to login to a PC within our LAN with an administrator account so i can do everything ? 

thanks !

---

### Post by mkoehler on 2007-11-11
Rtoobtoo,

      You could use an application such as VNC, but it might be easiest to use an application that is already built into X.  If the computers which you wish to administrate are on a wired network (I say this because the application is bandwidth intensive), you could use XDMCP.  You do this by clicking on Options>Remote Login via XDMCP from the login screen.  Note: you first have to enable remote system administration on each of the client computers.  The XDMCP remote connection tool should automatically detect each of the available computers to log onto, but if it does not, you can manually enter their IPs.

Cheers!

---

### Post by rtoobtoo on 2007-11-11
> **mkoehler said:**
> Rtoobtoo,

      You could use an application such as VNC, but it might be easiest to use an application that is already built into X.  If the computers which you wish to administrate are on a wired network (I say this because the application is bandwidth intensive), you could use XDMCP.  You do this by clicking on Options>Remote Login via XDMCP from the login screen.  Note: you first have to enable remote system administration on each of the client computers.  The XDMCP remote connection tool should automatically detect each of the available computers to log onto, but if it does not, you can manually enter their IPs.

Cheers!

 how can i enable remote system administration on the client computers ?  (newbie here :))

---

### Post by Hospadar on 2007-11-11
I would just use ssh if it were me, it allows you to get a command prompt from their machine.  the only drawback here is you'd need to manually enter their IP adresses, (although you could use launchers or aliases to keep track of machines)  ssh is very fast, and allows you also to open graphical applications (the apps are run by their machine, but displayed on yours)  also this makes it possible to access machines from a windows box with a ssh client like puTTY if you're out of the office.

You'll need to do a relatively simple setup on the client machines, have a look at [this]("http://php.8ez.com/drsmall/blog/?p=124") page.  You'd need to do that setup on each client machine, then you could use the command ```
ssh <admin username on target machine>@<target IP address>
```
to get you a command prompt on their machine, then you can startup graphical apps from the command line.

---

### Post by rtoobtoo on 2007-11-11
being new to ubuntu i think i'd stick first with xdmcp (if i configured it properly) . administration using the command line is something i still have to learn ( commands . etc). so how can i enable remote login in the client computer to be used by XDMCP?

---

### Post by socceroos on 2007-11-11
Hello mate,

Here is the easiest way to be able to administer someone elses desktop remotely:

Go to System->Preferences->Remote Desktop

Tick the "Allow other users to view your desktop" and "Allow other users to control your desktop" boxes.

Also, tick the "Require user to enter this password" box and create yourself a password that you can use to log into the remote machines.

Once you have done this, click on the vncviewer command that is below the first two boxes and email this to yourself.

Once this is done, all you need to do to remotely view a desktop from your own Ubuntu computer is this:

Go to Applications->Accessories->Terminal and paste the command from the email.

Hope this helps,

Socceroos

---

### Post by rtoobtoo on 2007-11-11
does vnc allow a separate login for the remote user ? i need this because i dont want to interfere with the user's daily work when im updating their system. VNC is used to share / control the desktop of the user right ? what differentiates XDMCP from VNC? 

thanks !

---

### Post by carlosjuero on 2007-11-12
> **rtoobtoo said:**
> does vnc allow a separate login for the remote user ? i need this because i dont want to interfere with the user's daily work when im updating their system. VNC is used to share / control the desktop of the user right ? what differentiates XDMCP from VNC? 

thanks !
Try this for seperate logins:

[http://www.nomachine.com/](http://www.nomachine.com/) 

There is a free (for life) server & client download. It logs you in as a seperate user (and session) and doesn't take over the desktop as with VNC. I just started using it and it is a very good solution for remote control.

---

### Post by poudin on 2007-11-12
at work we use the following to admin remote machines

1. ssh with -X...ssh [email]root@xxx.xxx.xxx.xx[/email] -X...should allow the X session on the remote machine to be forwarded to your local X server on local machine.

2. Exceed....its a licenced program to emulate X from a remote machine to a local machine.

from previous posts....

the nomachine should work also....

also you should be able to use Xming over .ssh...i have not tried that as an option...as I have the other #1 and #2 working successfully already.

good luck

---

### Post by rtoobtoo on 2007-11-14
nomachine worked great! i was able to setup all the computers within our LAN.. now my problem :

i want to download updates on one computer and reflect / implement this updates to the other 9 workstations.. how can i do this? I have tried aptoncd but it seems its only for packages and i still have to manually run the cd on each workstation.. 

thanks

---

