---
title: "where to set environment variables for custom application launchers"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by cnkbrown on 2006-05-26
I created a custom application launcher for eclipse.   I also installed an eclipse plug-in that needs to have a certain .so library on the LD_LIBRARY_PATH.  I tried adding a line to my .bashrc file, and this works if invoking eclipse from a terminal window, but it does not work when using the launcher.

   Where would I put this modification so that the launcher picks it up?

   I've considered creating a bash script, and calling the bash script from the launcher.  This does work - but seems very clunky.  Is there a better way?

   Thanks.

---

### Post by vcrfix on 2006-08-15
I also had a problem earlier when creating a launcher for eclipse with the path for Java in the local bash_profile.

I move the Java enironment to the global setting in /etc/profile (see me other post on what to add) and I put eclipse in the /opt/eclipse path.

Note I couldn't extract the tar file directly, so I extracted the tar file to my home path, and then did a sudo mv eclipse*** /opt/eclipse/

I then created a launcher from the popup menu off the desktop, and entered the following fields:

Name:  Eclipse 3.2
Generic Name: Eclipse
Command: /opt/eclipse/eclipse
Type: Application
Icon: <pick one, looks nicer on your desktop>

Click OK.

Then launch Eclipse 3.2 successfully from the desktop.

Pat...

---

### Post by vcrfix on 2006-08-15
Clariy, the full mv command that I used was

sudo mv ./eclipse /opt/

which moves the directory from my home directory to the /opt/ path.

The eclipse startup file will be located at

/opt/eclipse/eclipse

Pat...

---

### Post by givré on 2006-08-15
> **cnkbrown said:**
> 
I've considered creating a bash script, and calling the bash script from the launcher.  This does work - but seems very clunky.  Is there a better way?

That's i think the better way. That's how work a lot of apps (/usr/bin/firefox is just a bash script)
create a script eclipse2 (or whatever) which set the good environnement variable and then launch eclipse, and put it in /usr/bin (so it's in the PATH) is definitly not clunky :cool:

---

