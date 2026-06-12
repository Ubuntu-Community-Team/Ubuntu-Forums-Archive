---
title: "Remote control/desktop type prog for Ubuntu"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-03-09
Hey all,

I'm wondering if Ubuntu 6.10 comes with any kind of remote desktop/terminal services or remote control program already installed by default or that can be installed through Universe or however it is you access programs that come with the install CD.  I'd like to be able to access my Ubuntu PC from work.  Right now I can access my XP machine via LogMeIn or the built-in remote desktop capability.  Let me know.  Thanks.

---

### Post by benfindlay on 2007-03-09
I believe the program you are looking for is x11vnc. Sorry, but I don't have any experience with it. I personally use vnc4server but as far as I am aware, it still isn't working on 6.10. 

x11vnc should be in the repositories though and there are plenty of guides on this site for it!

Hope this helps!

---

### Post by jkeyes0 on 2007-03-09
Thrasonic, I believe you're looking for "Remote Desktop", which comes built-in to Ubuntu.

Click System ==> Preferences ==> Remote Desktop. Checkmark the "Allow other users to view your desktop", "Allow other users to control your desktop", and "Require the user to enter this password" (if you want any security on it). Also, uncheck the "Ask you for confirmation", or else it won't let you in remotely.

You will need a VNC viewer program at the other location (in windows, especially) if you intend to do it this way. I personally use RealVNC, [http://www.realvnc.com/products/free/4.1/download.html](http://www.realvnc.com/products/free/4.1/download.html)

---

### Post by Bachstelze on 2007-03-09
If you just need a console access :

```
sudo apt-get install openssh-server
```

Then you will need a SSH client to access it. Most UNIX-like systems have one installed by default and you can download one for Windows from [http://sshwindows.sf.net](http://sshwindows.sf.net)

---

### Post by benfindlay on 2007-03-09
> Thrasonic, I believe you're looking for "Remote Desktop", which comes built-in to Ubuntu.

I take it that is vino as opposed to vnc? If so, was wondering what happens if you log in remotely then just close the connection without logging out. The computer will no doubt stay on, but if you reconnect, does it ask for the password again, or just let you straight in?

---

### Post by Thrasonic on 2007-03-09
Wow, excellent information.  I was hoping it had the built-in capability like XP.  It appears that it does.  What about port forwarding?  Do I need to forward any ports to the Ubuntu IP address, and what ports would those be?

---

### Post by jkeyes0 on 2007-03-09
> **Thrasonic said:**
> Wow, excellent information.  I was hoping it had the built-in capability like XP.  It appears that it does.  What about port forwarding?  Do I need to forward any ports to the Ubuntu IP address, and what ports would those be?

You will need to forward port 5900.

benfindlay, if you close the connection, it will stay however you left it (logged in, locked, whatever), but it will ask for the password every time you open the connection again.

---

### Post by benfindlay on 2007-03-09
> **jkeyes0 said:**
> benfindlay, if you close the connection, it will stay however you left it (logged in, locked, whatever), but it will ask for the password every time you open the connection again.

Thats good to know! I have been putting off upgrading to 6.10 because I was worried about the security of the built in remote desktop stuff!

Thanks for that! :D

---

### Post by jkeyes0 on 2007-03-09
> **benfindlay said:**
> Thats good to know! I have been putting off upgrading to 6.10 because I was worried about the security of the built in remote desktop stuff!

Thanks for that! :D

Only thing about this is I believe you have to leave a logged-in session on the system you're remoting in to. You can lock the session, but it has to exist for you to remote. I'll test further and see, but I remember reading that somewhere.

EDIT: As it turns out, yes, you have to have a logged in session. I logged my home machine off, and now it is inaccessible from work.

---

### Post by Thrasonic on 2007-03-09
> **jkeyes0 said:**
> Only thing about this is I believe you have to leave a logged-in session on the system you're remoting in to. You can lock the session, but it has to exist for you to remote. I'll test further and see, but I remember reading that somewhere.

EDIT: As it turns out, yes, you have to have a logged in session. I logged my home machine off, and now it is inaccessible from work.

jkeyes0, thanks for the information.  So if I understand you correctly I need to log into Ubuntu before leaving for work, otherwise I won't be able to remotely connect?

---

### Post by jkeyes0 on 2007-03-09
> **Thrasonic said:**
> jkeyes0, thanks for the information.  So if I understand you correctly I need to log into Ubuntu before leaving for work, otherwise I won't be able to remotely connect?

Correct. You can log in and lock your system (Ctrl+Alt+L)

---

### Post by Thrasonic on 2007-03-09
No rebooting of the system though, it would seem.  Are there other options available that allow you to connect remotely while not already being logged into the system, say after a reboot?

---

### Post by jkeyes0 on 2007-03-09
> **Thrasonic said:**
> No rebooting of the system though, it would seem.  Are there other options available that allow you to connect remotely while not already being logged into the system, say after a reboot?

Well, you could either set your login to automatically log in after so many seconds (System ==> Administration ==> Login Window ==> Security and you can set up automatic login or timed login there.

Alternately, you could set up tightvncserver, but I haven't had much/any luck getting it to work out of the box.

---

### Post by Thrasonic on 2007-03-09
Okay.  You've given me some great ideas and information.  Thanks a ton for your help.

---

### Post by Thrasonic on 2007-03-12
So I'm trying this out and it's pretty bad, actually.  I'm guessing it's because I have to remote control into a PC on my home network first and than remote control into the Ubuntu box.  I'm assuming it's because of a firewall issue at work not letting VNC get outside onto the Internet.  That's my assumption, anyway.  Is there anything for Ubuntu like LogMeIn for Windows, where firewalls aren't an issue?

---

### Post by benfindlay on 2007-03-12
If its your home router then can't you just forward the relevant ports? I think it is 5900 and/or 5901 that you need to forward.

The other option you have is to restrict your "experience" of the remote desktop to, say, 8-bit in the connecting client software you use. I use tightvnc and it has that option!

---

### Post by Thrasonic on 2007-03-12
bump

---

### Post by Thrasonic on 2007-03-12
Hey benfindlay, thanks for the reply.  I'm pretty certain it's the company firewall restricting VNC out to the Internet.  I have VNC ports fwd'd on my home router to the Ubuntu box so that should be good to go.  And I do have the VNC client set to the lowest video selection.  Are there any other options for remote control with Ubuntu?  Is there anything like LogMeIn for Linux?

---

### Post by Ek0nomik on 2007-03-12
You should be able to port forward in your router.  Have you tried that?

---

### Post by Thrasonic on 2007-03-12
If you're referring to the company firewall, I don't have access to that.  Is that what you're referring to?

---

### Post by Ek0nomik on 2007-03-12
No, sorry, you replied just before me.  ;)

So you are trying to access your home Ubuntu computer from work, correct?  If the company has a firewall than it shouldn't matter, assuming you are positive your firewall at home is disabled (or you have the port open).

---

### Post by benfindlay on 2007-03-12
The only other thing I can suggest is to install the openssh-server on your ubuntu box and put putty on your computer at work (stand-alone executable so no need to worry about installation rights etc) That way you should be able to tunnel your vnc through the SSH protocol, which is far more secure to boot!

If its a business network I would assume they use SSH in at least some form or another for administration, so the ports for that should be open!

---

### Post by Thrasonic on 2007-03-12
> **Ek0nomik said:**
> No, sorry, you replied just before me.  ;)

So you are trying to access your home Ubuntu computer from work, correct?  If the company has a firewall than it shouldn't matter, assuming you are positive your firewall at home is disabled (or you have the port open).

You got it right.  My DSL router at home has the VNC ports forwarded to my Ubuntu box.  The ports that are forwarded are TCP/UDP 5900 to the Ubuntu box/IP.  I guess I should have someone test it from their own home DSL or cable modem service just to make sure it works over a less rigorously secured outbound connection.  If it works for them than maybe the problem is here at work with the firewall.  We use a MS ISA 2004 server here for our gateway/firewall and I'm pretty certain that some things are blocked going out.  I actually do have access to the ISA server, I just don't have the OK to make changes.  I could make changes, but I could get busted for it, too.  =)

