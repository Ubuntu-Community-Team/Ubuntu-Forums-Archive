---
title: "X session vs vnv"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by frafu on 2006-07-28
Hello, 

I have read different threads about remote desktop with GUI; some people do it with vnc, others talk about an X session... Further, there is also the problem about connecting to an already existing session or opening a new session... 

Could you please tell me the difference of both methods: I am not talking about how to configure it, but about what it is possible to do with them. 

Maybe, if I knew exactly what an X session is would also help... 

Thanks in advance for any explanation. 

frafu

---

### Post by Paerez on 2006-07-28
"X Session" is most likely X forwarding (over ssh). This means that you make an ssh connection, then the gui of the application is displayed on the local X server.

What people usually do with this is run the Xnest program, which will run a windowed X Server (ie gnome or kde) on the local machine.

VNC runs everything on the remote computer, then takes screen captures and compresses them and sends them to the local computer.

So the difference is the sending of the visual data. I *think* vnc is faster, but I am not sure.

Another thing is that vnc will send the entire screen to the local computer, while X forwarding can be used to just send one application (like you could open Gaim remotely without having to start a full session).

---

### Post by frafu on 2006-07-29
@Paerez

Thanks for your explanation. 


@Paerez and all

So, if I understand it correctly, X forwarding and vnc both need a running gui on the remote computer; it will not work on a computer that boots into the cli. 


When using X forwarding, do the local and the remote computer have to run the same window manager? Otherwise, how can the local computer paint the gui of an appplication on his monitor if it does not have the same buttons, popups,...? (I suppose this is not a problem with vnc, as it transmits "screenshots" of the remote computer.) 


By the way, I don't know yet what to understand exactly by the term window manager: Only the routines to handle the windows? What about the desktop? What about the buttons, popup and the other elements used in the gui? What about the graphical login window? What other components are needed to have a complete gui?

---

### Post by jimmygoon on 2006-07-29
> **frafu said:**
> @Paerez

Thanks for your explanation. 


@Paerez and all

So, if I understand it correctly, X forwarding and vnc both need a running gui on the remote computer; it will not work on a computer that boots into the cli. 


When using X forwarding, do the local and the remote computer have to run the same window manager? Otherwise, how can the local computer paint the gui of an appplication on his monitor if it does not have the same buttons, popups,...? (I suppose this is not a problem with vnc, as it transmits "screenshots" of the remote computer.) 


By the way, I don't know yet what to understand exactly by the term window manager: Only the routines to handle the windows? What about the desktop? What about the buttons, popup and the other elements used in the gui? What about the graphical login window? What other components are needed to have a complete gui?

I believe that if you have gaim installed but you are not in a gui that if I tunnel X that gaim will open on my screen still since its running through my graphical server... I'm probably wrong though

---

### Post by Paerez on 2006-07-29
you do not need to be running a gui on the remote machine. Mine boots straight to cli. You do need to have a gui installed in order to use it though.

It's great because it uses like 40m ram when it boots because there is no gui, then when you need the gui you start the xsession/vnc and then you have it.

---

### Post by frafu on 2006-07-30
> **Paerez said:**
> you do not need to be running a gui on the remote machine. Mine boots straight to cli. You do need to have a gui installed in order to use it though.

It's great because it uses like 40m ram when it boots because there is no gui, then when you need the gui you start the xsession/vnc and then you have it.

Do you mean that after booting into the cli, the fact of starting an Xsession/vnc will automatically start the gui? Or will I have to start the gui manually before starting the Xsession/vnc?

---

### Post by Paerez on 2006-07-30
There is a key concept of linux that I think you don't understand, and once you get it, everything will all fall into place (I don't mean to sound condescending and I'm sorry if it comes across this way).

Once the kernel is loaded, everything else that runs is just an application. Unlike windows, the gui is not part of "linux". The gui is an application, like gnome or kde, that is run on top of the kernel. Gnome is just like firefox or gedit or nano or bittorrent, it is just an application.

In reality, everyone's ubuntu is booting to the cli. A series of startup programs are run (like power management and automatic disk mounting). One of these startup programs is the gui. So, when you have a computer that just boots to CLI, that means either the gui is not set to start automatically, or it is not installed.

So, when you boot your machine, it just boots to the cli, and gnome is told not to start. When you run an xsession, gnome is run just for that xsession, for a remote display. Normally, gnome is run on a local display. In fact if you want, you can have one gnome running on a local display, and multiple gnomes running on multiple displays, because they are just applications.

