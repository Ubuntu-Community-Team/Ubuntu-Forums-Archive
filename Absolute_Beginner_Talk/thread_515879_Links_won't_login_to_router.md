---
title: "Links won't login to router"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Weebs on 2007-08-02
I currently have a computer running Ubuntu Server 7.04, with no GUI installed. I'm away from home for the next two weeks, but I do have ssh access to my server. I currently need to forward port 27015 for my Counter-Strike: Source server. I tried using Lynx, and when I went to the router it asked for the user password and logged in just fine. The problem was that my router requires Javascript, which Lynx does not support. I then searched for a text browser that does, and came acros Links. The problem is that whenever I go to my router page, it never asks me for a login, it just immediately tells me "401 Access Denied". I tried doing the whole [http://username:password@192.168.1.1](http://username:password@192.168.1.1) think for the URL, but that didn't help either. Is there anyone who can tell me how to tell Links to fill out the login form, or if there's a Javascript mod for Lynx?

Thanks,
Weebs

---

### Post by Rocket2DMn on 2007-08-02
If you want SSH access, you will also need to forward port 22 I believe.  I run a counter-strike 1.6 server, and I just enabled DMZ on the router to the server computer which has a static internal IP address of 192.168.1.200.  You will then be able to login with ssh, ftp, and anything else you have setup on the server without having to worry about forwarding a bunch of different ports.  The only disadvantage is that DMZ can open the computer up to the internet, but it's not really much of a problem with linux.
As for your text based browser, I'm not sure about that one, just thought I would give my 2 cents on the above info.

---

### Post by Weebs on 2007-08-02
I already have SSH access, as well as FTP. I'm just trying to use the browser to login to my router so I'm able to forward ports and change settings and such. I could ssh into Ubuntu and run GUI apps, but my main OS on this laptop is Mac OS X. I suppose I could install a small Linux distro into a virtual machine via Parallels or VMWare suchs as D*** Small Linux and use that to run GUI apps on the server via SSH.

---

### Post by Rocket2DMn on 2007-08-02
Elinks might be an option, some sources say it supports javascript.
Also, another option is to install a GUI on the server (like ubuntu-desktop), but set your init level to 3 on boot so it stays in the CLI.  This gives you the option of running "init 5" and starting up the GUI if you really need to do GUI stuff (like access a good enough browser), then dropping back to runlevel 3 afterward to save on computer resources.

---

