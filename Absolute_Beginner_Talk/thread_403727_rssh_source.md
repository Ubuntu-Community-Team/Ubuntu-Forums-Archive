---
title: "rssh source"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by tim_barsness on 2007-04-07
I am trying to install rssh to follow this tutorial

[http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)

apt-get install rssh says this:

Package rssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


I am wondering what the appropriate source for this package would be.

---

### Post by ffxr on 2007-04-07
have a look in synaptic for it... 

what are you trying to achieve? and why isnt ssh satisfactory?

[https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29](https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29)

---

### Post by tim_barsness on 2007-04-07
I don't have a GUI installed.  Is there a way to use synaptic from the command line?


I basically want to create chrooted Openssh SFTP without shell access.  The tutorial uses rssh and since I don't really know exactly what I am doing, I just figured I would do what they say.

---

### Post by tim_barsness on 2007-04-07
Does anyone know the source for rssh?

---

### Post by tim_barsness on 2007-04-07
I figured it out.  It is in universe.

---

### Post by marcosXL on 2007-04-07
open: Add/Remove in the program menus "Aplications"

Open: Advance wish is located in th bottom left.
 when it open do click on type in    "ssh"
scroll down the bar until you find "Openssh-client and "openssh-server.

mark those two for installation.  


        Good Luck!!

---

### Post by tim_barsness on 2007-04-07
I don't have a gui installed, so I can't do that.  I was looking for the source to add to /etc/apt/sources.list file and I found it.  It is commented out in the default install of edgy called "universe".  

If anyone is interested in a similar chrooted sftp install, that tutorial is great.

---

