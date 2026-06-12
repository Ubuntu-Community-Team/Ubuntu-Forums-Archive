---
title: "[SOLVED] recommend an ftp client"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-08-07
Just looking for a basic FTP client. 

In windows I used smart FTP

---

### Post by Rocket2DMn on 2007-08-07
I use gFTP when needed.
Also, I mounted some remote directories on my desktop using SSH so I can quickly access files on my school unix system and our Fedora Core 5 game server.

---

### Post by Dr Small on 2007-08-07
I use gFTP, but it has a tendency to freeze apt times.
I think you can user Fireftp for Firefox though.

Dr Small

---

### Post by wormser on 2007-08-07
There is one built in.  Places> Connect to Server.  Then under service type they have FTP, SSH plus others.  Gftp is not bad but recently I switch to the built in one because it creates a short cut on your desktop.

---

### Post by lmlypfan on 2007-08-07
Rocket2DMn,

Do you have the files in your home directory so you can access them via ssh?

Today was my first day using ssh (via putty) from work to home desktop. 

No too good with the command line, so I am limited in what I can do.  
I tried to edit the config file for my ftp server, but couldn't launch gedit from an ssh connection.

Also, I have used VNC to remote desktop from work, but the delay SUCKS. 
Never had that problem when using RDT windows to windows.  

Any suggestions?

Thanks for all the help so far.

---

### Post by Dr Small on 2007-08-07
> I tried to edit the config file for my ftp server, but couldn't launch gedit from an ssh connection.

Use pico for command line based editing.

Dr Small

---

### Post by Rocket2DMn on 2007-08-07
> **lmlypfan said:**
> Rocket2DMn,

Do you have the files in your home directory so you can access them via ssh?

I am able to navigate the whole root file system.  If you run the Connect to Server and select SSH, it will ask you for a server, a username, and a directory to start it.  I start in /steam b/c this is where I keep the game server files, but I can move directories easily (it opens in nautilus and mounts on my desktop).

> Today was my first day using ssh (via putty) from work to home desktop. 

No too good with the command line, so I am limited in what I can do.  
I tried to edit the config file for my ftp server, but couldn't launch gedit from an ssh connection.
That type of SSH is simply command line, and it will drop you in your home folder, but you should be able to navigate around.  There are plenty of guides to help you learn the CLI, like
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)
[https://help.ubuntu.com/community/AdvancedCommandlineHowto](https://help.ubuntu.com/community/AdvancedCommandlineHowto)
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

> Also, I have used VNC to remote desktop from work, but the delay SUCKS. 
Never had that problem when using RDT windows to windows.  

Any suggestions?

Thanks for all the help so far.

VNC is a powerful tool, but isn't perfect.  I hardly ever actually use VNC because I have learned to use the command line very effectively.  This requires less time and bandwidth.  You can look around for help with remote desktop connections, or start a new thread about it.

---

### Post by wormser on 2007-08-07
> **lmlypfan said:**
> Rocket2DMn,

Do you have the files in your home directory so you can access them via ssh?

Today was my first day using ssh (via putty) from work to home desktop. 

No too good with the command line, so I am limited in what I can do.  
I tried to edit the config file for my ftp server, but couldn't launch gedit from an ssh connection.

Also, I have used VNC to remote desktop from work, but the delay SUCKS. 
Never had that problem when using RDT windows to windows.  

Any suggestions?

Thanks for all the help so far.

You can use the method I posted above with ssh and just drag and drop files.  It works great.

Gedit is a gui application and will not work in a ssh shell.  Use nano instead.

---

### Post by lmlypfan on 2007-08-07
Thanks for all the advise.

GFTP works great, as well as ubuntu's connect to server application.

I will look at using the CL editors as well.

Thanks again

---

