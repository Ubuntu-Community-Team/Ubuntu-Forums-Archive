---
title: "HOW TO : Remote Desktop to windows xp"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by orangedangila on 2006-12-30
i am wondering if i can remote desktop my windows xp via ubuntu...
what program should i use and how to configure and use it??

---

### Post by PriceChild on 2006-12-30
*thread moved and approved*

---

### Post by The Joe on 2006-12-30
If you mean what I think you do you need VMWare however I think it costs. [http://www.vmware.com](http://www.vmware.com), unfortunately I don't think there is an alternative.

---

### Post by jonathan.lees on 2006-12-30
Or do you mean you want to remotely manage XP from Ubuntu, if so you need to enable remote desktop on XP and on Ubuntu install and run rdesktop.

---

### Post by orangedangila on 2006-12-30
how to enable remote desktop on windows xp??
do i need to install or download specific program??

---

### Post by PriceChild on 2006-12-30
Remote desktop is viewing the windows desktop on the ubuntu machine.

---

### Post by Crakie on 2006-12-30
EDIT: I misread the original post... my 2 cents below is for logging into Linux from XP. Deleting it now seems a waste though, but you might want to continue reading in the next post ;)

What you need is a VNC server. Both Ubuntu and Kubuntu have one installed by default, meaning that - if enabled - you can access your (K)ubuntu box with a VNC client (be it on Windows or another operating system). In Ubuntu it's called remote desktop, in Kubuntu Krfb desktop sharing. You'll find them in your menus. There's not much to it, but a simple google will get you simple step-by-steps. 

Something to keep in mind: if you are behind a router, you'll need to forward the port for VNC to work. The standard is 5900. Look in the router's manual on how to do that.

Another thing: VNC is not secure. It is much better to tunnel it through a SSH connection. [This]("http://www.rhymingpanda.com/weblog/2006/06/23/15_32_13/index.html") will get you started on how to do that.

---

### Post by jonathan.lees on 2006-12-30
You can enable Remote Desktop in XP by right clicking My Computer > Properties and select the Remote tab. Now you can enable Remote Desktop which will allow you to remotely manage XP providing you know the administrator password or you add a normal account to it.
In Ubuntu you need to install the Remote Desktop client rdesktop. You can either install from Synaptic or apt-get, with the latter running sudo apt-get install rdesktop from a terminal.

Once installed, to run rdesktop in ubuntu, open a terminal and type:

rdesktop (IP address of XP box), e.g rdesktop 192.168.1.1

If you want, you can tweak the rdesktop settings to improve resolution etc, if you type rdesktop a list of options will be shown to you. 

I hope this helps.

---

### Post by xpod on 2006-12-30
vnc servers great.........it`s certainly saved me one or two visits to the mother in laws recently:D 
She cant\wont do the simplest of things to keep her xp running reasonably so this is great stuff....

Unfortunately the other more secure methods are still quite a bit over my head at the moment so vlc it has to be.....for now.

---

### Post by orangedangila on 2006-12-30
thanks for the help... i got it works... thanks...

---

### Post by venik212 on 2007-02-08
To log on irc.freenode.org one needs more patience and time than most of us have.  I have tried repeatedly to log on, and most of the time I fail.

---

### Post by PriceChild on 2007-02-09
> **venik212 said:**
> To log on irc.freenode.org one needs more patience and time than most of us have.  I have tried repeatedly to log on, and most of the time I fail.irc.freenode.net

---

### Post by venik212 on 2007-02-09
Crakie wrote above: [I]"Both Ubuntu and Kubuntu have one installed by default, meaning that - if enabled - you can access your (K)ubuntu box with a VNC client (be it on Windows or another operating system). In Ubuntu it's called remote desktop, in Kubuntu Krfb desktop sharing."
[/I]

As far as I can tell, the Krfb in Kubuntu is a RemooteDesktop CLIENT, not a server.  I am desparately looking for the Kubuntu server which will enable me to log on the kubuntu machine from a remote computer, but have not found it.  I like the look and feel of KDE, but without such a server I might have to crawl back to Gnome, leaving Kile behind...
Any help will be greatly appreciated.

---

### Post by PriceChild on 2007-02-09
The server is the same in both Ubuntu and Kubuntu.

---

### Post by kazuya on 2007-02-09
I am trying to assist my mom in another city, she has XP on the laptop. I do not think she logs in with a password. What is the default password in the event that user never set one up to begin with as the XP OS came with the laptop. It is a HP one I believe.

---

### Post by venik212 on 2007-02-09
I was unable to find VINO (the VNC server under gnome) anywhere, and am now hunting for krfb, which I had installed, but don't know where the clever gnomes of KDE have hidden-- it is nowhere in the various menus!

---

### Post by RichTJ99 on 2007-11-07
What is the terminal command to install Remote desktop on 7.10?  I am looking to log into XP from my Ubuntu desktop/workstation

---

