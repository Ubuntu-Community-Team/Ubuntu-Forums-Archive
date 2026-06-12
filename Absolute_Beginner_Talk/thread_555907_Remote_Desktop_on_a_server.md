---
title: "Remote Desktop on a server"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by drhiii on 2007-09-20
A Noob here.

Here is the scenario.  I have a windows application that I need to run in wine.  It imports data into a a sql data base (trust me, this is temporary to get to a proof of concept before the application will be rewritten to run native *nix).  It needs to be run from a desktop, Xwindows, beacuse the application is invoked from remote.  

Question is, what would you recommend to run a secure connection (ssh?) into a server that can run a remote desktop or similar method, that would allow interaction with a Wine application that requires a GUI to use it?

Secondarily, can one run Xwindows via SSH without actually running the desktop ona server?  Seems that I have read one can run a remote desktop via SSH, without having to have the server running X in runlevel 3 is it?  Am I getting this right?

I've been reviewing a lot of info here, but thought to just ask the question straight up.

tx.  This is a fantastic community...

---

### Post by Kilz on 2007-09-20
I would recommend posting this question in another section of the forum. Maybe the [server and security section]("http://ubuntuforums.org/forumdisplay.php?f=7") would be a good place. You are aware that a server install does not by default install a desktop, right?

---

### Post by HermanAB on 2007-09-20
Install OpenSSH on the machine. 

Connect to it using ssh:
ssh -X user@server
password
$ gedit

La voila!

H.

---

### Post by drhiii on 2007-09-21
Holy cow.  That's it?  I assume X has to be installed on the server even though it is not invoked to run at boot?

tx a mil. This sounds very cool, to a noob learning it.

---

### Post by bodhi.zazen on 2007-09-21
> **drhiii said:**
> Holy cow.  That's it?  I assume X has to be installed on the server even though it is not invoked to run at boot?

tx a mil. This sounds very cool, to a noob learning it.

Well, I think there will be more to it then that as if I am reading your OP correctly you are connecting windows and linux.

Which OS is host and which is the client ? Do you want to forward a single application or an entire desktop ?

If windows is the client, take a look at putty (for your ssh connection) and cygwin (for a X server on windows).

If windows is the server you will need to install a ssh server on windows ... again cygwin. But I am not sure you can the forward windows applications to a linux client via ssh -X ...

You *might* want to look at VNC or RDP. You can use the RDP protocol to forward a single application, like this :

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by drhiii on 2007-09-21
The Server is Linux/Ubuntu.  I really only need to forward a single application, running in Linux, but is a WIndows application so will have to use at the least, Wine if the proggie runs under it that way.   SSH is already running on the server and works fine.  I will look at VNC and RDP.  If there is a way to simply run the application without having to bring up the full Xwindows on the Ubuntu server, that would be a huge relief.  Why use all those resources on a server for a single app??  But I am learning how all this can piece together anyway so my understanding curve is advancing....

Thank you for this detailed response...





> **bodhi.zazen said:**
> Well, I think there will be more to it then that as if I am reading your OP correctly you are connecting windows and linux.

Which OS is host and which is the client ? Do you want to forward a single application or an entire desktop ?

If windows is the client, take a look at putty (for your ssh connection) and cygwin (for a X server on windows).

If windows is the server you will need to install a ssh server on windows ... again cygwin. But I am not sure you can the forward windows applications to a linux client via ssh -X ...

You *might* want to look at VNC or RDP. You can use the RDP protocol to forward a single application, like this :

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by bodhi.zazen on 2007-09-21
Well, ssh -X is the way to go for a single application.

You will likely have to tweak the wine settings a little.

The reason I suggest VNC is, IMO at least, it is faster, desktop and all, then ssh a single application.

Let us know if you need help.

---

### Post by drhiii on 2007-09-21
This is great.  I really appreciate the "community" spirit that is put forward here.  The "let us know if you need help" means a great deal.  

I must RTFM before expecting other people to answer researchable questions, which I do, but will stick my neck out and ask... so it will help me to figure out what materials to study.  

Will repeat back what I think I understand... the recommendation is to use ssh -X if one is invoking a single application.  But, am I correct in assuming that VNC requires Xwindows to be running on the "server" side, meaning a full desktop must be running in order for VNC to work?

If I got that right, I will drill down into the tasks and learn how to do it, then share the knowledge with others.  


Interestingly yesterday, was in a conversation with someone who was handed a running Ubuntu client.  Everyone around him, including himself, says that they need to go back to Windows because nothing works.  I got into the usual discussion that often falls on deaf ears, that yes, one could throw in the towel and revert back to Windows, and all those problems that come with it, like virii, the endless breakages and blue screens of agony, not to mention his particular machine was under powered and Win2000 may run on it, slowly, but fahgetaboutit with anything later.  I said, sure... but Ubuntu has breathed fantastic life into your older machine, it is running fine, it is just a matter of relaxing, having an open mind, and learning new things that are really not so new since everything he needs to do is familiar if you just calm down and let it come to you. > Insert rant from everyone standing around me saying how things don't work, too hard, blah blah blah.  < So in my limited knowledge I proceeded to "do" each one of the things they said was too hard in one or two keystrokes.  Not so hard.  But my final comment was that what they really were missing was the superb sense of community that awaited them if they just slowed down, took a breath, opened their brains, and let the Ubuntu community help.  

So, pardon the spin up, but after a wheels off yesterday with a lot of whiney, pissy, freaky, let-someone-else-do-it-for-me people in my domain, I appreciate the simple phrase... let us know if you need help.   Music to me ears.



> **bodhi.zazen said:**
> Well, ssh -X is the way to go for a single application.

You will likely have to tweak the wine settings a little.

The reason I suggest VNC is, IMO at least, it is faster, desktop and all, then ssh a single application.

Let us know if you need help.

---

### Post by bodhi.zazen on 2007-09-21
There are several vnc servers available. The Ubuntu default is "vino" and vino requires one to be running X on the server (as does X11vnc).

But tightvnc does NOT require you run X on the server.

[uwiki]VNCOverSSH[/uwiki]

On the client side, the vnc viewer gives you X on the client, thus if you are on a windows clinet, no need for cygwin.

You might also want to look at this page :

[uwiki]SSHHowto[/uwiki]

---

