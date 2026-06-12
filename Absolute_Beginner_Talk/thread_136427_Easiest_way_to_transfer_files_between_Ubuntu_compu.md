---
title: "Easiest way to transfer files between Ubuntu computers?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by balaram on 2006-02-25
I have Ubuntu installed on four computers in my home. I want to transfer files between these computers. I WON'T be using Windows, only Ubuntu. All four computers are connected to a router that is connected to a DSL modem. What is the SIMPLEST way to do this?

---

### Post by Sandlst on 2006-02-25
I have no experience whatsoever in doing this, but Ive read that using NFS is the way to go when sharing files between linux computers-there is a guide on getting this set up [https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29]("https://wiki.ubuntu.com/NFSServerHowTo?highlight=%28nfs%29") 
and if you have any problems you could just search the forums for 'nfs' 
good luck!

---

### Post by abhaysahai on 2006-02-26
The simplest, according to me, would be to install FTP server on all machines 
and use ftp client to transfer files. 
NFS is not so easy to setup, but once setup properly it is very easy to use. I on my part use the standard ftp client.

---

### Post by xhie on 2006-02-26
I just have one ftp server on one system and go from there. But with me thats all I need for the stuff I do, if its alot of files being transfered all the time between all the systems then I guess the NFS route would be worth going.

---

### Post by rharris on 2006-02-26
You might want to check out SSH, good wiki at the following link:

[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

Its what I use here and it works well with Nautilus.

Take care............

Rob

---

### Post by SickTwist on 2006-02-26
netcat is fast and requires no setup. However, I wouldn't use it for more than the occasional transfer since it requires that you initiate the transfer on both ends.

Check out this [article about netcat]("http://www.linux.com/article.pl?sid=05/11/07/182200") to find out how to use it.

---

### Post by torf on 2006-02-26
If you just need a solution to do simple transfers, and don't mind getting up, you could always use netcat, the "TCP/IP swiss army knife." You can find this in Synaptic, or just do a "sudo apt-get install netcat".  I find netcat to be handy because not all of my computers on my network are all running Ubuntu, and some of the ones that are lack the GUI.

Let's say you have two computers: 192.168.0.4 (The one containing the file you want) and 192.168.0.5 (The one you want to put the file on to).

On 192.168.0.4 enter the directory containing the file type:
```
cat yourfile | nc -l -p 12345
```
This basically just outputs every thing in the file, and pipes it to netcat, which is set to listen (-l) on port 12345 (-p 12345).

On the 192.168.0.5, you can run this command to grab the file:
```
nc 192.168.0.4 12345 > myfile
```
This connects to the computer that is "spitting out" the file so to speak, and outputs it to a file called "myfile"

Keep in mind that this program is just a TCP/IP tool, it's not a smart transfer utility, so it won't know when your file is done.  So before you transfer it, check the filesize.  When you see the network activity on either end stop, check the received filesize, which should match, and hit ctrl-C on either end to stop netcat and connection.  Although it's a simple, quick and dirty solution, it can be cleaned up quite a bit with a little shell scripting.  Keep in mind that this is definately not a secure method.  (you could use a variation called cryptcat, but you might as well get into ssh.) Oh well, it may not apply to your situation after all, but I hope someone will find it handy. :)

---

### Post by celloandy on 2006-02-26
I second the plug for ssh.  This takes almost no effort, and is *much* easier than dealing with an ftp server, with the added benefit of security.  Just install the OpenSSH server with apt, and you'll be good to go.  You can then access it from other computers using Nautilus using an address like "sftp://username@hostname/home/username" or whatever, and you'll be good to go.  You may have to install an extra extension or something to Nautilus to do this, but I don't think so, and if you do, it's in apt.

Andrew

---

### Post by munga_bill on 2006-02-26
Third plug for SSH, it's the best, it's secure, and it's the simplest to set up and use. Try it [Herman's way]("http://users.bigpond.net.au/hermanzone/p11.htm"), that's the easiest.

---

### Post by aysiu on 2006-02-26
What about sharing between Kubuntu computers?

I installed OpenSSH-Server and SSH on one Kubuntu, but when I try to navigate graphically through Konqueror, I just get a terminal up.

I love the terminal (*scp* can be cool, but sometimes I just like to browse through Konqueror. Any ideas?

---

### Post by patrick295767 on 2006-02-26
[QUOTE=aysiu]What about sharing between Kubuntu computers?

I installed OpenSSH-Server and SSH on one Kubuntu, but when I try to navigate graphically through Konqueror, I just get a terminal up.

I love the terminal (*scp* can be cool, but sometimes I just like to browse through Konqueror. Any ideas?[/QUOTE]
  
You can install : 
```
apt-get -f install proftpd
```
to have a ftp server
and taht's it : u can log via gftp to the pc with ftp server
(enter the ip address)
(ifconfig         to know them)  

 
or 

You can use the nfs & shaing one folder on 1 pc:
you have to check the exports, hosts.allow, hosts.deny ...
and then on the distant pc, use :
```
mkdir /mnt/folderonserver
mount -t nfs IP_address_ofdata_shared:/mnt/sharedfolder /mnt/folderonserver
```
  
Or last possibility: 
the one i have : 
I have a big big tower that is a Linux server
then all pc are having their /home in a big harddisk
no problem with sharing data
cos you'll be exactly with the same data and everthg on any PC 
taht's LInux , that's why we like it so much
it's like workstations ;-)
(you have to use in /etc/fstab: IP_address:/mnt/hda1/home	/home	nfs	rsize=8192,wsize=8192,timeo=14,intr) ...
  
Greetings

Pat'

---

### Post by aysiu on 2006-02-26
Thanks, Pat.

I'll keep that for reference (it sounds a bit complicated) and get used to *scp* for now. When I feel more daring, I might try one of those. Thanks again.

---

### Post by balaram on 2006-02-26
I used the openSSH Server method it worked  
like a charm. I also followed the link to Herman's Way which made it even easier. Thanks for all the help.

---

### Post by nocturn on 2006-02-27
[QUOTE=aysiu]What about sharing between Kubuntu computers?

I installed OpenSSH-Server and SSH on one Kubuntu, but when I try to navigate graphically through Konqueror, I just get a terminal up.

I love the terminal (*scp* can be cool, but sometimes I just like to browse through Konqueror. Any ideas?[/QUOTE]

KDE has an SCP ioslave.  I thought it was called fish (in KDE 3.3)

---

### Post by colo on 2006-02-27
Konqueror should, afaik, support ssh2-sftp via the fish://-KIOslave. You may want to take a look at gftp (graphical) and lftp (CLI) for accessing sftp by other means. The sftp-client shipped with openssh is PITA, but a nice fallback to have, and still much better than scp for interactive use.

---