This is analogous to opening multiple terminals and running multiple nanos, they are just applications.

When you run vnc, gnome is run on a local display that is not sent to a monitor, it is just captured via compresses images and sent to a remote computer, and mouse and keyboard events are sent back.

So yes, you are right when you say:
[quote]the fact of starting an Xsession/vnc will automatically start the gui[/code]
except is it more accurate to say "the fact of starting an Xsession/vnc will automatically start **a** gui." Since there is no "the" gui. Much like there is no "the" firefox, you just run "a" firefox instance.

I hope that was clear, this is one of the reasons I think linux is great, because everything is so modular.

---

### Post by frafu on 2006-08-01
Hello Paerez,

> 
There is a key concept of linux that I think you don't understand, and once you get it, everything will all fall into place (I don't mean to sound condescending and I'm sorry if it comes across this way).


Don't worry about that; in fact I am happy that you took the time to explain about the ideas behind ubuntu/linux. :cool: 


> 
In reality, everyone's ubuntu is booting to the cli. A series of startup programs are run. One of these startup programs is the gui.


OK; so the graphical desktop is an application that is automatically started after the computer has booted to the cli. I have no problem to understand that. :) 


>  
When you run an xsession, gnome is run just for that xsession, for a remote display. Normally, gnome is run on a local display. In fact if you want, you can have one gnome running on a local display, and multiple gnomes running on multiple displays, because they are just applications.
 

If I get it right: each display gets its own instance of gnome (or of any other gui). In other words, if I have 2 displays and I type 'top' in xterm, I can see 2 different gnome-processes!? 





In about a week, I will probably get the box where I am going to install ubuntu. The main purpose of the box will be to act as an headless nfs-server. But I would also like to use the box to experiment with ubuntu. According to the information I have got up to now, I will probably proceed like this and also in this order: 


1. Connect the box with ethernet to my router running a dhcp server; connect a monitor, keyboard and mouse. 

2. Install the desktop version of ubuntu on the box. (I think it will be easier for a newbie to start with the desktop version than starting with the server version.) 

3. Configure the ssh-server to let me in remotely from my MacOSX+AppleX11; and afterwards start the ssh-server.  
[https://help.ubuntu.com/community/AdvancedOpenSSH#head-7e9a25fd60ac8821009dc585dad819361b352527](https://help.ubuntu.com/community/AdvancedOpenSSH#head-7e9a25fd60ac8821009dc585dad819361b352527)

4. Change runlevel of the box to make it boot into cli. (There is no need to make it run a desktop and use resources when it is only acting as nfs-server). 

5. Reboot the box and test whether the remote ssh-connection works; if it works, remove the display, the keyboard and the mouse from the box and use it headless. 


Now I wonder whether: 
- changing runlevel will not destroy the ssh configuration 
- point 3. will provide for the remote Xsessions (it should as far as I could learn up to now) 
- when I want to use vnc, I log (by using ssh) from MacOSX into the ubuntubox (where sshd is running), start a vnc-client on the remote ubuntubox, and then start a vnc-viewer (probably chicken of the vnc) on my MacOSX. 


If anyone thinks of anything that is not correct or that is missing or that could be done in a better way, please don't hesitate to tell me so. It will be greatly appreciated. 


Have a nice day. 


frafu

---

### Post by Paerez on 2006-08-01
> 
Now I wonder whether:
- changing runlevel will not destroy the ssh configuration
- point 3. will provide for the remote Xsessions (it should as far as I could learn up to now)
- when I want to use vnc, I log (by using ssh) from MacOSX into the ubuntubox (where sshd is running), start a vnc-client on the remote ubuntubox, and then start a vnc-viewer (probably chicken of the vnc) on my MacOSX.

I don't know how to change ubuntu's runlevel :( but hopefully you are right that ssh will stay.

Everything else is perfect! You nailed it. The only thing is that vnc's server is called "vncserver" not "vnc-client" and the viewer is "vncviewer"

You described my exact process when I set up a gentoo server, same method. You definitely have a clear grasp of everything you need to do, so ... Good luck!

---

### Post by frafu on 2006-08-01
@Paerez

Thanks for confirming that the theoretical part of what I am trying to do is ok, and especially thanks for the good wishes. :D 


Maybe you are interested to know where I learned about runlevels; here is the [thread]("http://ubuntuforums.org/showthread.php?t=207693&highlight=runlevel+cli") .


Concerning the terms client and server: Until recently, it was clear for me: the server runs on the remote computer and the client runs on the local computer. 

But then I found [this article]("http://en.wikipedia.org/wiki/X_Window") saying that in the X window system the meaning of the terms is reversed. (third paragraph, third line) 

Further, in [this doc]("https://help.ubuntu.com/community/VNCOverSSH") about vnc over ssh, the terms are also reversed (have a look at the links on the right). Consequently, to avoid misunderstandings, I often try to add the terms "on the remote computer" and "on the local computer" to my sentences. :cool: 


Have a nice day. 

frafu

---

### Post by Paerez on 2006-08-01
I see that the terms are reversed for the X server/client relationship, but in VNC it is as I said.

The problem is that "remote" changes based on which computer you are sitting at. If you are sitting at the server, the remote computer is the client. If you are sitting at the client, the remote computer is the server.

The host computer, whose screen is the main screen that will be viewed by someone else, runs the vncserver application.

The client computer, who will be accessing the server and performing tasks on the server, will be running the vncviewer application.

Here is an example:

On my computer at work (hereby referred to as the host and local computer) I run a normal display on :0 for me to code in. Sometimes, I need my boss to help me, so I run:
vncserver :1
to start a new display on my computer, running on display :1.
Now, because I want to work with him, I type:
vncviewer localhost:1
So that I can access my display :1 inside a window in my display :0 (see screenshot).

Then, he connects to me by typing:
vncviewer hostname:1

Now we both have our own displays running on our own :0s, and we are both connected to my :1, where we work together. It's very sweet.

---

### Post by frafu on 2006-08-01
>  
The problem is that "remote" changes based on which computer you are sitting at. If you are sitting at the server, the remote computer is the client. If you are sitting at the client, the remote computer is the server.
 
Oh, everything is relative not only in physics, but also in informatics. ;) 


More seriously, 
>  
The host computer, whose screen is the main screen that will be viewed by someone else, runs the vncserver application.

The client computer, who will be accessing the server and performing tasks on the server, will be running the vncviewer application.
 

So with vnc, the terms are used as usual. And your example was really good: your boss and you are both looking at the same thing, he remotely, you localy, you are both doing it with a vnc-client, and you launched a vnc-server to make it possible. Have you ever thought of becoming a teacher? ;) 


