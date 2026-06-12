---
title: "massive ubuntu server help needed"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by bunty99 on 2007-10-14
I'm a freaking linux noob, and though I should hire a management team to help me, I thought I learn it myself since I'm gonna need it later on. 

I'm not sure if I should just do a fresh OS install and try again or continue from where I am.

I have done searches to try and correct the problems but they just ain't working for me.

I have ubuntu 6.06 installed on my server as well as vsftpd. This is where the problem starts. I tried to edit the config file, but running all commands don't seem to work. I've tried redit, edit but it just keeps saying 
> root@server1:/# sudo gedit /etc/vsftpd.conf
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@server1:/#

I'm not sure what is going on and it's frustrating trying to get the ftp working. I  only can access anonymously and I can't access any other files or folders. The whole directory is just blank.

Second, once vsftpd starts working properly, will I have access to every folder in server and be able to read and write? If not, how do I go about ensuring I can. I originally had proftpd installed but I couldn't access the ftp as root and couldn't upload files into the /var/www directory.

Third, I have installed the desktop gui as well, as I thought it would make things easier. How the hell do I have the gui appear lol? I'm currently using Putty and all I see is command line.

Sorry for being a retard, but I seriously hate linux >.>

---

### Post by 001100 on 2007-10-14
wate and try ubuntu 7.10 server or try 7.04 I used it and it works good better than 6.06
and if you need any help on anything i'm here

---

### Post by bunty99 on 2007-10-14
The problem is my host only offers 6.06, that's why i'm stuck with it.

---

### Post by wormser on 2007-10-14
I think the problem is you are trying to run gedit in a non graphical mode.  Gedit is a graphical program for text editing.  Try using **nano** instead.

```
sudo nano /etc/vsftpd.conf
```

To start the gui: **startx**

---

### Post by jocko on 2007-10-14
> **bunty99 said:**
> I'm a freaking linux noob, and though I should hire a management team to help me, I thought I learn it myself since I'm gonna need it later on. 

I'm not sure if I should just do a fresh OS install and try again or continue from where I am.

I have done searches to try and correct the problems but they just ain't working for me.

I have ubuntu 6.06 installed on my server as well as vsftpd. This is where the problem starts. I tried to edit the config file, but running all commands don't seem to work. I've tried redit, edit but it just keeps saying 


I'm not sure what is going on and it's frustrating trying to get the ftp working. I  only can access anonymously and I can't access any other files or folders. The whole directory is just blank.

Second, once vsftpd starts working properly, will I have access to every folder in server and be able to read and write? If not, how do I go about ensuring I can. I originally had proftpd installed but I couldn't access the ftp as root and couldn't upload files into the /var/www directory.

Third, I have installed the desktop gui as well, as I thought it would make things easier. How the hell do I have the gui appear lol? I'm currently using Putty and all I see is command line.

Sorry for being a retard, but I seriously hate linux >.>

gedit requires a graphical interface. If you don't have a gui, use nano instead.
You don't say which gui you have installed, or how you installed it. If you installed gnome (by installing the meta-packages ubuntu-desktop or gnome-desktop-environment), you can start the login screen by typing "sudo gdm".

---

### Post by bunty99 on 2007-10-14
Nothing appears for nano, but 'vi' works. I see a whole list of text. Another problem here. After editing the file, how do i save it and exit out of it?

Sorry, thought there was only one gui. I installed gnome. It just tells me gdm is already running when I use the command, but i don't see anything >.<. Am i using the wrong program?

---

### Post by 001100 on 2007-10-14
wow that sucks but yea gedit is a gui text editer and you need a command line text editor

---

### Post by wormser on 2007-10-14
> **bunty99 said:**
> Nothing appears for nano, but 'vi' works. I see a whole list of text. Another problem here. After editing the file, how do i save it and exit out of it?

Sorry, thought there was only one gui. I installed gnome. It just tells me gdm is already running when I use the command, but i don't see anything >.<. Am i using the wrong program?

Once the file opens in vi.  Hit **i** or the **Insert** key to edit.  When done editing hit **Esc**.  To save changes **:w** and to quit **:q**.  To write and save changes at the same time use **:wq**.  To quit with out saving changes **:q!**.

---

### Post by bunty99 on 2007-10-14
Ok, awseome. The ftp is working for users now. But, how do I allow root to access the ftp? It tells me login incorrect. I can't upload files into /var/www directory with the other users.

---

### Post by wormser on 2007-10-14
> **bunty99 said:**
> Ok, awseome. The ftp is working for users now. But, how do I allow root to access the ftp? It tells me login incorrect. I can't upload files into /var/www directory with the other users.

How are you trying to move the files?  Regular users with sudo rights have root privileges.  Just put sudo before the command.

---

### Post by bunty99 on 2007-10-14
Trying to move it via flashfxp. It's easier to move, delete files there. So i need to be able to login to the ftp as root. But I'm having problems doing so. I can login in as other users, with permissions in their respective folders, but they don't have access to the files in root.

---

### Post by wormser on 2007-10-14
> **bunty99 said:**
> Trying to move it via flashfxp. It's easier to move, delete files there. So i need to be able to login to the ftp as root. But I'm having problems doing so. I can login in as other users, with permissions in their respective folders, but they don't have access to the files in root.

Logging in to root is a no no in the Ubuntu world.  You should be able to use sudo before the command to get root privileges.  But to get into root use **sudo -i** and type in that users password.  You have been warned!

---

### Post by bunty99 on 2007-10-14
Yes, I do know that. Apparently, flashxp doesn't allow me to login as root, but other ftp winscp3 does. Weird.

---

### Post by jocko on 2007-10-14
> **bunty99 said:**
> Nothing appears for nano, but 'vi' works. I see a whole list of text. Another problem here. After editing the file, how do i save it and exit out of it?

Sorry, thought there was only one gui. I installed gnome. It just tells me gdm is already running when I use the command, but i don't see anything >.<. Am i using the wrong program?
To install nano: ```
sudo apt-get install nano
``` it's easier to use than vi, since it does not require that you already know all commands to save, exit and so on (they are all listed on the bottom of the screen, ctrl-o to save, ctrl-x to exit).
If it tells you gdm is already running, try switching to the login screen by pressing ctrl+alt+f7.

---