---

### Post by Thrasonic on 2007-03-12
> **benfindlay said:**
> The only other thing I can suggest is to install the openssh-server on your ubuntu box and put putty on your computer at work (stand-alone executable so no need to worry about installation rights etc) That way you should be able to tunnel your vnc through the SSH protocol, which is far more secure to boot!

If its a business network I would assume they use SSH in at least some form or another for administration, so the ports for that should be open!

So using the openssh-server and putty cominbation should allow me to get out through the ISA 2004 server and access the Ubuntu box directly, instead of how I'm doing it now?  Let me know if I'm understanding you correctly.

---

### Post by benfindlay on 2007-03-12
Yes you understand correctly!

I must stress that I don't know for definite, but seeing as a lot of places use SSH for secure, remote admin I would think that it would be enabled. You use putty to connect to your computer at home (via SSH). Within putty you can set up a tunnel rule to forward traffic from the computer you are at to the remote location via the SSH session. Then you just direct your VNC client to connect to 127.0.0.7 (localhost) and putty takes care of the rest. As far as your work network will be concerned, there is only SSH traffic!

---

### Post by Thrasonic on 2007-03-12
> **benfindlay said:**
> Yes you understand correctly!

I must stress that I don't know for definite, but seeing as a lot of places use SSH for secure, remote admin I would think that it would be enabled. You use putty to connect to your computer at home (via SSH). Within putty you can set up a tunnel rule to forward traffic from the computer you are at to the remote location via the SSH session. Then you just direct your VNC client to connect to 127.0.0.7 (localhost) and putty takes care of the rest. As far as your work network will be concerned, there is only SSH traffic!

