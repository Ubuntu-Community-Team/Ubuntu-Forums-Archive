---
title: "remote desktop from linux ubuntu 6.10 to windows xp home"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by dynoweb on 2007-05-25
I am using linux and I want to access my windows xp computer from my linux computer. 
How do I do that?
What steps do I take?
I am new to this so please give as much detail as possible.
If you need information about either computer just ask.
Thank you

---

### Post by Ek0nomik on 2007-05-25
> **dynoweb said:**
> I am using linux and I want to access my windows xp computer from my linux computer. 
How do I do that?
What steps do I take?
I am new to this so please give as much detail as possible.
If you need information about either computer just ask.
Thank you

You first need a vnc viewing client.

```
sudo aptitude install xvnc4viewer
```

now:

```
xvnc4viewer xxx.yyy.zzz.vvv
```

Tada.  :)

You also need a vnc server running on Windows.  UltraVNC is my personal favorite, so install that on Windows and you are all set.

---

### Post by BHelts on 2007-05-25
the previous poster is correct in certain circumstances.  are you wanting to access your xp box over a LAN or through the internet?  if you want to access over the internet do you have a router, do you run any firewall applications?  these are things that will need to be addressed for it to work properly.
You also don't necessarily need to use VNC, RDP will work as well, but needs to be enabled on the XP machine.

---

### Post by Ek0nomik on 2007-05-25
> **BHelts said:**
> the previous poster is correct in certain circumstances.  are you wanting to access your xp box over a LAN or through the internet?  if you want to access over the internet do you have a router, do you run any firewall applications?  these are things that will need to be addressed for it to work properly.
You also don't necessarily need to use VNC, RDP will work as well, but needs to be enabled on the XP machine.

