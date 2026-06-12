---
title: "getting VMware server off my computer"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Phone33 on 2007-08-04
i was trying to install VMware server on my computer and i managed to botch the install... weird. now i want to uninstall it and reinstall it w/ synaptic package manager? so who do i clear this thing of my computer, i try running purge commands and remove commands but it stays there. i even ran 

sudo  vmware-uninstall.pl

and i get this

Uninstalling the tar installation of VMware Server.

 * Restarting internet superserver...                                    [ OK ] 
The removal of VMware Server 1.0.2 build-39867 for Linux completed 
successfully. Thank you for having tried this software.

but it is still there....

---

### Post by TBerben on 2007-08-04
is it still there in when you run it you can use it as if you never ran the uninstall script, or is it still there as in the menu entry wasn't deleted

---

### Post by Phone33 on 2007-08-05
there is still the vmware server console under my system tab. and it does not run

---

### Post by insane_alien on 2007-08-05
remove the folder /etc/vmware

```
sudo rm -rf /etc/vmware
```

---

### Post by anewguy on 2007-08-05
Also, you'll want to do this in a terminal window:

locate vmware

for each entry that shows:

sudo rm -r   paththatshowedonlocate

keep doing this until nothing shows in the locate vmware command.

This took me maybe 10 minutes at the most.:)

---

### Post by Phone33 on 2007-08-06
i do locate vmare and there are a few hundred entries that are in  /home/chris/.Trash

so i need to get rid of all of those as well. i tried emptying trash but that did nothing

---

### Post by Phone33 on 2007-08-06
hey that worked! thanks for the help!

---

### Post by wak_wak on 2007-08-19
If you still want to install it:

I was having the same problem and ran in to various others after spending a couple of hours trying various solutions.

Ultimately I went here: [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

That totally got it up and running.

The only thing I had to change was that where it says to command: sudo vi /etc/apt/sources.list

I changed "vi" to "gedit".

Make sure to go to vmware.com and get a license.

You'll love it once you've got it up.  I used it a bit under Windows before and it's an amazing tool.

---

### Post by Beatsake on 2007-08-25
I followed the instructions above. 

locate vmware and deleting everything it found.

when I tried to install

sudo apt-get install vmware-server 

I get an error: 

E: Sub-process /usr/bin/dpkg returned an error code (1)

any ideas what I'm doing wrong?

---

### Post by Beatsake on 2007-08-25
> **Beatsake said:**
> I followed the instructions above. 

locate vmware and deleting everything it found.

when I tried to install

sudo apt-get install vmware-server 

I get an error: 

E: Sub-process /usr/bin/dpkg returned an error code (1)

any ideas what I'm doing wrong?


here is the output:


Reading package lists... Done
Building dependency tree
Reading state information... Done
vmware-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.3-1) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

