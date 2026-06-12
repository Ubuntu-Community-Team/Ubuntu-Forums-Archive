---
title: "Best VNC program to use with Ubuntu"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-02-09
What is the best VNC program to use in conjunction with viewing between Ubuntu machines in both the sense of reliability and easy of use ?  Is this tightvnc or some other flavor ?

Also, if I am wanting to view say another machine (my brother-in-laws) at his house and he is connected to the internet using Verizon DSL (the same as I am using), what string parameter or IP machine identifying information do I need in order to view his machine from my machine at my house ?  Do I need to know how his machine is referenced by the Verizon network or just simply his Ubuntu machine name and/or IP address ?

Thanks.

---

### Post by PinkFloyd102489 on 2008-02-09
I use RealVNC viewer, because I have RealVNC Server on my XP machine. However, the built-in VNC server in Ubuntu, vino, works just fine for me.



In order to view his machine, have him set up remote desktop. If he has a router, forward port 5900 to the machine you want to connect to. Then put SOME.IP.GOES.HERE:0


The :0 is the X server display you want to connect to, usually :0 unless you have separate dual monitors.

---

### Post by wpshooter on 2008-02-09
> **PinkFloyd102489 said:**
> I use RealVNC viewer, because I have RealVNC Server on my XP machine. However, the built-in VNC server in Ubuntu, vino, works just fine for me.



In order to view his machine, have him set up remote desktop. If he has a router, forward port 5900 to the machine you want to connect to. Then put SOME.IP.GOES.HERE:0


The :0 is the X server display you want to connect to, usually :0 unless you have separate dual monitors.

When you say "**have him set up remote desktop**", is that a sub-function of the Vino package or it that another package altogether ?

Thanks.

---

### Post by wpshooter on 2008-02-10
> **PinkFloyd102489 said:**
> I use RealVNC viewer, because I have RealVNC Server on my XP machine. However, the built-in VNC server in Ubuntu, vino, works just fine for me.



In order to view his machine, have him set up remote desktop. If he has a router, forward port 5900 to the machine you want to connect to. Then put SOME.IP.GOES.HERE:0


The :0 is the X server display you want to connect to, usually :0 unless you have separate dual monitors.

The instructions that I found regarding port forwarding for a Westell 6100 said to forward ports 5500 and 5800 in addition to port 5900.

Do all 3 of these ports need to be forwarded in order for VNC to work properly ?  And will forwarding these ports comprise the security of my system in any way ?

Thanks.

---

### Post by ve9gj on 2008-02-10
> **wpshooter said:**
> The instructions that I found regarding port forwarding for a Westell 6100 said to forward ports 5500 and 5800 in addition to port 5900.

Do all 3 of these ports need to be forwarded in order for VNC to work properly ?  And will forwarding these ports comprise the security of my system in any way ?

Thanks.

Port 5900 (tcp) is the only port needed for vnc

Port 5800 (tcp) is used if you have the vnc java for a web browser running.  It will also require port 5900.

I don't know what 5500 is for.

vnc traffic is not encrypted so at the very least have a very good password.  Anyone with access to the packets could with the right tools and knowlegde "sniff" the password.
A good idea is to have a user start vncserver only when you are going to use it and kill it when you are done.  This won't work if there is nobody at the other end however!

IMHO vnc over a ssh tunnel is much more secure.  ssh should be locked down so only accounts with a good password are allowed to login.  google for vnc over ssh to get an idea how this works.

---

### Post by wpshooter on 2008-02-20
> **PinkFloyd102489 said:**
> I use RealVNC viewer, because I have RealVNC Server on my XP machine. However, the built-in VNC server in Ubuntu, vino, works just fine for me.



In order to view his machine, have him set up remote desktop. If he has a router, forward port 5900 to the machine you want to connect to. Then put SOME.IP.GOES.HERE:0


The :0 is the X server display you want to connect to, usually :0 unless you have separate dual monitors.

Please note that my brother-in-law is not on the same LAN which is located at my residence (his computer is at his house across town).

