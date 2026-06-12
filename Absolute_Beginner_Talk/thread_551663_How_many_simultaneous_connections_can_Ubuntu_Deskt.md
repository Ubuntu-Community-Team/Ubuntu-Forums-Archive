---
title: "How many simultaneous connections can Ubuntu Desktop have?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-09-15
How many simultaneous connections can Ubuntu have?

Specifically, in Windows XP Home the limit is 5, and XP professional its 10.

Also, if the number of simultaneous connections in Ubuntu desktop is high, why couldn't the desktop version be used as a server?  Why is there a Server version anyway?


Carl

---

### Post by jackocleebrown on 2007-09-15
There is not much difference between the server and desktop distros of Ubuntu - it is just a question of setup and the default installed software. You could "convert" one into the other with the right packages added and removed in synaptic.
I guess the reason for having different install disks is just for convenience - the "wizard" that guides you through the desktop install is less complicated than the server version & geared towards setting up a desktop with the right language, working display, a number of users etc....The server version has different options to automatically configure things like LAMP servers and leaves out software that is not normally used on a server (such as GNOME, OpenOffice etc...)

I believe the limit on users is simply hardware resources - there are no rules ;)

Jack.

---

### Post by julian67 on 2007-09-15
> **cwmoser said:**
> How many simultaneous connections can Ubuntu have?

Specifically, in Windows XP Home the limit is 5, and XP professional its 10.

Also, if the number of simultaneous connections in Ubuntu desktop is high, why couldn't the desktop version be used as a server?  Why is there a Server version anyway?


Carl

In Win XP SP2 and newer there is not a limit on simultaneous connections. It is a limit on simultaneous incomplete outbound TCP connection attempts. Microsoft explain it like this > Limited number of simultaneous incomplete outbound TCP connection attempts

Detailed description

The TCP/IP stack now limits the number of simultaneous incomplete outbound TCP connection attempts. After the limit has been reached, subsequent connection attempts are put in a queue and will be resolved at a fixed rate. Under normal operation, when applications are connecting to available hosts at valid IP addresses, no connection rate-limiting will occur. When it does occur, a new event, with ID 4226, appears in the system’s event log.

Why is this change important? What threats does it help mitigate?

This change helps to limit the speed at which malicious programs, such as viruses and worms, spread to uninfected computers. Malicious programs often attempt to reach uninfected computers by opening simultaneous connections to random IP addresses. Most of these random addresses result in a failed connection, so a burst of such activity on a computer is a signal that it may have been infected by a malicious program.

What works differently?

This change may cause certain security tools, such as port scanners, to run more slowly.

How do I resolve these issues?

Stop the application that is responsible for the failing connection attempts.

source [http://technet.microsoft.com/en-us/library/bb457156.aspx#EHAA](http://technet.microsoft.com/en-us/library/bb457156.aspx#EHAA)

As you can see it's basically a workaround for the fact that most Windows machines are extremely vulnerable to worms. I'm not aware of any such limit in Linux distributions, though there may be a very high one.

Yes you can use your desktop as a server but you should do some research. While you can install X-server and desktop on server and you can run server apps on the desktop editions it's worth noting that Ubuntu server and desktop editions ship with different kernels, so there is some difference already and I believe that when Gutsy ships the server editions will have apparmor. Servers and desktops handle different loads so the different kernels are optimised with this in mind.

---

### Post by jaybombalous on 2007-10-20
Yes, its TCP connections. Also, it was in the original XP and SP1 packages but was removed in SP2 because of all the complaining. There was a hack made available for XP so that u could open XP up even with the default limit. This is what stopped a lot of the torrent and multiple user d/l software to run horribly slow. U where only allowed to have 5 - 10 people connect at one time and half the time even when someone was connected they where never sending u data.

The only limit u have now is the software itself, after a while u will run out of memory holding open TCP connections and the machine will crash.

---

### Post by julian67 on 2007-10-20
> **jaybombalous said:**
> Yes, its TCP connections. Also, it was in the original XP and SP1 packages but was removed in SP2 because of all the complaining. There was a hack made available for XP so that u could open XP up even with the default limit. This is what stopped a lot of the torrent and multiple user d/l software to run horribly slow. U where only allowed to have 5 - 10 people connect at one time and half the time even when someone was connected they where never sending u data.

The only limit u have now is the software itself, after a while u will run out of memory holding open TCP connections and the machine will crash.

No it isn't a limit on TCP connections. See the outline above straight from the horse's mouth, Microsoft. What was limited was "simultaneous incomplete outbound TCP connection attempts" and what this does to a p2p app is cap the ability to find other peers. P2P apps were not restricted to only 5 or 10 connections.  What it could do to the system as a whole is give you a BSOD with an event 4226 showing in your system log every time your PC breached the limit (we had to destroy the village in order to save it/the operation was a complete success but the patient died).  This wasn't present in XP or XP SP1 and in fact *was* introduced with SP2.

Apart from that all your facts are correct ;-)

