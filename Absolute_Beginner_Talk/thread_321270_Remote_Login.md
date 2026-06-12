---
title: "Remote Login"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-18
In Ubuntu Edge, a couple of times I stumbled on a dialog with a check box for "Enable Remote Login" or "Allow Remote Login."  Now I can't find it.  ](*,)   Could someone please tell me where to find it again, and maybe give me a short explanation of what exactly it does.

Thank you very much,
Buck

---

### Post by xpod on 2006-12-18
System>preferences>remote desktop:D 

It`s for connecting pc`s remotely as far as i know.

I think theres other more advisable ways to do such stuff but i aint the person to ask about it.

---

### Post by Buck2348 on 2006-12-18
> **xpod said:**
> System>preferences>remote desktop:D 

Thanks, but that's not really what I was looking for.  The option there is "Allow other users to view your desktop"  What I'm looking for said either "Enable remote login" or "Allow remote login"

I hope someone will point me to it.

Thanks,
Buck

---

### Post by pormogo on 2006-12-18
Vino is the VNC client for gnome. VNC is an application that will allow you to remotely log into your Xsession. SSH is the protocal that allows remote terminal login however I doubt there is a GUI config option for that like you are explaining above.

---

### Post by thelinuxguy on 2006-12-18
> **Buck2348 said:**
> and maybe give me a short explanation of what exactly it does.

Remote login is used where u want users to log into your machine from other machines and allow them to run programs on your machine. So they will be running programs (maybe console or graphical) on your machine but having the display on their terminals.

You can use telnet or ssh (secure) to login remotely. With ssh, you can also use X11 forwarding, which means you can run GUI applications on the remote machine.
 
You have XDMCP for GUI based remote logins. Somewhat like mstsc on windows machines (to Windows Server and not to XP, which can have only one user logged in at a given time). See [http://tldp.org/HOWTO/XDMCP-HOWTO/]("http://tldp.org/HOWTO/XDMCP-HOWTO/")   for more information.

Remote login is different from VNC. With VNC, you allow the remote user to "see" what you are doing on your desktop and maybe control your desktop. That is, share desktops. With remote login, you allow the user to log into your machine and get a session for executing apps on ur machine. Different sessions / desktops for different users.

Unfortunately, my linux system is temporarily out of service. So I can't point you to the menu item's location.

Do not enable remote login or VNC server unless you want people to access your machine from other machines.

---

### Post by Buck2348 on 2006-12-18
Thank you all very much for your replies.  thelinuxguy:  if you should find what I'm looking for when you get back to your machine, I'd really appreciate it if you'd drop another note here.  I know I have seen option I mentioned more than once--don't know why it's so hard to find.

Edit--I think I've found what I was looking for.  System --> Administration --> Login Window --> Remote tab (surprise!).  The switch is at the top of this dialog under Style:  I didn't think to look at those options when I was searching earlier, but one of them is "Remote login disabled."  Not precisely what I said it was, but that was what I was looking for.  Thanks again to all.  I can use some of the info you gave me to try and set this up.

Regards,
Buck

---

### Post by scxtt on 2006-12-18
what exactly are you trying to accomplish?

a CLI login remotely? (ssh)
a GUI login remotely? (xdmcp)

---

### Post by dbott67 on 2006-12-18
SYSTEM > ADMINISTRATION > LOGIN WINDOW?

-Dave

---

### Post by Buck2348 on 2006-12-20
> **scxtt said:**
> what exactly are you trying to accomplish?

a CLI login remotely? (ssh)
a GUI login remotely? (xdmcp)

I was actually just vexed because I couldn't find this after having seen it before.  Since I started looking at it though I've started to try to set up a remote desktop so another computer on the network or on the Internet can remotely control this machine, which I guess is a GUI remote login.  I don't understand exactly what is accomplished by enabling remote login at System --> Administration --> Login Window.  I also wonder what the configuration box at System --> Preferences --> Remote Desktop does; apparently I have to have vnc installed to use that.  I installed it, but when I try to run either vncserver or vncviewer, I immediately get an error:  vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

So I'm going to have to work on that some more.  I googled it a bit already and for every package I downloaded the installer would give me another missing dependency.  I'll try a fresh start.

Thanks all for your replies.

Buck

---

### Post by scxtt on 2006-12-20
remote desktop through the menu is **vino** which will share your :0 connection ONLY when a user who shares their desktop is logged in (or whenever you can do a **ps -ef | grep vino**) ... it's *OK* but not that great of a method, tho you can make it so it can be 'watched' (i think) and/or require a password ... you could also use x11vnc to do this (you DON'T have to be logged in via GUI to use it either - i use x11vnc, it's nice) ...

you should be able to use vncviewer for this (vino), just be sure to specify :0 ... not sure about your stdc++ error, never seen that one ... i'm sure there's a package for it ...

you shouldn't have ANY dependency problems, apt-get / aptitude take care of that ...

you can use XDMCP to get GUI logins to any box on your network running an XDMCP "server" -- i'm 90% sure GDM/KDM provide that, so as long as they're running - and will allow connections, you'd be in business ... i also believe port 177 would give you access "from the outside" if it's forwarded / open ...

---

### Post by thelinuxguy on 2006-12-20
> I also wonder what the configuration box at System --> Preferences --> Remote Desktop does

[http://www.gnome.org/learn/users-guide/2.14/prefs-remotedesktop.html](http://www.gnome.org/learn/users-guide/2.14/prefs-remotedesktop.html)

---

### Post by Buck2348 on 2006-12-20
> **scxtt said:**
> 
you should be able to use vncviewer for this (vino), just be sure to specify :0 ... not sure about your stdc++ error, never seen that one ... i'm sure there's a package for it ...

you shouldn't have ANY dependency problems, apt-get / aptitude take care of that ....
I foolishly installed vnc from a tar.gz before I realized I already had vino installed and could install vncserver via synaptic.  It was that package that was giving me the error with dependency problems.  Once I got rid of that it was quite easy to set up remote desktop both ways with a windows machine on my network.  (I got the Windows version from the same download site as the problem package and it works fine.)  The only problem with it is it's pretty slow.

Thanks for the info--tomorrow I want to look at access from outside the network.

Regards,
Buck

---

