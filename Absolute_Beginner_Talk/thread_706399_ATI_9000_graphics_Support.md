---
title: "ATI 9000 graphics Support"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Kdawkins on 2008-02-24
So first off, I am brand new to the Linux OS world. I am very used to windows and how windows works.... so knowing that, hopefully you can help me out. I am using a IBM Thinkpad T41 with a ATI radeon 9000 graphics card. I really want to use the fancy graphics that Ubuntu has. I have been reading a LOT (2+ hours) on these forums trying to figure out how to work it. 

I came across this post : [http://ohioloco.ubuntuforums.org/showthread.php?t=550082&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=550082&page=2) 

More specifically, post #18 by Michael.

 I was wondering if someone could simplify his post a tad for me. For instance, how do I get to xorg.conf to edit it? Also how do I compiz with SKIP_CHECKS=yes? Small things like that....

Is there a better way to make this work? 

Thank you SO much for any help!
Kevin
P.S. I love Ubuntu and if I can get this to work i'm switching over my desktop form windows. :-)

---

### Post by rapiscan on 2008-02-24
To edit your xorg.conf:
Open a terminal, Applications->Accessories->Terminal
Type this in the terminal to edit your config:
```
sudo gedit  /etc/X11/xorg.conf
```
You can use the gedit text editor to make changes, then save and close gedit.

To create the file with SKIP_CHECKS=yes, type in your terminal:
```
gedit ~/.config/compiz/compiz-manager
```
Likely the file doesn't exist, so a new empty file will be created.  Add "SKIP_CHECKS=yes" without the quotes and save it.

You will likely need to restart your x-server.  You can do this by hitting ctrl-alt-backspace.  (Warning, this will kill your current graphical applications and you will have to relogin.)

---

### Post by Kdawkins on 2008-02-24
Thanks! That is exactially what I was looking for. Do I have to do this coding every time i log in or will this be permanent? One more question, do I have to install any other drivers or is this the only thing I have to do? 

thanks so much,
Kevin

EDIT: Is the xorg.conf suppose to be blank?

---

### Post by rapiscan on 2008-02-24
No, sorry, I made an error in my code example.  It should be in  /etc/X11/xorg.conf

I edited my comment so that it is corrected.

---

### Post by rapiscan on 2008-02-24
> do I have to install any other drivers or is this the only thing I have to do? 

I honestly didn't read much through the thread that you linked to, I was just trying to help with the basics.  I can't guarantee this will work for you.  Post #18 seems to say that this should work as long as you're using the ati driver.  This is (generally speaking) the default open source driver that's selected if you have an ATI card and if you haven't installed any other drivers.

---

### Post by Kdawkins on 2008-02-24
how would I go about getting this ATI driver? The one of their website is apparently non-functional... is there an open-source one available?

---

### Post by xeth_delta on 2008-02-24
> **Kdawkins said:**
> how would I go about getting this ATI driver? The one of their website is apparently non-functional... is there an open-source one available?

Yes, there is an open source driver that should provide hardware acceleration for your card.
Make a backup of your /etc/X11/xorg.conf. Then run the following in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions.
After that, open the file
```
gksu gedit /etc/X11/xorg.conf
```
Make sure that in the <<Section "Device">> the line starting with driver reads <<driver "radeon">>. Save the changes.
Reboot or restart the X11 server (Control-Alt-Backspace)

---

### Post by Kdawkins on 2008-02-24
> **rapiscan said:**
> 
To create the file with SKIP_CHECKS=yes, type in your terminal:
```
gedit ~/.config/compiz/compiz-manager
```
Likely the file doesn't exist, so a new empty file will be created.  Add "SKIP_CHECKS=yes" without the quotes and save it.


When I open this file, it is blank and when I add the line to it and try to save it I get an error telling me the file does not exist and thus it cannot save it...

---

### Post by rapiscan on 2008-02-24
I just tried gedit with a non-existing file, and it created the file as expected.

I suspect the message is saying that a directory does not exist. Does the ~/.config/compiz directory exist?

You can test this like so: 
```
ls -al ~/.config/compiz/
```

It will print directory information if the directory exists, or tell you that the directory doesn't exist.

I suspect the instructions in that thread might be missing an important step, which is starting up compiz.  If the .config/compiz/ directory doesn't exist, it will likely be created the first time you run compiz.  You can do this from the terminal, just type
```
compiz
```
Again, I'm not positive, but I suspect that the first time you try to run compiz it will fail, but it will create the compiz directory.  Once you add the SKIP_CHECKS line, try starting compiz again.

---

