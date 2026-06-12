---
title: "No GUI"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Jabithew on 2006-02-03
I am running Ubuntu 5.10 on a Dell (boo, hiss! :p). On startup Xorg fails, saying it can find no screens. Looking through the server record it has correctly identified my graphics card (ATI X600 PCI-E) and my monitor (Dell generic). I can still log in to the OS and use the command line, but I'm finding it a little...terrifying. Any idea at all what might be going wrong? 

This is the first time I've used Linux. And I had no idea where else to put this.

---

### Post by AndyCooll on 2006-02-03
Using the command line, what happens if you type:

```
sudo apt-get ubuntu-desktop
```

:cool:

---

### Post by serzz on 2006-02-03
Had same problem. I remember I partly solved it by disabling agp but couldn't get 3d acceleration to work. So I switched to suse, evrything works. But still waiting for dapper, ubuntu is number one. :D

---

### Post by Jabithew on 2006-02-03
Thanks. How would I disable AGP? Will start googling...

I tried a friend's Knoppix disc and that worked ok. Well, it was rubbish. But it worked. I wonder if the Kubuntu environment will work better?

---

### Post by Mustard on 2006-02-03
First I would backup your current xorg.conf file (although its not currently working, but you might want to use it as a reference), using this command...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then you could try reconfiguring xorg.conf using this command..

```
sudo dpkg-reconfigure xserver-xorg
```

I would switch to the 'vesa' drivers, when you reconfigure, to see if you could get a GUI up that way.  Once you have that up you can set up ATI drivers.  When answering the questions it asks, just choose defaults for any questions you don't know the answers to.

**If you have a working internet connection**, I would try getting onto the ubuntu irc support channel via a command line irc client, like irssi.  From there you could at least have someone to chat with and troubleshoot the issue. :)

If irssi is not installed I would type this to install it...

```
sudo apt-get install irssi-text
```

Commands to get onto IRC would be...

```
irssi                              #this should start up a command line IRC client

#From within the client you would do these commands

/connect irc.freenode.net         #connects the client to the relevant irc server
/join #ubuntu                        #joins the ubuntu channel (IRC support channel for ubuntu)

```

---

### Post by Jabithew on 2006-02-04
Messing with the Xserver settings didn't solve the problem, though I did find a couple of possible problems. The only problem left which I cannot solve is that the program may be trying to us the wrong bus address, but I don't know what the bus address of the card is.

---

### Post by Jabithew on 2006-02-06
I've found the bus address and it's right. I even checked I had the latest version of the xserver. I am at a total loss.

---

### Post by self0 on 2006-02-12
[QUOTE=Jabithew]I am running Ubuntu 5.10 on a Dell (boo, hiss! :p). On startup Xorg fails, saying it can find no screens. Looking through the server record it has correctly identified my graphics card (ATI X600 PCI-E) and my monitor (Dell generic). I can still log in to the OS and use the command line, but I'm finding it a little...terrifying. Any idea at all what might be going wrong? 

This is the first time I've used Linux. And I had no idea where else to put this.[/QUOTE]

I have this same problem and I don't what to do ;/

help pls...

---

