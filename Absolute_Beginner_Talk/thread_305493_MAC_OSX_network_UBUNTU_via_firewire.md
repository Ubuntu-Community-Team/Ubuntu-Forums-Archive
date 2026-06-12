---
title: "MAC OSX network UBUNTU via firewire"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by lioninwinter on 2006-11-23
Hi,

I am trying to connect my ubuntu PC to my mac with OS X via firewire cable. My mac connects to the internet through a cable modem. Is it possible to have the ubuntu PC connect directly to the mac with a firewire cable so that it may use its printers, the internet, and share files? If so, where can I learn more about doing this? I am new to ubuntu, and have a very basic understanding of networking so most of the help in the forums is beyond my grasp. If a walkthrough does not exist (I could not find one) I am more than willing to educate myself, I just don't know where to start.

---

### Post by lioninwinter on 2006-12-02
Since it seems no one knows about this or is willing to help, I went out and learned what I needed to make this work. Here is how:

In the MAC

1. Open System Preferences from the apple menu
2. Click on Network and select Built-in Firewire from show menu
3. Select Configure  IPv4 Manually from pull down menu and type 192.168.0.1 for IP address and 255.255.255.0 for Subnet mask
4. Click Apply now
5. Click Show all to go back to system preferences
6. Click sharing and turn on Windows sharing

In Ubuntu BOX

1. Open Applications>Accesories>Terminal and type this

sudo modprobe eth1934

2. Open Syste>Administration>Networking and disable eth0

3. Click on eth1 and click properties. Choose Static IP address from pull-down menu, then type 192.168.02 for ip address and 255.255.255.0 for submask and click ok.
4. Open System>Administration>Networking Tools and click the ping tab
5. In the network address type 192.168.0.1 and click the ping button. If you get packet loss 100% something did not work. If you get a response back your computers are seeing each other (almost there!!)
6. Open Places>Connect to Server... from main menu and select Windows share from service type
7. Type 192.168.0.1 under server
8. Type the name you use to log in for your mac
9. Give any name you like for this connection (i.e. MAC, My MAC, or whatever)
10. Click connect
11. You will see a new icon on the desktop with the name of the connection you just created. Double click it and enter the password you use to log in to your mac (remember it is caps sensitive).

You should see the contents of your mac and be able to copy files to the Ubuntu Box.


I am still working on:

Changing privilege setting so you can write files on the mac
Allowing the mac to look at Ubuntu Box and modify files (should be easy)
Connecting my Ubuntu Box to the internet through my mac (which is connected through cable).

If anyone can help, I would appreciate it.

---

### Post by fabbaz on 2007-01-29
hey!
this is impressive.
i will get my macbook next week, and am looking for ways to transfer all my data from my ubuntu box.
is it, using your guide, possible to move files to the mac?
thx

-fabbs

---

### Post by punx45 on 2007-01-29
> **lioninwinter said:**
> I am still working on:

Changing privilege setting so you can write files on the mac...

apparently not yet.

if you already have existing LAN hardware available to you then you can simply share Ubuntu directories using NFS.   thats how I rock it.

---

### Post by fabbaz on 2007-02-01
good point. thanks!

---

### Post by punx45 on 2007-02-01
[here is a past discussion]("http://ubuntuforums.org/showthread.php?p=1801795") troubleshooting setting up NFS with mac/ubuntu.  its not a full how-to but may help if you have any questions if you go that route.   it also deals with a specific NFS client for mac.

---

### Post by Xappe on 2007-02-01
This is how I usually connect to and from my ibook:

Connecting from ibook to ubuntu -> SSH and SCP using OSX terminal or Fugu (sftp/scp client)
Connecting to ibook from ubuntu -> SSH/SCP/SFTP (enable the ssh server in OSX)

---

