---
title: "What is UDP port &amp; hardware address of my network card??"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by elijahclarity on 2006-10-18
I'm trying to get online in Ubuntu.
In Windows, I'm using this 240nline client from Cyberoam (cable internet). 
In Ubuntu, I'm using its open-source alternative, Linc.
[http://linc.sourceforge.net/](http://linc.sourceforge.net/)

To set up my internet connection successfully, I need to know "the UDP port on which the Cyberoam / 24online server listens" and my "network card's hardware address". Plz tell me how to find this out in Windows. Is the MAC address of my ethernet card the hardware address?

I need this info to set up the configuration file which Linc uses.

I've tried all other ways of getting online...theres no other way. This page here was very helpful...I surely LOVE the way Linux users help others!
[http://beans.seartipy.com/2005/12/30/gnulinux-users-vs-rest-of-the-world/](http://beans.seartipy.com/2005/12/30/gnulinux-users-vs-rest-of-the-world/)

Thanks for your help. Plz reply asap.

---

### Post by David_T on 2006-10-18
Well, you can find your network card's hardware or MAC address in windows by typing ipconfig, or in linux by typing ifconfig.  Guessing that your network card is eth0, you would probably just type ifconfig eth0.  It will be listed as ``HWaddr''.

---

### Post by bswilson on 2006-10-18
> **elijahclarity said:**
> I need to know "the UDP port on which the Cyberoam / 24online server listens" and my "network card's hardware address". Plz tell me how to find this out in Windows.  I need this info to set up the configuration file which Linc uses.

[SIZE="4"]1. The UDP port on which the Cyberoam/24online server listens[/SIZE]

I believe you said you were using **linc**.  The port you want is to be added to  the file called **/etc/lincrc ~/.lincrc**.  Just open that file and find where it says **srvport** (refernce the [online man page]("http://linc.sourceforge.net/lincrc.5.php")).  That's where you'll put the port number.

To find this in Windows, you need to open a Command Prompt, and type the command:

```
netstat -ao |find "LISTENING"
```

This command will show you all listening UDP ports along with the process name.  I think you'll be able to figure out which one the Cyberoam/24online program is...

[SIZE="4"]2. You network card's hardware address[/SIZE]

This is also known as your adapter's MAC (media access control) address.  To find out what yours is, you need run this command in Windows:

```
ipconfig /all |find "Physical"
```

Note that if your system (like mine) has more than 1 Ethernet card, you'll have to ensure you pick the right one.  Just run **ipconfig /all** by itself to see all the details for all cards on your machine, that might help.

---

### Post by x64Jimbo on 2006-10-18
[edit]Beaten! Argh![/edit]
adding the "/all" argument to the ipconfig command like this: 
ipconfig /all 
will be necessary in windows to get the MAC address to display. As for the port, typing "netstat" in the windows console should tell you what ports are in use by which processes.

---

### Post by JayTee on 2006-10-18
Cyberroam listens on UDP port 6060. If you're using Cyberroam be aware that it pretty much blocks most of your IP ports and disables ICMP. You probably won't get things like bittorrent to work or other p2p stuff and if you have any kind of ISP alternative you'd be better off checking that out.

---

### Post by elijahclarity on 2006-10-19
Thanks for all the help all of you. But I haven't been able to find out exactly what port Cyberoam listens to. I've followed Jaytree's advice that it listens on port 6060 but I still don't seem to be getting it to work. I found out the hardware address.

Nevertheless I think this is a wonderful community that I got help so soon:) I'm glad I use Ubuntu!

---

### Post by JayTee on 2006-10-20
If it's not listening on port 6060 maybe your ISP is using another port other than the default. If you need to find this on your computer running Ubuntu and you use Gnome not KDE go to System/Administation/Network Tools and click on the Netstat tab. Click the radio button that says Active Network Services and then click the Netstat button. This will show you all the TCP and UDP ports that have active services listening. If you have it working on your Windows computer you can use the netstat -ao|find "LISTENING" that bswilson mentioned in one of the previous posts. That should give you the port info you need to configure it.

---