Wow, that sounds great.  Do you happen to know of a link where I could get some information on doing this step by step?  I am such a Linux newbie I don't know what I'm doing 99% of the time...  =)

---

### Post by benfindlay on 2007-03-12
Well to install openssh-server you just type ```
sudo apt-get install openssh-server
```
You're good to go there, no config needed for ssh!

There's a pretty good putty config guide here: [http://www.jfitz.com/tips/putty_config.html]("http://www.jfitz.com/tips/putty_config.html")

As for vnc, I would just use one of the guides here on the forum, but I think you already have the remote desktop stuff working, so that shouldn't be a problem!

Hope this helps!

---

### Post by thelinuxguy on 2007-03-12
Just to add to the information already on this thread, you can either "view your desktop remotely" or "log into your system remotely".

The first option is VNC which has been discussed extensively. It requires an active logged in session which you can control remotely.

The second option is remote login via XDMCP (Administration -> Login Window). Enable Remote Login and tweak the settings a bit. This doesn't require an active logged in session since you will be "logging in" from a remote machine. For logging in remotely from a Ubuntu box, look in the lower left corner of the screen where Ubuntu prompts for your username and password. There will be an option to login to another machine remotely. For doing this from Windows, you will need a program like XMing. Just be sure to google up the security of XDMCP before using it though.

---

### Post by Thrasonic on 2007-03-12
> **thelinuxguy said:**
> Just to add to the information already on this thread, you can either "view your desktop remotely" or "log into your system remotely".

The first option is VNC which has been discussed extensively. It requires an active logged in session which you can control remotely.

The second option is remote login via XDMCP (Administration -> Login Window). Enable Remote Login and tweak the settings a bit. This doesn't require an active logged in session since you will be "logging in" from a remote machine. For logging in remotely from a Ubuntu box, look in the lower left corner of the screen where Ubuntu prompts for your username and password. There will be an option to login to another machine remotely. For doing this from Windows, you will need a program like XMing. Just be sure to google up the security of XDMCP before using it though.

This sounds intriguing.  I might look into this.  One of the things I don't like about the way I'm doing it now is that I have to have already logged into Ubuntu in order to connect and take control remotely.  What you're talking about is more like what I had in mind.

---

### Post by Thrasonic on 2007-03-12
> **benfindlay said:**
> Well to install openssh-server you just type ```
sudo apt-get install openssh-server
```
You're good to go there, no config needed for ssh!

