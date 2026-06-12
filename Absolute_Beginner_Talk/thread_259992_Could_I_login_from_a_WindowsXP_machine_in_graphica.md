---
title: "Could I login from a WindowsXP machine in graphical mode?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by CeesT on 2006-09-18
I have installed (as a test) Dapper Drake on a server-pc and it works fine. The graphical User Interface is also nice, but usually I have to operate my server computer from a remote computer to do maintenance.  Now I do this via PuTTY in terminal mode, but is it also possible to use a kind of X-Server on a remote computer and control my server-PC ?? Preferable would be from a Windows-XP computer. If not via Windows, could this be done by another Ubuntu installed PC ?
Until now I have not found a FAQ or manual where this is described, but I have heard stories that this should be possible. Could someone give me some hints or url where I can find more information ?

---

### Post by webra on 2006-09-18
Yes !!! Just install freenx.

[http://www.ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto](http://www.ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto)

/WebRa

---

### Post by buffy^ on 2006-09-18
With it beign a server install it dosnt as standard have a gui with it.

I have been using linux for a couple of days now and woud suggest:

sudo apt-get isntall gnome-desktop with gnome it has VNC build in, although i think you might have to login in fist before it loads the vnc service.

---

### Post by tturrisi on 2006-09-18
Install openssh-server on the linux server box and use winSCP on the windows box instead of putty.  WinSCP is a gui that does what Putty does.
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

---

### Post by CeesT on 2006-09-18
> **tturrisi said:**
> Install openssh-server on the linux server box and use winSCP on the windows box instead of putty.  WinSCP is a gui that does what Putty does.
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

With WinSCP I only have a filemanager, and I was looking for a "copy" of the graphical screen.

I will have a look for the VNC solution and try to read something about that, but possibly the freenx is better. I will try that. I have used VNC for remote control of Windows NT machines, but do not know Freenx. What is different if you compare VNC with Freenx ??

I have done a server-install, but as I said, it was just a quick test and I could easily re-install the desktop version and add some server packages later.

My "old" server is still running SuSE 8.2 and I have been using SuSE for many years. But OpenSuse 10.1 does not support the Southbridge VIA chipset of my new server-pc, so the SATA drive is not recognized. Ubuntu works fine out-of-the-box and installs very easy. So probably Suse has one user less in the future, because I am starting to like Ubuntu. :)

---

### Post by CeesT on 2006-09-20
FreeNX did not install for me (AMD64 processor).

But I found the (new) [free-edition of NX 2.0]("http://www.nomachine.com/ar/view.php?ar_id=AR06D00401"). It is limited to 2 users/sessions, but enough for personal use.

I followed the FAQ [installing NX2.0 on Ubuntu 64 6.06]("http://www.nomachine.com/ar/view.php?ar_id=AR07D00407") and it worked without any problem.

---

### Post by benfindlay on 2006-09-20
I personally use tightvnc tunneled through a putty connection. It looks exactly like I was actually logged in at the machine itself! Vnc will run with mulitple resumable sessions, so you can log in several times from different locations (if you feel the need ;))

The beauty of using putty to tunnel tightvnc is that it encrypts the connectiong for you

Its eays to set up too; first of all go into System>>Administration>>Login Window (might be Login Screen Setup, not at my pc, so not totally sure)

In there, click on the Remote tab, and set remote to either same as local, or the minimal graphics option. Now launch terminal.

Type the following into your terminal via ssh:

```
sudo apt-get install vnc4server xinetd
``` This will install the server software you need

```
sudo vncpasswd /root/.vncpasswd
``` This will prompt you for a password to protect the connection

```
sudo nano /etc/xinetd.d/Xvnc
``` This will launch text editor in putty. Paste the following into it:```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}
```

then just reboot


It works a treat for me, and since the only port I forward on my router is my ssh port, its nice and secure :D

Don't think I've missed anything, but if I have then someone will no doubt point it out! ;)

Hope this helps

---

### Post by benfindlay on 2006-09-20
Just a thought as well, you need to set putty up to tunnel from localhost (127.0.0.1) onto the remote pc. Then, once you have established your putty connection, you launch tightvnc, or whatever vnc client you are using, and connect to 127.0.0.1

---

### Post by jbennet on 2006-09-20
i use RealVNC to communicate between my linux machines, xp box and pocketpc

---

### Post by jbennet on 2006-09-20
just use synaptics to install the x11vnc server and run it from the console

---

