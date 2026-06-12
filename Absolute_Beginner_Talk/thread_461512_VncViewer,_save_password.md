---
title: "VncViewer, save password"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by mayamaniac on 2007-06-01
How do I save the password for vncviewer? 

I'm confused, the help says to store the password in a .passwd file or something. I'm not sure how that is done. The way it works now, I made an applink with this line:
```
vncviewer server_adress:port
```
Launching it, it would connect then pop up a small window for the password. I would like to some how save this password so I don't have to type it in all the time. Please help, thanks.

The alternative is to use a VNC veiwer with a GUI, which I haven't found.

---

### Post by pmg on 2007-06-01
I didn't quite follow your question, but maybe this will help.

When you run **vncpasswd** to setup a password, it encrypts and saves it in a file, typically ~/.vnc/passwd.  That is what the vncserver then checks against when a client tries to connect. If the client shares a filesystem with the server and can access the same ~/.vnc/passwd file, you can use the -passwd option on the (client) **vncviewer** command to have it use that flie rather then having to type the password in.

Does that help clarify it at all?

---

### Post by mayamaniac on 2007-06-02
> **pmg said:**
> Does that help clarify it at all?
Actually, no. 

I guess I misundertood the whole .passwd thing, I didn't know it was only for Vnc**Server**, which I'm not using in ubuntu.

I'm dealing with vnc**Viewer** in Ubuntu and connection to a windows PC running VNC Server. What I want is a way to save the password on the vncViewer in Ubuntu so that I don't have to type it in each time I connect to the server. I have vnc clients in WinXP (UltraVNC) and OSX (Chicken VNC) that have the ability to save passwords, but can't figure out to do so in Ubuntu.

---

### Post by pmg on 2007-06-03
I think I follow now.  I've not done this from ubuntu, but it sholud do what you want.  Run the command **vncpasswd** which will save your (encrypted) vnc password in the file ~/.vnc/passwd on your ubuntu machine.  Then you can run **vncviewer -passwd ~/.vnc/passwd *vncservername:display***.

---

### Post by mayamaniac on 2007-06-04
thanks, that works!

---

### Post by Tobba25 on 2007-07-08
Works for me too in Terminal. But I'd like to make a launcher out of it. The exact command used in terminal just wont work with a launcher.

What gives?

---

### Post by Transmission3000 on 2008-01-29
> **Tobba25 said:**
> Works for me too in Terminal. But I'd like to make a launcher out of it. The exact command used in terminal just wont work with a launcher.

What gives?

I just ran into the exact same problem, after figuring it out from the terminal. Anyone?

---

### Post by Kralizec on 2008-06-26
Forgive me for bumping, but I felt the need to contribute. I've actually gotten a launcher working, and the only thing I did differently than the command pmg suggested was to use the exact path; that is, my command in the launcher looks like this:
```
vncviewer -passwd /root/.vnc/passwd 132.250.66.112
```
instead of
```
vncviewer -passwd ~/.vnc/passwd 132.250.66.112
```

Make sure you don't just copy and paste my code, because it won't work for you; I'm running running my session as root and you most likely aren't (I chose to forgo the extra security in exchange for not having to enter a root password). So make sure to change the **/root** portion to **/home/<your username>**.

---

