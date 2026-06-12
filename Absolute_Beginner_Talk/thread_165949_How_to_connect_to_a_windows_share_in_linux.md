---
title: "How to connect to a windows share in linux"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by soultang on 2006-04-25
Hey guys ....   I'm a real noob here and need a bit of help. I am on a network and need to connect to a local windows xp machine with this linux box. Just need to transfer some files. How would I go about connecting my ubuntu machine to the XP box?

they are on the same network.....

thanks in advance

---

### Post by jazzmuzik on 2006-04-25
This was just discussed in a recent thread. Try this:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Although that's more of a permanent approach. A quick approach is to use the mount command.

---

### Post by soultang on 2006-04-25
Ahhhh   I wasnt clear ... its not a xp partition .. its a seperate windows share .. on a different machine on the network ....

---

### Post by jazzmuzik on 2006-04-25
samba is used to connect to windows shares.

---

### Post by soultang on 2006-04-25
SAMBA? .....   ok i am really a noobie :L)  ....   samba ... is that a command line app?

---

### Post by mlind on 2006-04-25
**smbclient**, which should be installed by default, is a command line samba client. use it to connect windows shares.

---

### Post by echo $USER on 2006-04-25
If you want to point and click go to Places > Connect to Server > Choose the type of share it is and the ip address and enter your credentails if required.  Also make sure the proper permissions are set on the windows box so you can write to it.

---

### Post by soultang on 2006-04-25
Thanks .. thats what i needed ...    alll workind well .....   thanks a bunch  ...   connect to server worked just fine

---

### Post by kupajava on 2006-04-28
Sorry, this is a long one...

I can browse my windows network shares through nautilus, but they don’t appear in file operation dialogs. What this means is that although I can see the individual network files, I have to save to the desktop and then copy over to the network share (and vice versa) - I can’t navigate to the share through the save dialog.

So I tried to mount the share to a local directory.

When I manually mount in the terminal screen, everything goes fine and without errors (after a few hours of working on it) but when I try to open the directory I mounted to the folder is displayed as a unknown file and I get an access denied error (even with a gksudo nautilus browser) trying to open it.  I know this cannot be the windows side since I can browse this server in nautilus using "connect to server" and everything opens just fine.

any ideas?  Im sure I am just missing something obvious but I just cant seem to get it!

also, I have also tried the whole Mount Windows Shares Permanently with fstab method (//servername/sharename  /media/mountname  smbfs defaults,uid=1000,gid=1000,credentials=~/.smbcredentials,umask=777  0  0) with the same result.  no errors in the terminal with mount -a, but as soon as I navigate to the mount point the folder I created becomes an unknown file that wont open.

---

### Post by kupajava on 2006-04-28
one more thing...

The darn share shows up on my desktop too.  Looking like it wants to work.  But when I try to open it I get a system beep and nothing....  Grrrr!

So far this has been my only ubuntu problem and the last thing I think I really need to get working before my setup is really complete.  any ideas?

---