---

### Post by jaybombalous on 2007-10-20
I don't listen to the horses mouth as much as they like to speak...


I don't think it was limited to incomplete connections, at least not in my experience. I trust what I see more then I trust what I read.

---

### Post by Frak on 2007-10-20
As for the TCP question, I cannot answer, but for the Server, most webmasters would like to conserve resources for Server Operations, not Compiz-Fusion or Gnome.

---

### Post by julian67 on 2007-10-20
> **jaybombalous said:**
> I don't listen to the horses mouth as much as they like to speak...


I don't think it was limited to incomplete connections, at least not in my experience. I trust what I see more then I trust what I read.

Then look at the system logs, seeing and reading combined ....could be tricky which way to go on this one   ;-) 
If you still have XP SP2 it's easy enought o see for yourself that there is not this tiny limit on open connections. Open 20 different webpages each in a different tab or browser. Initiate 30 different ftp connections and so on. 

@Frak: It's rather hard to see that compiz-fusion or gnome has anything at all to do with limiting outbound tcp connection attempts. When MS did this it wasn't to conserve resources but as a security measure.....or more of a "we failed" security measure,  to prevent malicious code that had already arrived on a PC from making hundreds or thousands of simultaneous outbound connection attempts.

---

### Post by Frak on 2007-10-20
> **julian67 said:**
> Then look at the system logs, seeing and reading combined ....could be tricky which way to go on this one   ;-) 
If you still have XP SP2 it's easy enought o see for yourself that there is not this tiny limit on open connections. Open 20 different webpages each in a different tab or browser. Initiate 30 different ftp connections and so on. 

@Frak: It's rather hard to see that compiz-fusion or gnome has anything at all to do with limiting outbound tcp connection attempts. When MS did this it wasn't to conserve resources but as a security measure.....or more of a "we failed" security measure,  to prevent malicious code that had already arrived on a PC from making hundreds or thousands of simultaneous outbound connection attempts.
He also asked why they release a server version instead of just sticking with one Desktop version, so I answered it.

---

### Post by julian67 on 2007-10-21
> **Frak said:**
> He also asked why they release a server version instead of just sticking with one Desktop version, so I answered it.

you're right, excuse me.

---

### Post by Big_MARK on 2008-04-18
So to clarify for us Non-Geeks Ubuntu users, can I use Ubuntu Desktop edition to serv up files to my small network of 15-20 PCs?  I like the GUI so that's really the only advantage I see in using Destop over Server editions FOR THE NEWB (like me) Or does the server edition allow for  GUI upon installation?

---

### Post by IcemanV9 on 2008-04-18
Quick answer(s) ...
Desktop edition - is it possible to set up a file server for the network of 15+ PCs?: [COLOR="RoyalBlue"]Yes, you can[/COLOR]
Server edition - can I install "GUI"?: [COLOR="RoyalBlue"]Yes, you can[/COLOR]
```
sudo aptitude install xserver-xorg
```

---

### Post by Big_MARK on 2008-04-18
Does the GUI install with the Server install CD, or is it something that has to be done after the fact?

---

### Post by Frak on 2008-04-18
> **Big_MARK said:**
> Does the GUI install with the Server install CD, or is it something that has to be done after the fact?
After

If you want gnome-desktop, and not have to install everything and configure with hassle, use:

```
sudo aptitude install ubuntu-desktop
```

If you want a KDE desktop, use:

```
sudo aptitude install kubuntu-desktop
```

XFCE

```
sudo aptitude install xubuntu-desktop
```

Fully open source desktop (gnome)

```
sudo aptitude install gobuntu-desktop
``` (not sure if gobuntu-desktop works just yet)

---