I will go to bed now; it is getting relatively ;) late here. (23:40 PM) 


Thanks 

frafu

---

### Post by Paerez on 2006-08-01
The example was good because I actually do that often and that was a real screenshot (without boss) :D

And yes, one of my dream jobs involves being a computer science teacher by day and an open-source hacker by night. Now all I need is a costume.

---

### Post by teh_chris on 2006-08-04
i don't really have anything to contribute, but i have some really old screenshots of vnc sessions that i thought i would share.  these are old versions of redhat and mandrake (6.2/7.3 i believe... long before fedora), from the 90's.  i'm kind of showing my age here :-)

there are two vnc shots of gnome and kde WM's running off the same host (musahshi).

the redhat and mandrake screen shots include VNC sessions on windows desktops and citrix metaframe sessions to old windows hydra machines.  that's the first version of terminal server for windows NT 4.0, now that's old school :-)

anyway, they demonstrate that you can use VNC to remote pretty much anything.

---

### Post by frafu on 2006-08-04
@teh_chris

Thanks for your screenshots giving some examples of vnc sessions. 

I hope that by end of next week I will be running my own remote X or vnc session. :cool:  

frafu

---

### Post by Paerez on 2006-08-04
it's so old school! I love it!

This weekend I am going to use VMWare to install ubuntu-server within ubuntu to play around with apache, vnc, etc. I'll let you know if I discover anything interesting.

---

### Post by frafu on 2006-08-04
@Paerez

In [this thread]("http://ubuntuforums.org/showthread.php?p=1338289#post1338289"), someone (his nick is Perkins) explains that the vnc-server shipped with ubuntu might be a special purpose server that can only connect to a screen that is already running; and that one should install another vncserver. 

Further, he explains how to set up the vnc-server; but you surely know that already.

---

### Post by Paerez on 2006-08-04
I plan to use tightvnc, which is what I currently use on my gentoo server. I am hoping to switch my gentoo server over to ubuntu, but I am gonna test drive it first. So don't worry, I know what I am doing. Thanks for the info on ubuntu-server though, I could definitely confuse people if I didn't know about it.

---