True, RDP will work, however it should be noted that RDP will log you out of your local session on Windows.  If you use VNC, you can watch your mouse move on the Windows box.  (It won't log you out)

---

### Post by BHelts on 2007-05-25
> True, RDP will work, however it should be noted that RDP will log you out of your local session on Windows. If you use VNC, you can watch your mouse move on the Windows box. (It won't log you out)

excellent point, i'd forgotten that.  thanks.

---

### Post by dynoweb on 2007-05-25
> **Ek0nomik said:**
> You first need a vnc viewing client.

```
sudo aptitude install xvnc4viewer
```

now:

```
xvnc4viewer xxx.yyy.zzz.vvv
```

Tada.  :)

You also need a vnc server running on Windows.  UltraVNC is my personal favorite, so install that on Windows and you are all set.


I have run the 2 sets of code in the terminal and this is the end result.
Please view attachment:

and where do i get VNC server so I can get it to run on my windows computer?

---

### Post by Ek0nomik on 2007-05-25
> **dynoweb said:**
> I have run the 2 sets of code in the terminal and this is the end result.
Please view attachment:

and where do i get VNC server so I can get it to run on my windows computer?

Replace xxx.yyy.zzz.vvv with your own IP.

[http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/) is what I use on Windows for VNC.

---

### Post by BHelts on 2007-05-25
```
xvnc4viewer xxx.yyy.zzz.vvv
```
xxx.yyy.zzz.vvv is meant to be the IP address on your windows machine.

you can get a vnc server for windows at [UltraVNC]("http://uvnc.com") or [TightVNC]("http://tightvnc.com")

---

### Post by dynoweb on 2007-05-25
> **Ek0nomik said:**
> Replace xxx.yyy.zzz.vvv with your own IP.

[http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/) is what I use on Windows for VNC.

ok i used my ip address  and i got this crazy stuff.

please view screenshot-1.png

did i use the wrong ip address ?

I want to use the remote desktop thru a router.....

---

### Post by owise1 on 2007-05-25
Vncserver also loads up a small web server that allows you to access via a browser (like firefox) on any PC running any OS.  Once VNCServer is running point your browser to [http://www.xxx.yyy.zzz:5801](http://www.xxx.yyy.zzz:5801) where [www.xxx.yyy.zzz](www.xxx.yyy.zzz) if the ip address on your LAN.  I use this for my oldest boy to access Gaim on the Linux box to avoid all those nasty bugs that come with MSNMessenger!  Works well.

---

### Post by owise1 on 2007-05-25
Screen shot showing VNC on firefox.

---

### Post by nae5 on 2007-05-25
i read this post because i am interested in doing the same thing, so thanks for the info.

will this work for a winxphome pc that is using dhcp? or do i need a static one? 
im also new with linux so i may not understand if these steps allow me to see and manipulate my desktop? or just access files, and if so what types?  

thnx for the help

---

### Post by dynoweb on 2007-05-25
> **owise1 said:**
> Vncserver also loads up a small web server that allows you to access via a browser (like firefox) on any PC running any OS.  Once VNCServer is running point your browser to [http://www.xxx.yyy.zzz:5801](http://www.xxx.yyy.zzz:5801) where [www.xxx.yyy.zzz](www.xxx.yyy.zzz) if the ip address on your LAN.  I use this for my oldest boy to access Gaim on the Linux box to avoid all those nasty bugs that come with MSNMessenger!  Works well.

so I am not sure what you mean because i get nothing when i do that.
in the  window i get no use of the windows desktop from my linux 
I am so confused

---

### Post by owise1 on 2007-05-25
I have 6 pc of a mix of XP and Linux (Ubuntu and SUSE) connected to a LAN via Wifi and hard link.  The addresses are all provided by DHCP and do not change over time.  You can look at the DHCP client list on your router to see what PC is given what IP address.

You will be able to use your desktop as if you were at it.  I share files via a common server that supplies the XP machine via SAMBA and the Linux ones via NFS.

Have fun

---

### Post by BHelts on 2007-05-25
as far as the wacky windowing behavior with the screenshot, i think that is what happens when you connect to the machine you are on.  you want to enter the IP address of the windows box, assuming you are on your ubuntu machine and trying to connect to the windows.

> will this work for a winxphome pc that is using dhcp? or do i need a static one?
im also new with linux so i may not understand if these steps allow me to see and manipulate my desktop? or just access files, and if so what types?

this will work on a machine with DHCP, but the ip address may change, so you just need to be aware of that.  as far as manipulating desktop and files and such, everything you will be doing will actually be on the machine you are remote controlling.  the only thing sent over the network are keystrokes, mouse movements and video.

---

### Post by owise1 on 2007-05-25
Your XP machine will need a bit of java to run the applet - see [http://www.cs.vu.nl/~eliens/documents/vnc/start.html](http://www.cs.vu.nl/~eliens/documents/vnc/start.html)
for more help.

---

### Post by BHelts on 2007-05-25
on your xp machine you may need to open up a port in windows firewall if you are running it to get it to work, if you are running a different firewall (norton, trendmicro, etc.) that firewall will need to be opened up as well.

---

### Post by owise1 on 2007-05-25
> **BHelts said:**
> on your xp machine you may need to open up a port in windows firewall 

If you use the web browser technique you will also have to open port 5801  - normal browser traffic is on port 80.

cheers

---

### Post by dynoweb on 2007-05-25
Ii still cannot figure this out. I need someone to do it for me..... so.... maybe someone can come onto my computer and do it for me.

what is the xdmcp used for then?

---

### Post by Inxsible on 2007-05-25
> **dynoweb said:**
> ok i used my ip address  and i got this crazy stuff.

please view screenshot-1.png

did i use the wrong ip address ?

I want to use the remote desktop thru a router.....

You dont have to use your own IP address, you have to put in the IP address of the system that you are trying to access. In your case that would be the XP box. 

But since you haven't yet installed VNCServer on your XP machine, it would not work. First install the VNCServer on the XP box and then also get its IP address. Use that IP address on your Ubuntu machine

---

### Post by mojo123 on 2007-05-25
[www.logmein.com]("www.logmein.com")

---

### Post by nae5 on 2007-05-25
once again thnx for the help.  i am actually using 6.06 and it also works,

i installed the ultra vnc client on the winxphome pc 1.0.2 and the sudo aptitude vnc4viewer(mentioned above) on the ubuntu. it works.  couple more questions though, 

can i use it in reverse?

was the code in the beginning of this thread (4 my ubuntu desktop) the entire server viewer combo i installed on my winxphome pc?

because i see on the winxp comp the server viewer runnables in start menu, but i dont know the commands to run the server on the ubuntu desktop? so that i can access it with the viewer on the winxp laptop.

last one, :O)  .. im working through confusion..  .. if i can see the config gui for the server in the linux box.. are these where i make changes to view with xplaptop my buntuserver over the internet? 

or was i already doing that? i thought it might be over our LAN cuz my 192.168.1.xxx ip is only an ip from my comp to router and not from internet to router? ?  so do i have to connect to router then server with my viewer when i am somewhere in lets say china?

if i need to clarify plz tell me. i spent a while just articulating this one..

just edited vnc program type ultra vnc 1.0.2

---

### Post by BHelts on 2007-05-25
ok, you're doing great!
go to your xp box.  go to start>all programs>whatever VNC client you installed>start vnc server
go to start>run and type in CMD
at the prompt type in ipconfig and write down the number where it says "IP Address"
go to start>control panel and if you have a white screen with icons click on Windows Firewall
if you have a blue screen with writing, click on "Switch to classic view" in the upper left hand corner, then click on Windows Firewall.
In windows firewall, if it is on, click on the Exceptions tab and then click on new.  Give it a name, like VNC and put in port 5900 if you are going to use VNC viewer or 5801 if you are going to use firefox.
click add or ok or next or whatever and make sure the new entry in the exceptions tab is checked.
if you have another firewall or windows firewall is off, let me know.
go back to your ubuntu machine.  open up terminal (applications>accessories>terminal and type in
vncviewer 192.168.1.100, replacing 192.168.1.100 with whatever the IP Address you wrote down was from the windows machine.  that should do it.

---

### Post by dynoweb on 2007-05-25
i am totally lost nothing is working for me.

treat me like i dont know anoything about computers and this is the first time i have sat infront of one.
PLEASE

I just want to know how do I access another computer(win xp home) from my linux(ubuntu 6.10 edgy eft) and have access to where i can open files and run programs ..... I want to make it to where as if it was that i was sitting infront of the windows xp computer.

Can anyone help?

Can I use the xdmcp thing? 

both computers are in the same room connected through a router.

---

### Post by BHelts on 2007-05-25
can you be more specific?  where are you getting caught up?  are you getting any errors?

---

### Post by dynoweb on 2007-05-25
> **BHelts said:**
> can you be more specific?  where are you getting caught up?  are you getting any errors?

well when i seem to be doing the stuff said at the beginning, and nothing is working and then people come on the forum and say oh good it works..... I dont know what the heck i am doing wrong. because obviously i am supposed to get a result ..... but I dont get anything.nothing no errors nothing.

---

### Post by BHelts on 2007-05-25
which part specifically

---

### Post by dynoweb on 2007-05-25
> **BHelts said:**
> which part specifically

specifically the vnc viewer, and everything after it.

to be more specific... when i tried to install the vnc stuff nothing happened except the stupid window where i could not do anything except look at the desktop of MY COMPUTER I am on.   I wanted to access another computer... not my laptop....

---

### Post by dynoweb on 2007-05-25
> **dynoweb said:**
> specifically the vnc viewer, and everything after it.

to be more specific... when i tried to install the vnc stuff nothing happened except the stupid window where i could not do anything except look at the desktop of MY COMPUTER I am on.   I wanted to access another computer... not my laptop....





WELL I guess I am on my own on this.


UNLESS someone else sees this forum..

---

### Post by Ek0nomik on 2007-05-26
Alright **dynoweb**, it's time to solve this problem of yours.

[http://internap.dl.sourceforge.net/sourceforge/ultravnc/UltraVNC-102-Setup.exe](http://internap.dl.sourceforge.net/sourceforge/ultravnc/UltraVNC-102-Setup.exe)

Download UltraVNC from the link above, on your **Windows** computer.

Go through all the steps, (make sure you install the *Server* (and viewer if you wish)).  It should ask you if you want to run it as a System Service, and I would choose yes so it will startup every time you reboot your computer.

Now, are both computers hooked up on a LAN with a single external IP?  If this is the case, you will want to connect via your internal IP's  (192.168.1.100, etc)  To figure out your internal IP, go to Start/Run than type cmd.  Run the command ipconfig, and it should tell you what your address is.

If you are using an external IP, visit [http://whatsmyip.org/](http://whatsmyip.org/) and make note of what your IP is.

Now, on the **Ubuntu** side of things:

Install a VNC viewing application.

```
sudo aptitude install xvnc4viewer
```

Now, connect to your Windows computer:

```
xvnc4viewer 192.168.1.100
```

or

```
xvnc4viewer my.external.ip.here
```

Let me know how it goes, I will be sure to check the thread in a few.

---

### Post by nae5 on 2007-05-27
thnx for the thread, you guys are very succinct and very helpful

I would like to figure out a couple more things if you would:

I have the server and viewer working on my two winxp computers and i can view each of those on the ubuntu computer with the terminal install and input you provided above.

How can i run the server on the ubuntu computer? so that i can view it as well? i installed the windows version with wine but when i connect to view with a winxp comp the viewer closes right after opening tho the first time i saw the ubuntu desktop.  

And after that: at the moment these computers are all on our home network.  so i am using *internal* ips? with the viewer to identify which server to connect to, ...yea.. ?

i went to whatsmyipaddress.org and found my *external* ip ? when i use that with a viewer it doesn't work, is there another process for accessing one or more comp from an ..*external* ip? which i am thinking is the routers ip, no?

or do i simply have to be at another access point for the external ip to be taken into account? 

your help has been extremely helpful to me

---

### Post by reed026 on 2007-07-01
Hello, I have a similar problem, but it involves another Operating System.

I have been able to get VNC to work on my windows XP computer to run various files through the network that I am unable to run through Ubuntu or Wine. 

Now, I have 2 DSL (Damn Small Linux) computers I would like to be able to remove view.

I already have VNC set up on one of the DSL boxes and properly configured, however when I run the vncviewer 192.168.1.102:5901 command in the terminal, the window opens and asks for a pass which I supply then it opens the OS window. However, all I get is the odd background before flux loads. 

I have included a screenshot of what I am seeing.

---

### Post by liviubero on 2007-08-29
> **Ek0nomik said:**
> Alright **dynoweb**, it's time to solve this problem of yours.

[http://internap.dl.sourceforge.net/sourceforge/ultravnc/UltraVNC-102-Setup.exe](http://internap.dl.sourceforge.net/sourceforge/ultravnc/UltraVNC-102-Setup.exe)

Download UltraVNC from the link above, on your **Windows** computer.

Go through all the steps, (make sure you install the *Server* (and viewer if you wish)).  It should ask you if you want to run it as a System Service, and I would choose yes so it will startup every time you reboot your computer.

Now, are both computers hooked up on a LAN with a single external IP?  If this is the case, you will want to connect via your internal IP's  (192.168.1.100, etc)  To figure out your internal IP, go to Start/Run than type cmd.  Run the command ipconfig, and it should tell you what your address is.

If you are using an external IP, visit [http://whatsmyip.org/](http://whatsmyip.org/) and make note of what your IP is.

Now, on the **Ubuntu** side of things:

Install a VNC viewing application.

```
sudo aptitude install xvnc4viewer
```Now, connect to your Windows computer:

```
xvnc4viewer 192.168.1.100
```or

```
xvnc4viewer my.external.ip.here
```Let me know how it goes, I will be sure to check the thread in a few.

I have done this and the result, when I try to connect to the xp machine (sharing the same router as the Ubuntu one) I get, in the terminal:

> 
liviu@liviu-laptop:~$ xvnc4viewer 192.168.178.20

VNC Viewer Free Edition 4.1.1 for X - built Jan  7 2007 17:30:38
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Aug 29 20:10:55 2007
 CConn:       connected to host 192.168.178.20 port 5900
 CConnection: Server supports RFB protocol version 3.4
 CConnection: Using RFB protocol version 3.3
 CConnection: Unknown 3.3 security type -6
 main:        Unknown 3.3 security type

and a window telling me that "Unknown security tipe 3.3" (VNC Viewer: Information.png image)

If I try with Firefox, the I get to the login window, but even I introduce the right name and pass, I get rejected (images Firefox1 and Firefix2).

I have no idea how to set this up and I am about to uninstall Ultravnc from the xp machine.

---

