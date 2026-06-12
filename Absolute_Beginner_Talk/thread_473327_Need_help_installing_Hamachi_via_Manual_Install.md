---
title: "Need help installing Hamachi via Manual Install"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-13
I downloaded Linux version of Hamachi and to install it, thre readme file had the following instructions.  Is "run" the equivalent of double clicking on the file.  I have been using synaptic to install and don't know where to put programs and files if ZI have to do a manual install.

Run 'make install' and then 'tuncfg' from under the root account

	Run 'hamachi-init' to generate crypto identity (any account).

	Run 'hamachi start' to launch Hamachi daemon.

	Run 'hamachi login' to put the daemon online and to create an account.

	Run 'hamachi join <network>' to join the network.

	Run 'hamachi go-online <network>' to go online in the network.

	Run 'hamachi list' to list network members and their status.



**Then the following is written:**

Installation

	Hamachi Linux client comes as a single executable binary (hamachi)
	compiled for the platform of your choice. This binary includes the 
	daemon, the control application and the setup utility.

	To install hamachi in /usr/bin run the following command from under
	the root account

		make install

	Once installed you must run 'tuncfg' daemon with root privileges -

		sudo /sbin/tuncfg

	or if you don't have sudo -

		su - ; /sbin/tuncfg; exit

What dos all of this mean?

Thanks in advance,

VC

---

### Post by videocheez on 2007-06-14
I could really use a little bit of help manually installing a couple of files.  I hate to be a noob pest but that's what I am for now.  Why cant I extract files to the bin folder?

Thx,,
vc

---

### Post by videocheez on 2007-06-14
Anybody have an Idea how to manual install Hamachi?  I do not have permission to move files to /user/bin.  Why is that?

---

### Post by inque_54 on 2007-06-15
Me too I kinda need some help installing hamachi the manual way 8(

---

### Post by inque_54 on 2007-06-15
[http://ubuntuforums.org/showthread.php?t=253934&highlight=ghamachi](http://ubuntuforums.org/showthread.php?t=253934&highlight=ghamachi)

A good how-to, but I didn't opt to go for Ghamachi, wouldn't want to work, just used the command lines and it worked perfectly.

---

