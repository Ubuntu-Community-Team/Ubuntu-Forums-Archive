---
title: "You do not have the permissions necessary to save the file. - on MY desktop"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-08-29
tried to create a file on my desktop using terminal but got this when I went to save:

```

Could not save the file /home/john/Desktop/bf2-server/bf2/admin/test

You do not have the permissions necessary to save the file.
Please, check that you typed the location correctly and try again.
```


I am logged in as john so I would have thought I have full rights to any and all folders on my Desktop?


To create the file and save it I had to sudo it. ](*,)

---

### Post by FuriousLettuce on 2006-08-29
You must have accidentally changed permissions of the Desktop file.

To fix it graphically, type the following into gnome-terminal:

```
gksudo nautilus /home/john
```

This will load up nautilus as root. Next, right click on the Desktop folder and go to permissions. There are two drop down boxes - make sure that they are both set to john (both the user and group), then click OK.

EDIT: Only just re-read your post. If the above doesn't work, can I ask where is the bf2 file coming from?

---

### Post by Scorpuk on 2006-08-29
Just worked out what happened.


When i downloaded the dedicated server is downloaded it to /home/john

When I tried to install it i got permission errors creating the install directory in /home/john/Desktop/bf2-server, so I sudo'd the install program.


DOH every folder is owned by root!


Must be something in permissions about running a file in a folder lower than Desktop. Prob quick deleteing and reinstalling from within /Desktop/bf2-server. :mrgreen: 


Mind you not a bad solution as I am having problems with punk buster versions. :eek:

---

### Post by steve.horsley on 2006-08-29
This'll fix it then:
sudo chown -R john:john /home/john/Desktop

---

### Post by plyte on 2007-12-08
> **steve.horsley said:**
> This'll fix it then:
sudo chown -R john:john /home/john/Desktop

I just sudo chown -R me:me /etc
so that I could edit th apache2 config files. Is this a security issue? If it is, what is the command to undo the permissions?

---

### Post by plyte on 2007-12-08
> **plyte said:**
> I just sudo chown -R me:me /etc
so that I could edit th apache2 config files. Is this a security issue? If it is, what is the command to undo the permissions?

I quickly found out that doing

# sudo chown -R me:me /etc

is not good at all. You get the following issue: /etc/sudoers is owned by uid 1000, should be 0

I was able to fix this by booting in recovery mode (restarting and hitting ESC when boot screen shows right before ubuntu load screen) and then at the prompt doing:

# chown root.root /etc/sudoers

So I was able to get back to where I started, but how do I go about editing the apache2 config files if I need root access??

---

### Post by ptn107 on 2007-12-08
You should get in the habit of using *sudo* for granting temporary administrative privileges when working with any configuration files (apache, proftp, samba, etc...)

ex.
```
sudo gedit /etc/apache2/httpd.conf
```

**Back up any file you plan to make modifications to.

---

### Post by plyte on 2007-12-08
> **ptn107 said:**
> You should get in the habit of using *sudo* for granting temporary administrative privileges when working with any configuration files (apache, proftp, samba, etc...)

ex.
```
sudo gedit /etc/apache2/httpd.conf
```

**Back up any file you plan to make modifications to.

ptn107 this works perfect, thanks for the info!

---

### Post by ptn107 on 2007-12-08
your welcome

---

