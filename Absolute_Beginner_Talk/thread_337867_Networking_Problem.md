---
title: "Networking Problem"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by clu on 2007-01-13
I installed Ubuntu Edgy about a month or two ago.    I had wired networking and wireless without wpa working out of the box.   
Recently I was trying to get wireless wpa working and installed network-manager-gnome.    Couldn't get it working so I removed it via synaptic and "fixed" the interfaces config.    Now I can't connect to any network.     Any ideas on what I should check to get back to the default config?  I'd rather not reinstall if I can get around it.   
Any help would be greatly appreciated .    Thanks

---

### Post by JayTee on 2007-01-13
Open a terminal and change to /etc/network/ by typing:
cd /etc/network
then type ls -ao to list all the files in a detailed alphabetical order.
it should show you an interfaces file and _hopefully_ will show an interfaces~ file as well. the one with the ~ at the end is a backup of your original interfaces file. Use the mv command to rename the interfaces file to something like interfaces.old and then rename the interfaces~ to interfaces. 
 example:
name@hostname:/etc/network$ sudo mv /etc/network/interfaces /etc/network/interfaces.old
name@hostname:/etc/network$ sudo mv /etc/network/interfaces~ /etc/network/interfaces

 And then do a restart.
That should get you back up and running.

---

### Post by clu on 2007-01-14
Thanks for the help.    Those steps fixed it right up.    :D

---

### Post by clu on 2007-01-19
I still have a minor issue that I haven't been able to find the answer to.    

Now when ever I reboot the computer it doesn't connect automatically to the wired network.     It used to before I starting messing with this WPA stuff.    
I have to disable and re-enable the interface and then it works great.    

How can I get it to connect automatically after a restart?

---

