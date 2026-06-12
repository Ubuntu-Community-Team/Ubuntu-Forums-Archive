---
title: "Ubuntu Remote Server"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Vortex153 on 2008-01-24
Hello all. I'm new to Ubuntu and was having some problems before I even got started.

I'm leasing a remote server and I'm trying to use VNC Viewer to remotely connect but all I'm getting is: "unable to connect to host: Connection refused (10061)". I'm putting the ip in correctly (xx.xxx.xxx.xxx:0).

Any suggestions? The server is running Ubuntu 1.0.6.1 and I'm running windows XP. I've also forwarded the port 5900 on my router, but I can't seem to figure out what's wrong. Am I suppose to have the remote server company do something on their end?

Thanks for any help!

---

### Post by Rocket2DMn on 2008-01-24
Did you boot a vncserver on the machine?  If not, SSH into the server and run
```
vncserver
```  It will tell you the port to use.  Also, are you sure they have remote desktop enabled and not just SSH and SFTP?

---

### Post by Vortex153 on 2008-01-24
When I try to run vncserver I get "vncserver: command not found"

---

### Post by Rocket2DMn on 2008-01-24
that means that you will be unable to use a VNC remote connection for now.  The chances are that your server provider only gives you SSH and SFTP access, you will have to contact them and ask about remote desktop with VNC.  If they allow it and you have full access to the server (with root privileges), you can set up VNC yourself, otherwise they will have to do it for you.  It's entirely possible they don't even have X (the GUI software) installed on the machine and only allow terminal access.
What are you using this server for?

---

### Post by Vortex153 on 2008-01-24
yeah, it looks like GUI isn't installed. I do have root access. I'm trying to run rTorrent on it, my home connection isn't exactly fast.  Thanks for your quick replys.

Sorry for the delay in my reply,  I had an emergency at work I had to take care of.

---

### Post by Rocket2DMn on 2008-01-24
IF they allow you to setup a GUI, the command to install gnome would be
```
sudo apt-get install ubuntu-desktop
```
After that you can setup remote desktop, check this out - [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
Here's the obligatory warning: don't install a GUI if it is against your agreements terms.

---

### Post by Nythain on 2008-01-24
why gui for rtorrent??? its a console app... at least the version i run is... its amazing, love that program, and best of all, doesnt require a gui

---

### Post by Vortex153 on 2008-01-25
Thanks, I have figured out that you don't need gui to run rtorrent. Now I just can't seem to get rtorrent going. I've learned how to install it and I found most of the commands for it, however I'm not finding how to actually start the program (man do I feel like a n00b ](*,) )

---

### Post by Rocket2DMn on 2008-01-25
I don't use rtorrent, but can you not just run
```
rtorrent
```
If not, search of the executable, it should be in /bin or /usr/bin
```
whereis rtorrent
```

---

### Post by Vortex153 on 2008-01-25
I'm getting this:

root@xx-xxx-xxx-xxx:~/rtorrent# rtorrent
-bash: rtorrent: command not found
root@xx-xxx-xxx-xxx:~/rtorrent# whereis rtorrent
rtorrent:
root@xx-xxx-xxx-xxx:~/rtorrent#

---

### Post by Rocket2DMn on 2008-01-25
It seems that rtorrent is not actually installed.  You will have to install it with apt-get, but you will need the universe repository to be enabled
The command to install is
```
sudo apt-get install rtorrent
```
If it can't find it, setup the universe repository and run the command again
```
sudo nano /etc/apt/sources.list
```
Find the lines relating to universe and multiverse and remove the # at the start of the line.  If you need more detailed help, post the contents of the sources.list file here.  You can get it by running
```
cat /etc/apt/sources.list
``` through your ssh session.
IF YOU HAVE TO ENABLE the universe and multiverse repositories, you MUST run this command before you run the install command:
```
sudo apt-get update
```

---

### Post by Vortex153 on 2008-01-25
I think I got it. I had it installed wrong. Thanks for the help, it's up and running now. Thanks for your quick replys and all your help.

---