There's a pretty good putty config guide here: [http://www.jfitz.com/tips/putty_config.html]("http://www.jfitz.com/tips/putty_config.html")

As for vnc, I would just use one of the guides here on the forum, but I think you already have the remote desktop stuff working, so that shouldn't be a problem!

Hope this helps!

Cool.  I'll give this a try and see how it works.  Thanks for the help.

---

### Post by Thrasonic on 2007-03-12
> **benfindlay said:**
> Yes you understand correctly!

I must stress that I don't know for definite, but seeing as a lot of places use SSH for secure, remote admin I would think that it would be enabled. You use putty to connect to your computer at home (via SSH). Within putty you can set up a tunnel rule to forward traffic from the computer you are at to the remote location via the SSH session. Then you just direct your VNC client to connect to 127.0.0.7 (localhost) and putty takes care of the rest. As far as your work network will be concerned, there is only SSH traffic!

Well, I successfully installed the open-ssh program on my Ubuntu box.  Is there a way to check this?  From the terminal window it appears all went fine.

I DL'd putty and tried to set it up but it's not connecting to my home machine.  I'm not sure I've got the settings within putty correct.  There is always the possibility that our ISA server doesn't utilize or allow SSH outside, but I'd like to think not.  Also, on my home DSL router I have enabled SSH server so port forwarding to the Ubuntu box should be going on there.
I have a domain name that points to my static IP at home.  I can just use that in putty as the host name, correct?  In the tunnel section of the putty setup I'm assuming that I need to use localhost:22 as the forwarded port, and that I should have Local and Auto selected, which is underneath the port forwarding options mentioned in the last sentence.  

I'm not sure if it's all setup correct and it just won't work or if it's not setup correct.  Let me know what I can do to help you help me.  Thanks.

---

### Post by benfindlay on 2007-03-12
> **Thrasonic said:**
> Well, I successfully installed the open-ssh program on my Ubuntu box.  Is there a way to check this?  From the terminal window it appears all went fine.

I DL'd putty and tried to set it up but it's not connecting to my home machine.  I'm not sure I've got the settings within putty correct.  There is always the possibility that our ISA server doesn't utilize or allow SSH outside, but I'd like to think not.  Also, on my home DSL router I have enabled SSH server so port forwarding to the Ubuntu box should be going on there.
I have a domain name that points to my static IP at home.  I can just use that in putty as the host name, correct?  In the tunnel section of the putty setup I'm assuming that I need to use localhost:22 as the forwarded port, and that I should have Local and Auto selected, which is underneath the port forwarding options mentioned in the last sentence.  

I'm not sure if it's all setup correct and it just won't work or if it's not setup correct.  Let me know what I can do to help you help me.  Thanks.

You can sheck this by trying to SSH into the machine from another on the network. This won't tell you if port forwarding is working, but will tell you that SSH is running ok! Putty will only work on the local IP from within your network I believe. You need to be outside the lan to test it properly.

As long as port forwarding is set up right, you can use either the IP or the domain. I personally have a dynamic IP, so have to rely on dyndns.com to route my traffic from a made-up domain. The forwarded port you need in putty is 22 to get through the router.

For the tunneling to work you need to set 5900 and 127.0.0.1:5901 if you are on default. 5900 is source port and 127.0.0.1 goes in the destination (unless you have changed the options)

Hope this helps!

---

### Post by Thrasonic on 2007-03-12
benfindlay, just a quick note.  I did test the SSH capability on my internal network and it is working!  That's cool.  However, now I have to figure out how to connect from the office through the ISA server.  Like I said, it is possible that they aren't using SSH for anything so this might not work at all.  Is it possible to use port 80, where all the web traffic goes out, as the outbound port so that this will work?

---

### Post by Thrasonic on 2007-03-12
> **thelinuxguy said:**
> Just to add to the information already on this thread, you can either "view your desktop remotely" or "log into your system remotely".

The first option is VNC which has been discussed extensively. It requires an active logged in session which you can control remotely.

