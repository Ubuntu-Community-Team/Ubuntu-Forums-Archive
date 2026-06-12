---
title: "Setting up SAMBA on debian to share files with a WIN XP machine"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by zahid on 2006-01-03
Hi all,

This is my first post. :KS 

Can anyone tell me how to use SAMBA on a Debian system to share files with a Windows XP  machine?

Any help would be appreciated.


Tnx.

---

### Post by gnu2tux on 2006-01-03
Hi,

If you have installed the samba service from the Synaptic Package Manager then the file smb.conf in the /etc/samba folder can be edited as root:

```

sudo gedit /etc/samba/smb.conf &

```

In the file make a share, I have the following line at the bottom of my smb.conf:

```

[mp3]
path = /home/ajross/bin/mp3
comment = my music
available = yes
browseable = yes
public = yes
writable = yes

```

Restart the samba service:

```

sudo /etc/init.d/samba restart

```

Hope that gets you started..

Cheers,

Al.

---

### Post by zahid on 2006-01-04
Thanks gnu2tux for the help.

Can't wait to try it out!

One small question though: 

The last code:

sudo /etc/init.d/samba restart

sounds like a command line prompt code rather than just going into folders, right?

---

### Post by AndyCooll on 2006-01-04
Couple of tips to add to the above posts.

You'll probably also need to install smbfs as well as the samba common files.

And you'll probably need to set your Samba password, which IIRC is something like:

```
smbpasswd -a user
```

You'll then be asked to input a passowrd of course.

:cool:

---

### Post by AndyCooll on 2006-01-04
[QUOTE=zahid]
The last code:

sudo /etc/init.d/samba restart

sounds like a command line prompt code rather than just going into folders, right?[/QUOTE]

Yes it is.

---

### Post by ed_d on 2006-01-04
Or.....
System > Admin > Shared folders. You can set it all up from there, just tab on browsable, and I think you can do all your passwords and such from there. One thing though, editi the /etc/samba/smb.conf file and make sure you are part of the same workgroup. That is the easiest way to make sure all will see you.

---

### Post by CK05 on 2006-01-06
[QUOTE=gnu2tux]Hi,

If you have installed the samba service from the Synaptic Package Manager then the file smb.conf in the /etc/samba folder can be edited as root:

```

sudo gedit /etc/samba/smb.conf &

```

In the file make a share, I have the following line at the bottom of my smb.conf:

```

[mp3]
path = /home/ajross/bin/mp3
comment = my music
available = yes
browseable = yes
public = yes
writable = yes

```

Restart the samba service:

```

sudo /etc/init.d/samba restart

```

Hope that gets you started..

Cheers,

Al.[/QUOTE]

Thanks I've done this but my XP machine is now asking for a password. I enter in my Ubuntu username but it's not working, do you know how to change the username and password? 

Thanks.

---

### Post by j_monty10 on 2006-01-06
[QUOTE=CK05]Thanks I've done this but my XP machine is now asking for a password. I enter in my Ubuntu username but it's not working, do you know how to change the username and password? 

Thanks.[/QUOTE]

You will also need to setup samba users. These can be the same as the users on your systems, but they need to be defined.

```
smbpasswd -a system_username
sudo gedit /etc/samba/smbusers
```

Also, when all else fails, RTFM :)  [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server")
I have tried just about every flavor of linux and so far ubuntu has been the best.  Great community and great OS!

---

### Post by zahid on 2006-01-12
Hi again ppl.

Thanks for your inputs.

One last thing.

Does the above methods also work if I want to share files on Debian from Windows xp?

And what if I want to transfer a file from debian to win xp?


Tnx.:D

---

### Post by j_monty10 on 2006-01-17
You will need to create a share on Windows in order to connect from ubuntu.  Then it is just a matter of clicking on Places -> Connect to server -> choosing Windows Share and then filling in the appropriate information

---

