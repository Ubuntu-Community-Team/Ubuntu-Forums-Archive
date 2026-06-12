---
title: "No root permissions anymore"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Luis_vxd on 2007-06-11
Hi

Im a newbe. A happy one up to an hour ago :-)

I lost the ability to install progs or change to root. My Administration Menu is a lot smaller and no more remove /install menu. I was "playing" with command sudo bash and usermod.

What I did wrong? How can I correct it?

Thanks.

---

### Post by Skrynesaver on 2007-06-11
I suspect you have removed yourself from the adm group.  To check if this is the case you should see which groups  your username is a member of,  the groups command should tell you which groups you are a member of.

If you aren't in the admin group then you will have to reboot with the live CD and mount your root partition then edit /media/part_name/etc/group and add your name after the admin group declaration.  Then reboot without the CD and you should be good to go.

If you are still in the admin group, you may have damaged your /etc/sudoers file.  The following line should exist in this file.
```
%admin ALL=(ALL) ALL
```

---

### Post by Luis_vxd on 2007-06-12
You were right Skynesaver, I removed myself from admin group.
I was following instructions from LINUX FORMAT May edition to install VirtualBox and I think I typed *'usermod -g vboxusers luis'* instead of *'usermod -G vboxusers luis'*.

In the /etc/group my name was following the VboxUsers declaration: *vboxusers:x:1006:luis,root* and admin had nothing after it. Everything is back to normal. Even VirtualBox do not start again. Says Im not a member of vboxusers group...

Thank you Skynesaver

---

### Post by Luis_vxd on 2007-06-12
After that 'usermod' command I lost sound as well. It says "No volume control GStreamer plugins and/or devices found". Should I be part of other group besides 'admin'? It sounds that that 'usermod' command is very destructive :-). Thanks

---

### Post by Skrynesaver on 2007-06-12
You should be a member of the following groups
scanner
plugdev
audio
dip
floppy
cdrom
dialout
adm
admin


Or more accurately, on my setup I am a member of the above groups ;)
you will have restricted yourself to a single group by your edit and so all the above may have been lost.

---

### Post by Luis_vxd on 2007-06-12
Thanks. 
All this has been consequence of that "usermod -G" command. I tried it again and everything went back to the start point: no root access.
Should this be the outcome of the command? is the LINUX Format magazine wrong (page66)? Or is just an issue specific to Ubuntu?

---

### Post by Skrynesaver on 2007-06-12
```
usermod -a -G newgroup 
``` appends a user to the new group without effecting their original group ;)

---

### Post by Daniel-Dane on 2007-06-13
Hey, not to hi-jack this topic but I am having a similar problem.

I changed my user group from the one I made when I installed Ubuntu (7.04). I changed it to root, but now I've lot my sound and admin rights.

I tried looking after the directory but couldn't find it. I dual boot with Windows, so could I get a walkthrough?

---

### Post by Skrynesaver on 2007-06-13
Hi Daniel,

Ok first you'll have to reboot using a liveCD, then open a terminal and
```

sudo mount

```If your root partition is listed cd to the directory it is mounted on and open etc/passwd from this directory.
the entery for your username should look like this
```
daniel:x:1000:1000:Daniel Dane,,,:/home/daniel:/bin/bash
```These are in order ,seperated by colons ':'
Your username
Your password (x indicates shadow passwording, don't worry about it)
Your UID
Your primary group
Your details
Your home directory
Your prefered shell

If your primary group is different change it back.

Next edit the /etc/group file in this directory
add your username after all the groups listed above (note: multiple userrnames are comma seperated)
eg. admin:daniel,skrynesaver

Hope that helps

---

### Post by Daniel-Dane on 2007-06-13
What's all those smilies for?

---

### Post by Skrynesaver on 2007-06-13
Ooops, unfortunate, have set as a code block now, should be legible

---

### Post by Daniel-Dane on 2007-06-13
Well, I found the password list (was named "passwd") and it looked as it should (username and name varies from what you have shown, of course). But I had to boot Windows in order to get permission to save the file. It all works now!

THANKS!

---