The second option is remote login via XDMCP (Administration -> Login Window). Enable Remote Login and tweak the settings a bit. This doesn't require an active logged in session since you will be "logging in" from a remote machine. For logging in remotely from a Ubuntu box, look in the lower left corner of the screen where Ubuntu prompts for your username and password. There will be an option to login to another machine remotely. For doing this from Windows, you will need a program like XMing. Just be sure to google up the security of XDMCP before using it though.

Wow, that Xming stuff is confusing to me.  I think it's a bit beyond my capabilities right now.  Thanks for the idea, but unless someone is going to walk me through getting this working I'll have to take a pass right now.

---

### Post by Thrasonic on 2007-03-13
Is it possible to use port 80, where all the web traffic goes out, as the outbound port so that this will work?  IOW, can the traffic from my PC for VNC be tunnelled through port 80 or something like that in some way?

---

### Post by thelinuxguy on 2007-03-15
> **Thrasonic said:**
> Wow, that Xming stuff is confusing to me.  I think it's a bit beyond my capabilities right now.  Thanks for the idea, but unless someone is going to walk me through getting this working I'll have to take a pass right now.

**Step 1:** Forward UDP port 177 on the router
**Step 2:** Configure Remote access options
[INDENT]System -> Administration -> Remote[/INDENT]
[INDENT]Change any options that you want. Default settings will work fine.[/INDENT]

**Step 3:** Enable XDMCP
[INDENT]```
gksudo gedit /etc/gdm/gdm.conf
```[/INDENT]
[INDENT]Scroll down to the section ```
[xdmcp]
```[/INDENT]
[INDENT]Change ```
Enable=false
``` to ```
Enable=true
```	(line no 263 on my system)[/INDENT]

**Step 4:** Download and install Xming-6-9-0-23-setup.exe from [http://sourceforge.net/project/showfiles.php?group_id=156984](http://sourceforge.net/project/showfiles.php?group_id=156984)
**Step 5:** Setup XMing on Windows box
[INDENT]After installation, start XLaunch (Start -> Programs -> XMing -> XLaunch)[/INDENT]
[INDENT]Screen 1: select One Window or Fullscreen as desired (preferably One Window)[/INDENT]
[INDENT]Screen 2: select "Open session via XDMCP"[/INDENT]
[INDENT]Screen 3: enter the IP address of the linux box with XDMCP enabled[/INDENT]
[INDENT]Screen 4: accept the default settings (Clipboard)[/INDENT]
[INDENT]Screen 5: click Save Configuration and save the file on desktop[/INDENT]
[INDENT]When you click finish, if XMing can communicate with the XDMCP enabled linux box, you should be presented with a login screen.[/INDENT]

For subsequent use, you can launch the configuration file you saved from screen 5. 
I would suggest you check the XDMCP stuff from a local LAN machine first and then check the forwarding from a machine on the internet.

Let me know if this helps.

---

### Post by gcvisel on 2007-03-15
Interesting thread to me right now.  I just got assigned to a temporary duty assignment for six weeks.  

I downloaded RealVNC4 to my laptop, and it's up and running, but how do I now contact my desktop at home, after setting it to allow remote access?   Does it have an address that I need to put in?  How do I find that?

Thanks for helping a noob!

Spook

---

### Post by thelinuxguy on 2007-03-22
> **gcvisel said:**
> Interesting thread to me right now.  I just got assigned to a temporary duty assignment for six weeks.  

I downloaded RealVNC4 to my laptop, and it's up and running, but how do I now contact my desktop at home, after setting it to allow remote access?   Does it have an address that I need to put in?  How do I find that?


1. You will need a VNC server on the desktop (and a VNC client on the laptop which you seem to have)
2. If your desktop is behind a router, you will need to forward the appropriate port (the one used by VNC server - typically 5900 but could be different) to your desktop 
3. You will need the IP address of your desktop. Start >> cmd >> ipconfig on Windows and [Terminal] >> ifconfig on Linux. Be sure to note the **external** IP address. 
4. You could also visit [http://myipaddress.com](http://myipaddress.com) for the external IP

---

