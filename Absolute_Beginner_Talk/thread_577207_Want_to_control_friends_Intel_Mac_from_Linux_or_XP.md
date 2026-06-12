---
title: "Want to control friends Intel Mac from Linux or XP (Via VNC or..?)"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by wilberfan on 2007-10-15
I have a wonderful friend who just bought her first REAL computer--a MacBook Pro.  (Up to now she's used Windows hand-me-downs).

She's frighteningly inexperienced, though, when it comes to computers (for example, she struggles with the concept of dragging-and-dropping files to move them around)!!

Bless her heart, she's so eager to learn--and she's constantly calling me and asking for my help.   Those of you who have tried to help someone with their computer over the phone without seeing what they're looking at--know how absolutely maddening that can be!

I've just now heard about VNC, and it sounds like that might do the trick--but I'm guessing I've got a lot to learn about setting it up, etc...

I have two computers at home:  They both have Windows XP and a couple different flavors of Linux (Ubuntu and Sidux).   

Can anyone point me towards what I need to load/run on our respective machines (Mac OS X on her end--Windows and/or Linux on my end) so that I can control her laptop remotely?

:cool:

---

### Post by wormser on 2007-10-16
First off, OSX 10.5 is about to come out and she should have waited a few weeks for it.  I would check to see if she can upgrade for free when it comes out.

[Redstone software]("http://www.redstonesoftware.com/downloads/index.html") makes a VNC server for the Mac.  Just download it and drag and drop into the application's folder.  You will have to go into the Mac's control panel and open up ssh.  Yes, ssh and not VNC.  You need to tunnel your VNC connection via ssh for security.  Next open up port 22 on her router's firewall.  Now you can use vncviewer on your Ubuntu machine to connect.  First start the  ssh tunnel:  ssh -L 5900:localhost:5900 username@herIP.  Now in a another terminal: xvncviewer localhost:5900.  It should now be connected.  Good Luck and let us know how it goes.

---

### Post by wilberfan on 2007-10-16
> **wormser said:**
> First off, OSX 10.5 is about to come out and she should have waited a few weeks for it.  I would check to see if she can upgrade for free when it comes out.

Yes, I thought about that already...    I can almost guarantee she doesn't care--nor would she even notice the difference?  :)  

> [Redstone software]("http://www.redstonesoftware.com/downloads/index.html") makes a VNC server for the Mac.  Just download it and drag and drop into the application's folder.  You will have to go into the Mac's control panel and open up ssh.  Yes, ssh and not VNC.  You need to tunnel your VNC connection via ssh for security.  Next open up port 22 on her router's firewall.  Now you can use vncviewer on your Ubuntu machine to connect.  First start the  ssh tunnel:  ssh -L 5900:localhost:5900 username@herIP.  Now in a another terminal: xvncviewer localhost:5900.  It should now be connected.  Good Luck and let us know how it goes.

Well, you've made this sound insanely easy!   I'm sure I'll have questions--but I probably won't have access to her machine for a few days.   [Hmmm.   I wonder if I could try this out on my bosses G5?!   Iron out the wrinkles?!   There's a Gutsy box right next to it on the desk!]

Did you perhaps mean xvnc_4_viewer?  I notice that's already installed in Gutsy...

Can't wait to get this going!  This will be WAY cool if this works!!  :guitar:

---

### Post by wormser on 2007-10-16
> **wilberfan said:**
> Yes, I thought about that already...    I can almost guarantee she doesn't care--nor would she even notice the difference?  :)  

Well, you've made this sound insanely easy!   I'm sure I'll have questions--but I probably won't have access to her machine for a few days.   [Hmmm.   I wonder if I could try this out on my bosses G5?!   Iron out the wrinkles?!   There's a Gutsy box right next to it on the desk!]

Did you perhaps mean xvnc_4_viewer?

The command is xvncviewer.  It might be version 4 but the command is the same.  You can also use Terminal Server Client under Applications> Internet.

There are some cool new features in 10.5 and if you can get it upgraded for free I would do it.

If you are going to try it on your boss's G5 make sure you download the correct version.

---

### Post by wilberfan on 2007-10-16
I just tried this with the bosses G5, and I got the following messages:
> 
amr@ubuntu:~$ ssh -L 5900:localhost:5900 [email]amr@71.XXX.XXX[/email].X
The authenticity of host '71.XXX.XXX.X (71.XXX.XXX.X)' can't be established.
RSA key fingerprint is [omitted].
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '71.XXX.XXX.X' (RSA) to the list of known hosts.
Password:
Last login: Tue Oct 16 16:21:59 2007
Welcome to Darwin!
XXXX:~ amr$[COLOR="Red"] channel 3: open failed: connect failed: Connection refuse[/COLOR]d

And in the terminal that I entered the xvncviewer command, I got this:

amr@ubuntu:~$ xvncviewer localhost:5900

> VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 16:58:22
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Tue Oct 16 16:32:16 2007
 CConn:       connected to host localhost port 5900

Tue Oct 16 16:32:17 2007
 main:        End of stream

Did I do something wrong?

On the G5, under System Preferences/Services, I checked "Remote Login", and under Firewall checked "Remote Login - SSH"   (I see an "Apple Remote Desktop" listed, but you didn't mention that, so...)

:confused:

[EDIT] I just tried a 2nd time and got this:

>  amr$ channel 247: open failed: administratively prohibited: open failed

And, just to clarify, the IP that I enter is the one that I'd get by going to whatismyip.com, right?!   (As opposed to the local router address...)

OK, the THIRD time I tried, I actually STARTED Vine Server on the Mac before trying to connect (D'oh!)...but I still got the same channel 247 error...

---

### Post by Dr Small on 2007-10-16
Looks like port 5900 needs to be opened :\

---

### Post by wilberfan on 2007-10-16
> **Dr Small said:**
> Looks like port 5900 needs to be opened :\

Oooh.   Opened where?   On the router, or....??

---

### Post by Dr Small on 2007-10-16
Both the router and the firewall on the system you are connecting to, need to have port 5900 opened. The router is not neccessary if you are on the same network, though.

Dr Small

---

### Post by wilberfan on 2007-10-16
> **Dr Small said:**
> Both the router and the firewall on the system you are connecting to, need to have port 5900 opened. The router is not neccessary if you are on the same network, though.l

Hmmm....  How DOES one open a specific port in OS X?

---

### Post by Dr Small on 2007-10-16
A Simple Google search returned this result:
[http://homepage.mac.com/car1son/static_port_fwd_firewall.html](http://homepage.mac.com/car1son/static_port_fwd_firewall.html)

Dr Small

---

### Post by NT4usB on 2007-10-16
Uh, don't forget the webcam so you can see if she's holding her mouse correctly. *g*
I'm putting together a Ubuntu system for my mom. They have an old Mac and she hates it. 
I'll be setting up some kind of connection so I can help her along, take care of updates, (and help my dad with his Mac.) 
Soon mom will have her own, private computer to play Hearts on. No more watching the beach ball 'wheel of death' go 'round and 'round for her!

---

### Post by wilberfan on 2007-10-16
Well...I got the OS X desktop to open (finally) on the Gutsy box :guitar:--but I had to put in the *internal* (ie, behind the router) IP.    That confuses me.     BOTH machines are behind the same router--maybe that's the reason?!

Plus, the Mac has a very wide screen display--and the Gutsy box has a 4:3 display, so I can't access the whole Mac screen--nor do I seem to be able to scroll over....    Does that mean I'd have to change the resolution of the Gutsy monitor, or....?

(You can tell I'm REALLY new at this!)  

Thanks for everyone's help so far!!

---

### Post by wormser on 2007-10-17
Cool, you got the VNC working and it sounds like you just need to tweak it to make it perfect.  If you are in the same network then it is best to use the local IP address.  When you try to connect across the internet you will have to use the routers IP.  You can use [Dyndns's]("http://www.dyndns.com/") free service to give the router's IP address a domain name.  It would be best to give the Mac a static IP address on the local network.  Then [port forward]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") port 22 on the router to the static IP address of the Mac.  This will just forward all request to port 22 on the router to port 22 on the Mac.

I am unsure about your display issues but I know you will have better performance if you change the desktop from millions of colors to thousands.  There will be a significant speed difference.  You might be better off asking the display issue to the Redstone [forum]("http://www.redstonesoftware.com/phpBB2/").  There might be changes you can make to the VNC server.  My guess is that you will have to start it by the command line with display options right after you ssh tunnel into the Mac.

Good luck and keep us up to date.

---

### Post by wilberfan on 2007-10-17
> **wormser said:**
> Cool, you got the VNC working and it sounds like you just need to tweak it to make it perfect.  If you are in the same network then it is best to use the local IP address.  When you try to connect across the internet you will have to use the routers IP.  You can use [Dyndns's]("http://www.dyndns.com/") free service to give the router's IP address a domain name.  It would be best to give the Mac a static IP address on the local network.  Then [port forward]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") port 22 on the router to the static IP address of the Mac.  This will just forward all request to port 22 on the router to port 22 on the Mac.

Cool.  Her router's (what I call, "external"?) IP is going to change, though, won't it?   I'm sure she has a "dynamic" IP (as I do).    It's been awhile since I've used Dyndns--that keeps track (somehow) of her variable IP, doesn't it..    That would prevent me having to ask her to check whether her IP has changed, huh?   And, yes, when I forward port 22 in her router, I will use the static IP of her machine.

> I am unsure about your display issues but I know you will have better performance if you change the desktop from millions of colors to thousands.  There will be a significant speed difference.  You might be better off asking the display issue to the Redstone [forum]("http://www.redstonesoftware.com/phpBB2/").  There might be changes you can make to the VNC server.  My guess is that you will have to start it by the command line with display options right after you ssh tunnel into the Mac.

Good idea regarding the number-of-colors issue--but were you referring to *her* desktop--or mine?  (Or both?)  I did notice it was laggy yesterday....

She lives half-an-hour away--it will probably be this weekend before I'm able to get over there--but I remembered today that Mom's Mac is only 5 minutes away--a good guinea pig methinks! (No router on Mom's machine, though...)

> Good luck and keep us up to date.

A gentleman and a scholar, you are, good Sir!  =D>

---

### Post by wormser on 2007-10-17
> **wilberfan said:**
> Cool.  Her router's (what I call, "external"?) IP is going to change, though, won't it?   I'm sure she has a "dynamic" IP (as I do).    It's been awhile since I've used Dyndns--that keeps track (somehow) of her variable IP, doesn't it..    That would prevent me having to ask her to check whether her IP has changed, huh?   And, yes, when I forward port 22 in her router, I will use the static IP of her machine.

Yes the external IP address is dynamic, but they never change.  If it does change then you can have her read it to you from [here]("http://www.whatismyip.com/") and update the Dyndns.  They have a client (not sure on a Mac) or in some routers that will automatically change to the new IP address.

> **wilberfan said:**
> Good idea regarding the number-of-colors issue--but were you referring to *her* desktop--or mine?  (Or both?)  I did notice it was laggy yesterday....

I was referring to her desktop.  If she is running Open Office under X11 (I recommend because it is good and free) then there is a setting you will have to change to get rid of the 3D glasses look.  If that is a problem let me know.

> **wilberfan said:**
> She lives half-an-hour away--it will probably be this weekend before I'm able to get over there--but I remembered today that Mom's Mac is only 5 minutes away--a good guinea pig methinks! (No router on Mom's machine, though...)

Get her a router!!!  Yes the Mac is pretty secure but it is better to be safe than sorry.  Plus you can always plug in another computer for internet access.

> **wilberfan said:**
> A gentleman and a scholar, you are, good Sir!

Obviously you have not talked to the police or my teachers! lol

---

### Post by NT4usB on 2007-10-17
> **wilberfan said:**
> ... It's been awhile since I've used Dyndns--that keeps track (somehow) of her variable IP, doesn't it..    That would prevent me having to ask her to check whether her IP has changed, huh?  ...

There was a ssh thread a while back, a guy wrote a skript that emailed him the new IP address whenever it changed... Sounds doable, just don't ask me how to do it. *g*

---

### Post by wilberfan on 2007-10-18
To answer my own question regarding "desktop scaling" (ie, a very large (or wide) screen on the server side vs a smaller screen on the viewer side, I found this in the "VineOSX" forums:

[http://www.redstonesoftware.com/phpBB2/viewtopic.php?t=775](http://www.redstonesoftware.com/phpBB2/viewtopic.php?t=775)

> Unlike UNIX based VNC servers Vine Server works by showing the existing display (rather than a newly created virtual desktop). As such the screen size is controlled by the Mac OS and there isn't currently a way to specify the size to display from Vine Server.

We have it on our feature request list to specify a "set to this size" when a user connects. That will message the OS to resize the screen, but keep in mind that it's the same screen that is connected to the monitor so existing windows will get pushed around, etc. Functionally it's not much better than setting the size yourself (from System Preferences) but when trying to connect to your BIG monitor from a low-band connection it can be nice for that to trigger without the delay of the initial screen.

Preliminary research suggests that scaling might be possible in Winblows XP [bleah] with "RealVNC (Enterprise)"?

---

### Post by wilberfan on 2007-10-20
You mentioned that port 22 needs to be opened on the Mac (server?) side.   But I'm confused about port 5900.    Does it need to be opened in the router(s)?   If so, on which machine?   One or the other--or both??

[Edit] Crap.  I asked this before, didn't I?   I'm still not clear on the concept, though...    Can anyone explain what's happening on port 22 and what's happening on port 5900?

[2nd Edit]  OK.  I think I got it now.    Port 22 seems to be for the ssh-whatever, and port 5900 is the one that the VNC-whatever goes through.   BOTH have to be forwarded on the machine that I'm connecting TO (the one running the VNC 'server').  

I got it working on my Mom's Mac...through a spanky new D-Link router (Wormser, you owe me $40!)  ;)    

Woo-hoo!

---

### Post by wilberfan on 2007-10-21
Well, things continue to go well with Mom's Mac--will be configuring my friends Mac tomorrow.   

What I'm wondering now:   What would a script look like to take care of the ssh and xvncviewer commands?  

:)

---

### Post by wilberfan on 2007-10-22
MAJOR SUCCESS!   :guitar:

After wrestling with some port-forwarding issues on my friends wireless router (still not sure what the problem was), I'm now able to remotely control her MacBook Pro--from Gutsy, Sidux, AND the Mac here at work ("Chicken of the VNC"!).

This is mega-way-awesome, and thanks go out to everyone who helped--most especially wormser!

=D>

---

### Post by wilberfan on 2007-10-26
As (another) followup, I just discovered that tsclient can be used as a front-end GUI for vncviewer?    I'd like to try it out (I know, the command-line is pretty simple!), but nothing I've tried has worked yet...

I put the following into a terminal

ssh -L 5900:localhost:5900 [email]carrot@vegetable.dyndns.org[/email]

then enter the password.

At this point I fire up tsclient, but I'm not sure what to put in the various windows (see screenshot).

Wouldn't carrot go into "User Name"?    And does "vegetable.dyndns.org" go into Domain??  But then I don't know what to put into "Client Hostname"...

:confused:

---

### Post by wormser on 2007-10-29
> **wilberfan said:**
> As (another) followup, I just discovered that tsclient can be used as a front-end GUI for vncviewer?    I'd like to try it out (I know, the command-line is pretty simple!), but nothing I've tried has worked yet...

I put the following into a terminal

ssh -L 5900:localhost:5900 [email]carrot@vegetable.dyndns.org[/email]

then enter the password.

At this point I fire up tsclient, but I'm not sure what to put in the various windows (see screenshot).

Wouldn't carrot go into "User Name"?    And does "vegetable.dyndns.org" go into Domain??  But then I don't know what to put into "Client Hostname"...

:confused:

Wormser to the rescue.. again! lol

Under computer use localhost:5900 and make sure Protocol is set to VNC. That should do the trick when connecting to the Vine VNC server on the Mac.  Try that first. It has been a while but I believe that is all you need to do.

---

### Post by wilberfan on 2007-10-29
> **wormser said:**
> Wormser to the rescue.. again! lol

Under computer use localhost:5900 and make sure Protocol is set to VNC. That should do the trick when connecting to the Vine VNC server on the Mac.  Try that first. It has been a while but I believe that is all you need to do.

"To the rescue...again", indeed!!   Yep, that did it.   :)

(And I sure do appreciate the help!   It's 12 kinds of awesome to be able to connect to her machine and walk her through stuff...!   (Tonight we learned how to use Audacity to trim a music file for a slideshow she's putting together!)

But I can't say that it saved me much *time...* (Very cool option, though.)   So, Mr. Smarty Pants--what would a SCRIPT look like that I could execute that would contain both the ssh command AND the vncviewer command?  Something I could just execute with one swell foop?

:guitar:

---

### Post by wormser on 2007-10-30
I am great not with scripting yet, but I believe this is what is needed.  First you should change your ssh session from password based authentication to [public key authentication]("https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30").  This will make you not need to use a password and is suppose to be more secure.  Check the Mac forums or HowTos on this.  Not needing a password will make the script easier.  I believe you just use both the commands together and just put && in between them.  I would put the command in a launch on your desktop.  Now you should just have to double click.

Another way to accomplish this is with 2 launchers.  Just right click on your desktop> create launcher.  Then put in the command for the tunnel.  Next create the launcher to open the VNC session.  If you are going to leave password authentication then this would be easier.  I recommend trying the first method.

---

### Post by Jugney on 2008-03-29
Hi all,

I followed wormser's instructions and they worked for me, all except the vnc connection command. Instead of typing localhost:5900, I actually had to type [ip address]:5900.

I also had the same issue with scaling, but when I connect with Krdc it has a button for scaling the screen so it fits perfectly.

My only problem now is that when I try to require SSH login from my OS X VNC server (Vine), I can no longer connect to VNC, even though I open the SSH connection first. Any ideas? 

Jugney

---

### Post by wormser on 2008-03-30
> **Jugney said:**
> Hi all,

I followed wormser's instructions and they worked for me, all except the vnc connection command. Instead of typing localhost:5900, I actually had to type [ip address]:5900.

I also had the same issue with scaling, but when I connect with Krdc it has a button for scaling the screen so it fits perfectly.

My only problem now is that when I try to require SSH login from my OS X VNC server (Vine), I can no longer connect to VNC, even though I open the SSH connection first. Any ideas? 

Jugney

Something is wrong if you have to use your [ip address]:5900.  The tunnel is not working and you are connecting directly with VNC.  Do you have a router?  Port 5900 should not be exposed to the internet.  It sounds like you can ssh in, but the port binding is not working.  Please post some more details.

---

### Post by Jugney on 2008-03-30
You are right. I noticed that I could log in whether an ssh connection was there or not. But the only reason I tried anything else is that, as I said, once the ssh connection is open, it won't work when I go 

```
xvncviewer localhost:5901
```

It's port 5901 because the Mac is set up with Vine VNC server (OSXVNC) and that automatically set it to port 5901. I have opened ports 5901 and 22 on the Mac, both in the system firewall and the router (we are not behind the same router), and set up port forwarding to the correct private IP of the Mac.

Also, I set up a domain with dyndns.org to avoid issues with the external IP changing, and also told the Mac to make its private IP static. It is running Tiger. 

I don't know what else to do?

Jugney

---

### Post by wormser on 2008-03-31
Block the VNC port on the router.  We only want the ssh port open to the internet.  The best thing in trouble shooting is to remove variables.  It sounds like you are able to connect with ssh and VNC separately.  From what you are telling me it sounds like the port binding is not working.  Can you post the command you are using?  This is what it should look like.

```
ssh -L 5901:localhost:5901 user@yourdomain.com
```

---

### Post by Jugney on 2008-03-31
Alright, I blocked forwarding on port 5901 on the Mac's router. 

This is how I've been doing it: I enter the following command to open up the ssh connection:
```

ssh -L 5901:localhost:5901 "username:@****.dyndns.org"
```

It prompts for a password, I enter the user account password, and then I get the Darwin welcome screen.

When I open a second terminal window, I enter the following:
```

xvncviewer localhost:5901
```

and get:

xvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

Perhaps I need to configure VNC on the Mac differently. Right now, I just have a VINE server running (on port 5901). 

Should I type anything different than "localhost" or is that what I actually type?

---

### Post by Jugney on 2008-03-31
Update!

xvncviewer still doesn't work, but I just tried from Krdc (my FAVORITE VNC program!) and it worked! I typed in 

localhost:5901

as the remote desktop and it worked immediately! Huzzah!

The only question now is...is there any way to make it run faster...? I set it to medium quality (colors look messed up in low quality), low color (8 bit) and the lowest desktop resolution. I'm also on a DSL connection which is about 500K. Is there anything I can do to make it go faster than the slow rate it does now??

---

### Post by wormser on 2008-03-31
> **Jugney said:**
> Update!

xvncviewer still doesn't work, but I just tried from Krdc (my FAVORITE VNC program!) and it worked! I typed in 

localhost:5901

as the remote desktop and it worked immediately! Huzzah!

The only question now is...is there any way to make it run faster...? I set it to medium quality (colors look messed up in low quality), low color (8 bit) and the lowest desktop resolution. I'm also on a DSL connection which is about 500K. Is there anything I can do to make it go faster than the slow rate it does now??

You can change your Mac to a lower color quality.  That made a big difference for me.  Also, add the switch -C to the command for compression.

---

### Post by wormser on 2008-04-01
> **Jugney said:**
> xvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

I tried it with Leopard and got the same error with xvncviewer.  It must be a bug because it works fine with Krdc.

---

