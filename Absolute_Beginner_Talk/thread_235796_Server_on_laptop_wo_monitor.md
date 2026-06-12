---
title: "Server on laptop w/o monitor"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-13
Hello,

I am a newbie; have a Ubuntu distribution running on my IBM laptop, have been enjoying it.

Am interested in running the server version to host my PHP/mysql websites (local intranet maybe later go public).  I just got another old laptop up and running and wanted to install the server version on there ... really, need something simple simple simple.

My question, though, is if I can access and work with the linux server from my other computer ?  Because: this old laptop's monitor is broken and the output for a screen won't stick unless I am holding it in hand in a special way.  So: after I installed it, would it be able to run from another machine ?

Thanks,
D

---

### Post by foolsh on 2006-08-13
absolutely if you can get the ip address configured and sshd installed 
then from another computer with ssh just type ```
ssh xxx.xxx.xxx.xxx
``` where xxx.xxx.xxx.xxx is the ip address of your server
also if your a GUI person you can install the regular version of ubuntu and ```
sudo gedit /etc/gdm/gdm.conf
```
and look for the [xdmcp] section and change Enable=false to Enable=true
save and restart
then from another ubuntu box at the login screen choose remote login and wait for it to search for ipaddresses or input the ip address yourself then login just like you were in front of that computer all along

---

### Post by thornomad on 2006-08-14
Hello and thanks for the reply.  Again, I am new but enjoying playing around.  Correct me if I am wrong:

So, would I want to install the "Server Edition" of Ubuntu on the "server/laptop" (so I could use the LAMP features), then setup the SSHD (I will look on the wiki for that, if not already installed I assume I use an "apt-get" command or something).  It sounds like if I did that, then I wouldn't be able to connect to the computer using the GUI ... hmm.  Will the desktop edition give me the same functionality as the server edition ?  Just a heavier install ?

Either way, once I got the server up and running, I would really only need to install the mysql databases that I needed and add/remove files from the appropriate directories of the web server.  Would all that have to be done frm SSHD or could I configure it to work with my Mac (like as a network/shared drive) ... where I do my html editing?

Thanks again everyone!  This is exciting.  So much to learn.

D

---

### Post by foolsh on 2006-08-14
I'm sure you can apt-get install ubuntu-desktop to get a gui on the server edition 
but anything you can do with a gui can be done from a terminal console just more technical 
when you login with ssh it is just like sitting at the computer the same with xdmcp just with the gui
i use both 
when i have it setup like I want I issue the command from ssh to free up resources
```
sudo /etc/init.d/gdm stop
```
and add
```
exit 0
```
to the top of script /etc/init.d/gdm so it doesn't startup automatically
then if i need the gui i ssh into the computer comment out exit 0 and
```
sudo /etc/init.d/gdm start
```
then use remote login at the gdm greeter get the gui 
you'll like it either way I'm sure

---

### Post by thornomad on 2006-08-15
Hello again - thank you for all your help.  I have successfully installed the Ubuntu Server on the old laptop (LAMP version).  Got a command prompt, checked it form another system and Apache is installed correctly.  Now I need to go about transfering my databases from my other mysql ...

I think I will leave it all command prompt; my hope is that I can:

A) connect via SSH through my Mac (other my other Ubuntu system) to make changes to the mysql and apache;

B) connect via ... hmm, I don't know what to call it.  I guess: file server.  I would like to use the "connect to server" function on my mac to create a network drive that I can use to manipulate the html, php, and whatnot without having to transfer each file or directory each time via SSH.  

Sound simple ?

D

---

