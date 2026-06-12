---
title: "Starting up?"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by wei_li on 2005-12-11
The installation went through but it just brings me back to dos and asks for the username and password but when I put them in the ubuntu doesn't start up? Is there a command to boot it up or should i just reinstall?

---

### Post by Zelut on 2005-12-11
it sounds like either 1) you installed the server version (did you just press ENTER to start installation, or type 'server'?) or 2) It may have a problem loading your GUI at startup and needs a little manual tweaking...

Does it allow you to login?  Are you left at a prompt similar to: <name>@computer:~$  ?  Try 'startx' and let me know what it does..

---

### Post by wei_li on 2005-12-11
I only hit enter to start the installation, I logged in and the command line starts off like that <name>@computer:~$, when I typed in startx it said -bash: startx command not found

---

### Post by Ali_Baba on 2005-12-11
You might try sudo apt-get install gdm and sudo apt-get install gnome.Just in case you dont have those installed :)

---

### Post by wei_li on 2005-12-11
Couldn't install them, it said E:  could not open locked file

---

### Post by Mustard on 2005-12-11
[QUOTE=Ali_Baba]You might try sudo apt-get install gdm and sudo apt-get install gnome.Just in case you dont have those installed :)[/QUOTE]

Assuming he is using Ubuntu, I would think it might even be better to do a sudo apt-get install ubuntu-desktop.  The metapackage should install gdm and gnome as well as anything else that might be missing.

---

### Post by Mustard on 2005-12-11
[QUOTE=wei_li]Couldn't install them, it said E:  could not open locked file[/QUOTE]

Hmmm seems strange to be getting these errors on a clean install.

When it says the the file is locked does it also ask you if you are root?

---

### Post by wei_li on 2005-12-11
nope doesn't ask me if i'm the root but it does say (13 permission denied)

---

### Post by wei_li on 2005-12-11
and yes i'm using ubuntu

---

### Post by Mustard on 2005-12-11
[QUOTE=wei_li]nope doesn't ask me if i'm the root but it does say (13 permission denied)[/QUOTE]

Are you using sudo in front of the commands?

```
sudo apt-get install ubuntu-desktop
```

If you are using sudo in front of the commands then they should be working.  If they aren't then I can only assume that the install has not given the first user account sudo privileges.

All these issues are quite probably solveable using different terminal commands and slowly eliminating each obstacle as it comes up, but I would be tempted to try installing again from scratch, because this particular install is running into a lot of issues that are not normal.

---

### Post by wei_li on 2005-12-11
oops, yeah it was the sudo part that was missing, now its downloading :KS  
after the download should i enter startx? or reboot or something?

---

### Post by Mustard on 2005-12-11
[QUOTE=wei_li]oops, yeah it was the sudo part that was missing, now its downloading :KS  
after the download should i enter startx? or reboot or something?[/QUOTE]

Yeah try startx first to see how it goes.

```
startx
```

A reboot might fix things after its finished installing ubuntu-desktop, but I am curious what is going to happen when you start the X server up. If you get an error message of some kind, post it in here with as much detail as possible.

-edit-

If you want to get all fancy and reboot via terminal you can use this command. ;)

```
shutdown now -r
```

I don't think it needs a sudo in front of it to work, but if you get some sort of permission denied error then it may well do.  The -r part of the command is telling it to reboot after the shutdown.

---

### Post by wei_li on 2005-12-11
I am going to reinstall ubuntu because when I entered startx it told me that the account I was on was not allowed to start the server up?  I tried going in as root but apparently I must have hit a extra key in the password soo.... redoing it.... 
So I should be back in like 15+ minutes or so after I've redone the installation of ubuntu-desktop, gdm and gnome.  :???:

---

### Post by Mustard on 2005-12-11
[QUOTE=wei_li]I am going to reinstall ubuntu because when I entered startx it told me that the account I was on was not allowed to start the server up?  I tried going in as root but apparently I must have hit a extra key in the password soo.... redoing it.... 
So I should be back in like 15+ minutes or so after I've redone the installation of ubuntu-desktop, gdm and gnome.  :???:[/QUOTE]

Ok..hopefully the install goes smoothly this time. :)

Did you try startx with sudo in front of it?

```
sudo startx
```

I'd also mention that you there is an IRC support channel called #ubuntu on the irc.freenode.net server.  If you are familiar with IRC and want more immediate help with your issue, you could try there, as well as here in the forum.  I quite often hang out in the #ubuntu channel.

---

### Post by wei_li on 2005-12-11
This is what happened when i restarted the computer and typed in sudo startx....

xinit: no such file or directory (errno 2): no server "X" in path....
then it says to use the "--" command or get the patch checked out....(which i have no idea how to do it)
...

zinit: connection refused (errno111): unable to connect to X server
xinit: No such process (errno 3): Server error

:confused:

---

### Post by aysiu on 2005-12-11
It sounds as if you need to reinstall.
I've never heard of this happening, and I don't think trying to solve the problem as-is is worth the effort.

---