Can this VNC be made to function from my house to his house if we are both using the same ISP (Verizon DSL) ?  I have called Verizon about this and they were ZERO help.

Thanks.

---

### Post by timcredible on 2008-02-20
with regards to vnc, i would suggest using x11 instead, my tutorial [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27").  really guys, c'mon, why install a second window manager on your linux box, just use what's already there - x11.

as for how to connect, you have to connect to the remote's routable IP address, which you can find by going into the dsl modem and seeing what the routable ip address is.  you probably access that dsl modem by going to [http://192.168.1.1](http://192.168.1.1) in your browser.  you'll also need to setup your dsl modem for port forwarding, I have the ports listed in my tutorial.

---

### Post by bodhi.zazen on 2008-02-20
VNC is covered in the Ubuntu wiki :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

[uwiki]FreeNX[/uwiki] is also popular.

@timcredible: why not just ssh -X ?

```
xinit -e ssh -XCT user@server fluxbox -- :1
```

Also I find Xephyr is more reliable then xnest : [http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

[[img]http://cafelinux.org/OptickleArt/albums/userpics/normal_Xephyr.png[/img]](http://cafelinux.org/OptickleArt/albums/userpics/Xephyr.png)

*Click to enlarge*

---

### Post by wpshooter on 2008-02-20
Thanks, I will try to digest all this when I get home.

---

### Post by fatdadkev on 2008-02-20
I use UltraVNC on my PC's.
As long as you have port forwarding on the router or the router is NAT friendly (the port will normally open by itself if its is) you should be OK..

you just normally pop the IP address of the remote machine in Ubunutu terminal server client and sometimes need portnumber at the end where obviously you put your port number in i.e :5900 at the end of the IP.

I've connected to my brothers machine with this and he was on a seperate ISP so it had no trouble linking up.
A program I use quite a lot and have great success with is Hamachi - 
[http://linux.softpedia.com/get/System/Networking/Hamachi-9968.shtml](http://linux.softpedia.com/get/System/Networking/Hamachi-9968.shtml)
You can get it for Windows and Linux, run it - set up a username and password then set yourself a network and add in the username of your guest.
If you both then run Hamachi it creates a private VPN between the two machines that will traverse most NAT firewalls.

We use it to play LAN games  but via the internet - it assigns a temporary IP to the Hamachi network VPN and thus puts you both on the same subnet and the same Lan.
Using this you can easily use VNC and type the local iP of the remote machine i.e 192.168.0.10 and your connected !
If that doesn't work then sometimes typing the Hamachi IP (it normally shows you its special IP in the Hamachi control panel) will link you instead.

Its a great little program and as an example of how easy it is, I linked to my brothers machine, I could see and use his printer, he could see and use mine - we could also see each others shared folders where we had allowed guest permissions.

---

### Post by wpshooter on 2008-02-20
> **timcredible said:**
> with regards to vnc, i would suggest using x11 instead, my tutorial [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27").  really guys, c'mon, why install a second window manager on your linux box, just use what's already there - x11.

as for how to connect, you have to connect to the remote's routable IP address, which you can find by going into the dsl modem and seeing what the routable ip address is.  you probably access that dsl modem by going to [http://192.168.1.1](http://192.168.1.1) in your browser.  you'll also need to setup your dsl modem for port forwarding, I have the ports listed in my tutorial.

However, a few questions before I get home.  

When you say **routable IP address**, is that the exact descriptor of the IP address that I will be looking for in the router's configuration program ?  

Or might this be referred to by some other name ?

Also, Verizon tells me that the name descriptor for my router "**myhome.westell.com**" is NOT a unique identifier to just ME, i.e. my brother-in-laws router name/domain is probably also myhome.westell.com. 

Does that mean that ultimately,  I am going to be forced to ask Verizon for a unique/static IP address identifier for my computer(s) or this is NOT going to work from my home to my brother-in-laws home ?

Thanks.

---

### Post by bodhi.zazen on 2008-02-20
You can see your public IP address here : [http://www.showip.com/](http://www.showip.com/)

The problem is your IP is assigned to you by your IP provider and they likely use DCHC, so it may change.

So you need to either purchase a static IP from your IP provider or use something like this :

[http://www.showip.com/](http://www.showip.com/)

there are other free services as well :)

=======

Last you have to configure your router to forward the ports. That varies by router (read your router documentation).

You can also do this :

[http://ubuntuforums.org/showthread.php?t=256102](http://ubuntuforums.org/showthread.php?t=256102)

---

### Post by wpshooter on 2008-02-20
> **bodhi.zazen said:**
> You can see your public IP address here : [http://www.showip.com/](http://www.showip.com/)

The problem is your IP is assigned to you by your IP provider and they likely use DCHC, so it may change.

So you need to either purchase a static IP from your IP provider or use something like this :

[http://www.showip.com/](http://www.showip.com/)

there are other free services as well :)

=======

Last you have to configure your router to forward the ports. That varies by router (read your router documentation).

You can also do this :

[http://ubuntuforums.org/showthread.php?t=256102](http://ubuntuforums.org/showthread.php?t=256102)

Thanks.

Is the link for the show address correct ?  When I click on it here at work on my M/S windows computer it says that it can not be displayed ?

Thanks.

Never mind, I see that our IT department has access to that site blocked.  I will check it out when I get home.  Seems that I can hardly do anything on this machine anymore !!!

---

### Post by wpshooter on 2008-02-20
> **timcredible said:**
> with regards to vnc, i would suggest using x11 instead, my tutorial [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27").  really guys, c'mon, why install a second window manager on your linux box, just use what's already there - x11.

as for how to connect, you have to connect to the remote's routable IP address, which you can find by going into the dsl modem and seeing what the routable ip address is.  you probably access that dsl modem by going to [http://192.168.1.1](http://192.168.1.1) in your browser.  you'll also need to setup your dsl modem for port forwarding, I have the ports listed in my tutorial.

timcreible:

In your tutorial you refer to going to the main login window by clicking on "session".  I don't seem to see this in Ubuntu/Gutsy.   Are you referring to what I see as Terminal Server Client under Applications/Internet ?  When I open the Terminal Server Client I can get it to remote to one of my other machines on my LAN by using the VNC protocol from the drop-down listing but the XDMCP protocol that you refer to in your tutorial is grayed out/not accessible.  I looked for it under Synaptic but I do not seem to see anything by that exact name, however there is a "LIB" program with XDMCP in it that is shown as already being installed.  Is there something else I need to install to get the XDMCP to be listed in the terminal server client ?

Also, once I do get control of the other computer thru terminal server client and then when I end the session the connector diagonal box keeps coming back with an error connection message but the diagonal goes away if I just hit the cancel on the diagonal.  Any idea as to why I get this connection error after I exit the remote session ?

Thanks.

---

### Post by daflame on 2008-02-22
You could also use FreeNX as was posted earlier.  Most of the grunt work is done for you.  The only exception is accessing someone's active desktop, but XDMCP doesn't access the local desktop either.

I've built a forum here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by MountainX on 2008-02-27
> **timcredible said:**
> with regards to vnc, i would suggest using x11 instead, my tutorial [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27").  really guys, c'mon, why install a second window manager on your linux box, just use what's already there - x11.
l.

I would like to use X11 and your tutorial, but your link is broken.

Does anyone know of a tutorial for this? I want to connect my Ubuntu Gutsy desktop (or laptop) to a Unbuntu 7.10 server at Linode.com (no GUI).

---

### Post by bodhi.zazen on 2008-02-27
For ssh see the Ubuntu wiki :

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by MountainX on 2008-02-27
Thanks for the ssh links. Reading over it quickly, it sounds like OpenSSH will do everything I need it to do. Is there a reason to Consider FreeNX or NX Free? Does their compression make things run faster than ssh? (I'm a noob)

---

### Post by bodhi.zazen on 2008-02-27
Depends on what you want.

ssh gives you a command line, which is all you (I) really need to remote admin.

You can ssh -X to forward single apps, which again is usually just fine.

You can ssh -X with compression (blowfish) , adding compression helps if you are outside your LAN (ie over the internet). (if you are ssh over a LAN, compression can slow you down).

FreeNX = entire desktop and may be overkill if you are comfortable with the command line. FreeNX adds security and speed to VNC connections.

---

### Post by MountainX on 2008-02-27
I see I have a lot to learn. What I want is to access my Linode Ubuntu server (over the Internet) using an entire X Desktop GUI locally. I particularly want to have multiple instances of Nautilus open. I don't care how good I get at the command line, I will never be as productive as I could be without a GUI file manager. With a GUI file manager, Cream and/or GEdit, and a terminal, I'm OK for most things. 

Anyway, it seems like I need more than just ssh. Maybe NX is the way to go....

---

### Post by rfdeshon on 2008-02-28
> **MountainX said:**
> I see I have a lot to learn. What I want is to access my Linode Ubuntu server (over the Internet) using an entire X Desktop GUI locally. I particularly want to have multiple instances of Nautilus open. I don't care how good I get at the command line, I will never be as productive as I could be without a GUI file manager. With a GUI file manager, Cream and/or GEdit, and a terminal, I'm OK for most things. 

Anyway, it seems like I need more than just ssh. Maybe NX is the way to go....

You shouldn't say never. I always said I would never be as productive at a command line as I was with a GUI but when I was forced to used the command line (working on servers with no X installed, better performance and all that) I found that I can be much more productive on the command line. Anyway, to chime in and reiterate what was said earlier, if you want to do full desktop, the easiest is probably just to enable XDM for remote logins as one of the other people posting earlier mentioned. The link which he posted that I found helpful is [here.]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27") Why install any extra software if you don't really need to right? I do believe one of the core computing principles is still KISS - Keep It Simple, Stupid.

---

### Post by MountainX on 2008-02-28
Thank you. However, the link is not working. 

[http://www.linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27](http://www.linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27)

if you remove one of the double dashes, you get a Google ads spam site (I think).

---

### Post by rfdeshon on 2008-02-28
Very odd. The links are working just fine for me.
I did a bit more reading, I guess there is a problem with XDMCP in Gutsy so maybe I was wrong about that being the better option. I guess you could check out this article here on the [Ubuntu Wiki]("https://wiki.ubuntu.com/RemoteAccess?highlight=%28remote%29")

---

### Post by MountainX on 2008-02-28
Thanks again. 

I found a bunch of other good stuff with this Google search:
[http://www.google.com/search?num=50&hl=en&safe=off&q=x11+over+ssh+compiz&btnG=Search](http://www.google.com/search?num=50&hl=en&safe=off&q=x11+over+ssh+compiz&btnG=Search)

The Linode forum pointed me to that search and this link:
[http://digg.com/linux_unix/Tutorial_Forwarding_GNOME_over_SSH](http://digg.com/linux_unix/Tutorial_Forwarding_GNOME_over_SSH)

After reading that I am more confused than ever.

Am I off base in thinking that I can have the kind of experience I'm used to when I connect to a Windows server with Remote Desktop (or Ubuntu's Terminal Server Client)? Windows 2003 server has a full GUI obviously, and when I connect to a remote Windows server over the Internet, I have an experience almost exactly the same as if I were sitting at the machine. I often run the remote session full screen across dual monitors (1920 x 1200 each) and there are almost no restrictions on the work/tasks I can do on the server.

What I think I understand so far about connecting to my Linode (Ubuntu 7.10 server which does not have a GUI installed) is that if I want this kind of experience, I need to use nomachine.com's NX server. Is that correct?

---

### Post by rfdeshon on 2008-02-29
Hmm... The fact that you don't have a GUI installed on your Linode would mean that you can't really do an RDP-type of setup. In an RDP style system, everything runs on the server but is displayed on the client, so if you want to run nautilus, it has to be installed on the server then the window is simply drawn on the client machine. Sounds to me like what you should do is set up OpenSSH on your linode then just mount anything you want to work on on your client ubuntu box (go to Places... Connect to Server... Choose SSH, fill out info). This will let you use the GUI on your client computer to interact with the files on your server computer. That sounds more like what you are trying to do.

---

