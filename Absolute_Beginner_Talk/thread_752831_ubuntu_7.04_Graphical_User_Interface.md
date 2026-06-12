---
title: "ubuntu 7.04 Graphical User Interface"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by mikemont012 on 2008-04-12
I recently tried reinstalling my cups printer s/w in the synaptic manager - after the re-install I lost all my desktop icons.  I re-booted the system Ubuntu 7.04 i386 to find I'm in text mode   it seems I have lost the GUI. Tried a init 1 command on the command line - systems re-loads but stays in text mode - how can I recover the GUI.  The re-install of the cups printer s/w seems to corrupted something.  Any assistance would be much appreciated.

Mike M

---

### Post by zvacet on 2008-04-12
Try with 

```
startx
```

or

```
sudo /etc/init.d/gdm restart
```

If that don´t give result 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mikewhatever on 2008-04-12
I am not sure if it's the gui or just the login program, but try <sudo apt-get install ubuntu-desktop>. Post back any messages you get.

---

### Post by mikemont012 on 2008-04-12
Guys tried the x server commands - stated the server but not the GUI - now running apt-get ubuntu desktop so far so good once finished I'll report back.

thanks

Mike M

---

### Post by mikemont012 on 2008-04-12
Guys

None of this worked;

- once all the apt-get install ubuntu-desktop loaded - rebooted back to a command line - note before I get the command line I do have a ubuntu graphical load screen - once the load bar is full then system goes text based - login p/w which I can do.

- If I run the dpgk xserver  command just goes back to command line but get a system message reads as follows 'xserver-org postinst warning: overwriting possibly-customised configuration file; back-up in etc/X11/xorg.conf.20080121772546 

Any suggestions of where to from here?

thanks 

Mike M

---

### Post by mikemont012 on 2008-04-12
Guys

Thanks got it going - ran the apt-get install ubuntu-desktop again - went thru a setting up process then back to command line - ran startx the system fired up in root and then rebooted up she came.

thanks


MikeM

---

