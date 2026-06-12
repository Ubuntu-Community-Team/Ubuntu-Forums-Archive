---
title: "remote desktop setup"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by boogersmcgee on 2007-03-26
I am very new to linux/unix. I was recently given a computer that has ubuntu installed on it. The issue here is, I have no peripherals. I have no mouse keyboard or screen.  What I do have is a powerbook G4 and a router. Is there any way for me to log into the other computer through the router using the mac. I have both the root pw and the computer IP. 


Once logged in I would like to set up a remote desktop program so that I can login easier and into the gui through the mac. I have been told that this should be possible and be pretty easy however I am unable to find any straight forward guides on how to do such a thing.

Any suggestions would be appreciated.

Thanks in advance.

---

### Post by halitech on 2007-03-26
if the system hasn't already been set up for remote connections then no, you will need a mouse, keyboard and monitor to get things going. once you have the remote stuff set up you can get rid of the extras but without them now, no way.

---

### Post by kidders on 2007-03-26
Hi there and welcome,

You could try flying blind for a few minutes, and see what happens. You'd at least need to have an old keyboard lying around. Hopefully, you already know what you would be seeing if you were to do this with a monitor plugged in.

[LIST=1]
[*]Hit CTRL+ALT+F1 to open a text console.
[*]Log into your headless system.
[*]Do a **sudo apt-get install openssh-server**.
[*](Have a listen for reassuring disk activity.)
[*]After a while, make sure the server has started up correctly with a **sudo /etc/init.d/ssh restart**.
[*]Hit CTRL+D.
[/LIST]

From there, you can log into your box remotely, enable XDMCP, and so on. Assuming you have X on your PowerBook, something like **Xquartz -query ubuntubox** should let you log in graphically.

---

### Post by halitech on 2007-03-26
problem is, he's headless, armless and legless. Unless the system has already been setup, he can't log in remotely and you would need to enable the XDMCP before logging in remotely.

here is a great howto on setting it up once you have a head and arms

[http://ubuntuforums.org/showthread.php?t=191564]("http://ubuntuforums.org/showthread.php?t=191564")

---

### Post by kidders on 2007-03-26
I've just had a brainwave...

Although Ubuntu doesn't, there must be *some* Linux distro out there that has an SSH server in it by default. If you can find one, you could download its boot CD image, stick it in your computer, chroot into your Ubuntu environment remotely, and go from there.

Halitech, do you happen to know if Gentoo's LiveCD starts an SSH server by default, by any chance? It seems to me to be a likely candidate, but for the life of me, I can't remember.

**Edit:** Damn. It doesn't. :-( *Something* must!!

---

### Post by boogersmcgee on 2007-03-26
I'm pretty sure remote login has been enabled as a previous guest to my house did login through the terminal on my mac. He did not show me how though and is not available to consult.  He was the one that told me setting this kind of thing up should be fairly easy.  Sorry I can't help more but once I have this setup I should be good to go.

---

### Post by halitech on 2007-03-26
> **kidders said:**
> I've just had a brainwave...

Although Ubuntu doesn't, there must be *some* Linux distro out there that has an SSH server in it by default. If you can find one, you could download its boot CD image, stick it in your computer, chroot into your Ubuntu environment remotely, and go from there.

Halitech, do you happen to know if Gentoo's LiveCD starts an SSH server by default, by any chance? It seems to me to be a likely candidate, but for the life of me, I can't remember.

**Edit:** Damn. It doesn't. :-( *Something* must!!

there probably is but I have no idea which one as my experience has been pretty much limited to (X)Ubuntu and Mandriva 2006 

>   	I'm pretty sure remote login has been enabled as a previous guest to my house did login through the terminal on my mac. He did not show me how though and is not available to consult. He was the one that told me setting this kind of thing up should be fairly easy. Sorry I can't help more but once I have this setup I should be good to go.

logged into your Mac or used your Mac to log into something else?

---

### Post by boogersmcgee on 2007-03-26
Logged into the computer in question using my Mac... the only thing is that he did not tell me how he did this or set it up.  I should be able to get a screen etc from work but that won't be for another week or so. If its not possible then thats fine but if it is I would like to get this up and running within the next couple days.

---

### Post by halitech on 2007-03-26
if he was able to log into the Ubuntu machine from your Mac, then it must already be set up. Opena terminal (Applications - Accesories - terminal) and type vncviewer ipaddress:1 and it should ask for the password and let you in

---

### Post by boogersmcgee on 2007-03-26
no dice... thanks for the suggestion but it did not work... I got a message saying that the command could not be found.  I tried a VNC shell and it timed out.. maybe it wasn't configured after all... I was sure it was but.... any other ideas?

---

### Post by halitech on 2007-03-26
sorry, my bad, that's the linux command :( 

try this from kidders point

> Assuming you have X on your PowerBook, something like Xquartz -query ubuntubox should let you log in graphically.

---

### Post by jinx099 on 2007-03-26
```
ssh <user>@<ip address>
```

From there you can install and configure vnc if you wish.

---

### Post by boogersmcgee on 2007-03-26
ahahaa... that worked... thanks for pointing that out Hal... Im now logged into the command line of the other computer.  I can work the rest from here... thanks so much.

---

### Post by halitech on 2007-03-27
glad to hear you got in and are working :)

don't hesitate to ask if you run into any other problems :)

---

