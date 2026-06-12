---
title: "Is Ubuntu Server version really neccessary for new file server?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2007-04-29
Hi everyone,

I think I may have already mentioned this before in a previous post, but I am not sure.  I got a old used Compaq deskpro that I loaded Ubuntu Desktop onto and even on the ageing box it works fine, but here is my question.

I would like to stick a large drive or two in the old Compaq and use it for a file server.  I have never setup a server before and they are definitely not my area of expertise.  I plan on using this server box as a first time hands on experiment with setting up and running a server.  

Now here is my question.  Is it really a good idea to bother installing the server version of Ubuntu onto my old compaq or can I run the server with the current desktop install?  As I mentioned before I do not no anything about running a server beyond the theory so bare with me if this seems like a goofy question to be asking.

I am also thinking of digging up some more RAM (128 MB SD RAM seem pretty underpowered).

---

### Post by Happy_Man on 2007-04-29
Well, if you want to, it wouldn't hurt. But, if you've already got an existing install, I don't really think you need to reinstall. Mainly, a server install is just for a one-time setup then leave it alone forever-type thing.

---

### Post by Nythain on 2007-04-29
you dont HAVE to install server editition... everything it installs can be installed on the desktop version through apt-get or synaptic... but if you have never run a server of any sorts you might want to consider it.

what kind of file server... samba, ftp, etc... if just serving files over a local network or via ftp is all you want to do, then you might not really want all the added extra server daemons installed with server edition, like apache, mysql, and postfix (mail server).

if your gonna serve anything you might want to consider upgrading the ram, always a good idea

---

### Post by DanFromWinterpeg on 2007-04-29
Thanks,

I was thinking of running FTP for this server.  The only thing I need to really concern myself with is that Both my Ubuntu PC and my Windows XP boxes need to be able to access it.  I don't see this being a serious problem, but it could make things interesting.


Any suggestions would be very much appreciated.

Dan

---

### Post by [S|G] on 2007-04-29
If you're going to share files only for your local network, I'd suggest you to set up a Samba server instead of an FTP server. This way you would be able to access the files both from windows and linux just like any other windows shared folder.

---

### Post by Nythain on 2007-04-29
yeah, samba is much easier than trying to set up an ftp server, though thats not to difficult either. either way, i dont think a reinstall of server edition is really gonna be worth it... besides, if you set it all up this way, you will get much more familiar with those configuration files and how everything works :)

---

### Post by PilotJLR on 2007-04-29
Though you definitely do not need to use the Server edition, you'll save on space and resources with it. The server version installs very little software, so it's lean; this means you won't waste space with things like games,  firefox, etc, and you won't waste memory running X11.

Keep in mind the server install has no graphical desktop (though you can add one easily). So you'll want to either  know the command line, or be willing to learn it. Howtoforge has some really nice tutorials for this.
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by DanFromWinterpeg on 2007-04-29
Thanks,

I suppose I will try running Samba.  That sounds easier


Dan

---

### Post by DanFromWinterpeg on 2007-04-29
Thanks again for the good advice.   I do like working from the command line on a computer for a lot of things, but unfortunately I am still very green when it comes to Linux or any other Unix like OS. I have used mostly DOS, Windows,  and older versions of Mac OS.  I guess what it boils down to is I am still very unfamiliar with the syntax used in the Linux command line.  I cannot effectively tell the computer what to do because I am still learning the language so to speak.   As a result I am a lot more dependant on the GUI then I would like....for now.  Thanks for the link.

---

