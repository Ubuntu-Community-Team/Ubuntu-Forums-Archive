---
title: "Sudo doesn't work?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by grumble on 2008-04-09
Hi,

Completely new to Linux so apologies in advance for any inherent idiocy in my posts:oops:

I've installed Xubuntu on an older PC (specs: PIII 850mhz, 384mb Ram), and have the following problems:

1) Terminal crashes the machine, making it reboot. To get around this I installed Gnome terminal, which DOES work, but still - any suggestions on how to get the XFCE terminal prog. working would be great.

2) Sudo doesn't appear to work. I'm trying to set up Samba and am attempting the following:

sudo nano -w/etc/samba/smb.conf

This gives me a "command not found" response. The same occurs for any sudo command in the terminal.

Can anyone help?

---

### Post by Oldsoldier2003 on 2008-04-10
> **grumble said:**
> Hi,

Completely new to Linux so apologies in advance for any inherent idiocy in my posts:oops:

I've installed Xubuntu on an older PC (specs: PIII 850mhz, 384mb Ram), and have the following problems:

1) Terminal crashes the machine, making it reboot. To get around this I installed Gnome terminal, which DOES work, but still - any suggestions on how to get the XFCE terminal prog. working would be great.

2) Sudo doesn't appear to work. I'm trying to set up Samba and am attempting the following:

sudo nano -w/etc/samba/smb.conf

This gives me a "command not found" response. The same occurs for any sudo command in the terminal.

Can anyone help?
sudo probably works fine you need a space between -w and the filename

---

### Post by grumble on 2008-04-10
Thanks for your help, but no, I tried it both with and without a space. No dice :(

---

### Post by Oldsoldier2003 on 2008-04-10
> **grumble said:**
> Thanks for your help, but no, I tried it both with and without a space. No dice :(

without a space is definitely wrong and you will get the error. 

can you post the return from a couple commands for us.

```
id <your username>
which nano
whereis samba
```

---

### Post by bindatype on 2008-04-10
Starting with problem 2 (I don't see how you can fix 1 with first fixing 2) are you sure that you are logged in the an administrator account? Open System->Adminstration->Users and Groups...check your privileges by highlighting your username, clicking User Privileges, and making sure Administer System is checked. If you can't get that far you probably aren't and administrator. You could also open an xterm and type groups then <enter>. Look for a group that says admin. If you don't see it then that is your problem.

As for problem 1, instead of opening xfce-terminal, open an xterm (try alt+F2 and type 'sudo xterm' or if that won't work try 'gksudo xterm'). Then open your favorite editor and edit /etc/X11/xorg.conf. Search for default depth and change it from 24 to 16. Then log out and log back in. You should now be able to run xfce-terminal without any problems. 

You could also try alt+F2 'gksudo gedit' and open /etc/X11/xorg.conf that way.

---

### Post by grumble on 2008-04-10
Oldsoldier,

Thanks, I will do so ASAP... posting from work, and don't have the machine in front of me. I can confirm that I DEFINITELY tried it with a space, to no avail.

Bindatype... will check to make sure. I'm using the default user / password combination xubuntu made for me on install. I have not created any other users. 'scuse my ignorance, but that would make me the administrator, no?

---

### Post by Oldsoldier2003 on 2008-04-10
> **grumble said:**
> Oldsoldier,

Thanks, I will do so ASAP... posting from work, and don't have the machine in front of me. I can confirm that I DEFINITELY tried it with a space, to no avail.

As far as the output from id : if you are not in the group "admin" you have a permissions problem. The reasons I am having you do the which and whereis are to check your paths and to be sure both  nano and samba are properly installed.

---

### Post by grumble on 2008-04-10
Thanks all for your help. Upgrading to hardy heron solved both problems!

---

