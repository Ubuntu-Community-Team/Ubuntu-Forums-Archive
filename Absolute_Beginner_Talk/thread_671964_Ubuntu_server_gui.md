---
title: "Ubuntu server gui"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by markoklacar on 2008-01-19
Hi,

I've got ubuntu server(no my choice btw) running ok, now the problem is a need a GUI in order to set up some things.

I've read all the forums, posts, tips, tutorials I've been able to find and so far nothing has worked.

```
sudo apt-get install ubuntu-desktop 
```

I ran the command above and it installed ok, but when i type startx I get an error telling me that some font path elements could not be found.

Now I've tryed to set up my server for access using vnc but failed at this as well, I get the vncserver running alright but when I connect from the client side (Windows XP) it cannot connect.

Any ideas?

Thank you in advance

---

### Post by mlentink on 2008-01-19
Am I correct in assuming that you are not running a gui now? 
If so, I'd advise against using VNC to remote connect to that box, you would be better off using SSH.

Could you tell us a bit more on how you connect to thew internet?

---

### Post by zipperback on 2008-01-19
You don't want to run a GUI desktop on your server. That's a serious waste of system resources.


Remote administration should be done via SSH connections.



Since you have Windows XP for your client side computer, you would do well to download and use a copy of putty from [http://www.openssh.org/windows.html](http://www.openssh.org/windows.html)

- zipperback
:popcorn:

---

### Post by markoklacar on 2008-01-19
Hi again,

thank you for you replys. I connect to the server using putty at the moment.
I start the vncserver but when I connect using VNC it can't connect.

The server is at a co-locate but I a port needs to be opened up I can make it happen.
Do I need any additional port to be opened up or any other type of configuration to be changed?

Thank you one again.

---

### Post by mlentink on 2008-01-19
So you already use SSH tot get to the server.
What would you then want to use VNC for?

---

### Post by markoklacar on 2008-01-19
Hi,

well I need GUI access....but the vncviewer won't start.
Any ideas?

---

### Post by mlentink on 2008-01-19
Would you mind explaining why you would want to use a gui on a server? I know I don't with mine. I use SSH and Webmin, which is more than adequate, and doesn't eat up resources unnecessarily. Don't want to be obnoxious, just curious.

Which command are you using to start up the VNCserver, and what error messages does it give you?

---

### Post by markoklacar on 2008-01-19
Hi again,

no problem, the thing is I didn't choose the server version it was choosen for me at a co-locate, make sence? I need to install some programs in order to do some programming, server version is not optimal I know, from a different computer.

The "server" will not act as a real server, the thing is the co-locate did not have any other options.

All I need is a way to access the server and get a GUI so I can install eclipse and some other programs.

There does not exist any performace requirements, I know the GUI part takes a lot of rescources.

Cheers

---

### Post by mlentink on 2008-01-19
Thx, fair enough, you're just using it as a remote desktop, from what I understand.

HHow do you start the vncserver? Does it give you any error messages?

You may want to look at [this]("http://www.realvnc.com/products/free/4.1/man/vncserver.html") to check your syntax

---

### Post by markoklacar on 2008-01-19
Hi,

correct, perhaps I did not explain it fully(that I want to remote).
So, when I type in```
vncserver -name ubuntu -geometry 1024x768
```
I get

```
manager@de-0232:~$ vncserver -name ubuntu -geometry 1024x768
Found /usr/share/tightvnc-java for http connections.

New 'ubuntu' desktop is de-0232:4

Starting applications specified in /home/manager/.vnc/xstartup
Log file is /home/manager/.vnc/de-0232:4.log

manager@de-0232:~$
```

When I want to connect to the server, I suspect this is where I mess it ALL up, I type in the IP address of the server and try to connect.

It says that it can not connect.

Any ideas?

Thank you once againg, I really appreciate you help.

---

### Post by mlentink on 2008-01-19
What do you use to connect? A VNC client or your browser? 

From the looks of it, a browser based client is supported. Are you using port 5901 to connect? VNC connect not only at the IP-adress, but also at a specific port (5900 + the displaynumber, in most cases 1)

---

### Post by markoklacar on 2008-01-19
I've been using a vnc client, when I try setting the port or the display number it still does not work.
How do I connect using a browser? I've tried setting the port still does not work. 
Apache is installed so when I go to the ip address I come the first page.

---

### Post by mlentink on 2008-01-19
So...
If you use your vncclient (remote dekstop?) and use 123.456.789.123:5901 as the point to connect to it doesn't work?
What exactly do you get as error messages?

Edit: have you also tried [http://123.456.789.123:5901](http://123.456.789.123:5901) ?

---

### Post by markoklacar on 2008-01-20
I've tried it all, the message I get only says :"Failed to connect to server"
When I try using the http it says the page can not be found.

Could it be do to the fact the the port, say 5901, needs to be opened up?

Thanks

---

### Post by mlentink on 2008-01-22
my bad...

Yes. Obviously, that port needs to be open on your ISP&#347; router, and should be forwarded to your 'server' IP-adress (internal). If that's not feasible, you might want to take a look at hamachi.

---

### Post by markoklacar on 2008-01-22
Now it works fine, the port was opened up. 
I can't thank you enough.

---

### Post by erosion on 2008-01-22
use this great information: [http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/]("http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/")
This is the best url i found and it only took me a week to find:) hope it helps you as it helped me

---

### Post by legzelda on 2008-01-22
You might want to try the following, too:

```
sudo /etc/init.d/gdm start
```

---

### Post by markoklacar on 2008-01-23
Hey guys,

Thanks for the info, but when I type in the command all it says is:

```
* Starting GNOME Display Manager...     [OK]
```

After this nothing happens...am I missing somthing really obvious here???

Cheers

---

### Post by legzelda on 2008-01-25
You could try

```
sudo /etc/init.d/gdm restart
```

If still nothing nothing loads, try Ctrl + Alt + F7.  If you still don't have an X server running, switch back to tty1 using Ctrl + Alt + F1.  Then try

```
cd ~
nano .xinitrc
```

Type the following in the file, 

```
/usr/bin/gnome-session
```

and then save the file using Ctrl + O (press enter to accept the suggested filename) then Ctrl + X to exit:

Now, try

```
startx
```

and see what happens.

---

### Post by markoklacar on 2008-01-26
Hi,

It seems to restart OK, but after that nothing happens.
I still get the Fatal server error:

AddScreen/ScreenInit failed for diver 0

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 know processes) with 0 events remaining

Any ideas?

Thank you in advance...

---

### Post by ByteJuggler on 2008-01-26
I think you can ignore the comments about starting gdm, and startx -- these are all to do with starting the login manager and X on the console (meaning, the screen and video adapter actually connected to the server machine itself), to which you don't have access!!!

There is a way to set up VNC in a pseudo terminal server like way, so that gdm (the login manager) runs on the default session and then starts up new vncserver sessions for you to connect to, but I don't know the details and/or the caveats. 

However, I would suggest you look into NX, installing NXServer on your server and NXClient on your client PC will give you true terminal server style remote desktop access with multiple sessions.  It is also mind bogglingly efficient (even better than Windows RDP, and way better than VNC) in terms of bandwidth.

If you're interested I'll try and post a brief synopsis of what you need to do.

---

### Post by markoklacar on 2008-01-26
Hi,

I'd be willing to give it a shot. What I want basically, don't as why...just don't, is to be able to install Eclipse and Java and do some programming via the server, like I said don't ask...

I've got access through vnc now but the ubuntu-desktop, or whatever, won't start...

I want it to look like plain regular ubuntu, but since it's at a co-locate it is not possible for me to choose, you get it...


I'd appreciate any advice you could give me...

---

