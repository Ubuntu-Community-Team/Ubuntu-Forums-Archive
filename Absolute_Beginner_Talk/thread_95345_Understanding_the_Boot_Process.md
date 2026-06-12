---
title: "Understanding the Boot Process"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by solopop on 2005-11-26
I have been following the forums and working on getting my rt2500 wireless nic card (read that Belkin54G pci card) to work on Ubuntu 5.4.

So I figured out that Serial Monkey [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Has a driver that you can download.  Note, I was able to build the rt2500.ko in the Modules directory, but Hoary Hedgehog didn't have the right QT stuff to build the RaConfig2500 application, which provides a gui to configure the wireless card.  

Fortunately I only needed the rt2500.ko module.  I found a website that talked about using the **insmod** command to set the module up, so I ran
**sudo insmod /home/mydir/rt2500-cvs-2005112312/Module/rt2500.ko**

It didn't give me any errors, so on a whim I decided to check my System->Administration->Networkng  panel, and lo and behold I saw for the first time an entry for the Wireless card.  I configured the entry, and then activated the connection and BAM! I was able to google out from my Ubuntu box.

However, when I shut the machine down and restarted it no longer had a network connection.  I have to log on at the PC, run **insmod** and then use the System->Administration->Networking panel to reactivate the connection.

Being new to Linux, I don't understand the boot process well enough to figure out how to set up the system to automatically run the insmod command at the right time, and to automatically activate the Wireless connection.  I really want the thing to boot up with a connection active so that I can use it as a web server.

On a side note, I dont know how to automatically start Tomcat either.

In windows this is easy, you can use the startup menu or the control panel to set these things up.  I am sure that it is a matter of ratting through what seems to be a complex web of scripts and binary executables but perhaps somebody has an understanding of this process and would like to share.

---

### Post by davmac on 2005-11-26
There are a couple of ways to run stuff at start up. If you want it to run just for your user, as you sign on, click on System -> Preferences -> Sessions and then click on the "Startup Programs" tab and away you go.

If you want to run it during the boot up, rather than the login, which means it'll affect all users of the system. You need to work on the init scripts.

You can write a new script and put it in /etc/init.d and then, in a terminal, type "sudo update-rc.d myscriptname defaults".

The other way is to open up a terminal and type
"sudo gedit /etc/init.d/bootmisc.sh" and add your new commands near the bottom.

Hope this helps,

Dave Mac

---

