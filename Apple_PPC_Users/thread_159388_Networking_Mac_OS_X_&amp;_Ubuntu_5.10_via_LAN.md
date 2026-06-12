---
title: "Networking Mac OS X &amp; Ubuntu 5.10 via LAN"
date: 2006-04-12
forum: Apple PPC Users
---

### Post by Sipefree on 2006-04-12
Here's my dilemma: I've got a Mac (Tiger) which is directly connected to my DSL router via ethernet slot 1, and an Ubuntu PC connected to the Mac via ethernet slot 2 (using a different network card).

I've set up Internet Sharing with Mac OS X with System Preferences -> Sharing -> Internet. This lets the Linux box access the web just fine. It can connect out just fine. I can also use SMB to connect to my Mac and view its Shared Folders.

The problem is trying to connect to the Linux box. No matter what I try to do, I can't get it to accept a connection. What I'm trying to achieve is a VNC solution so I can monitor the PC without having to have its monitor on.

I can ping it and get a response, and I can also try and connect via Cmd-K and typing in smb://<address>/path/to/folder, but it complains about an incorrect username or password every time. I tried a port scan on it and all the ports are closed.

The thing is I can't seem to figure out why it won't accept any connections. I installed Firestarter on the Linux box so I could change its firewall settings, and I opened the ports I needed, but every time I try to connect via VNC or even trying to "telnet <address> 5900" I get a Connection refused message.

I wondered whether the problem was with my mac, so I disabled the built-in firewall, but to no avail. The PC still did not accept connections.

I really need to get this problem fixed. The PC can't even connect to GAIM or XChat.

Got any ideas? :confused:

---

### Post by Sipefree on 2006-04-13
I just realized I posted this in the wrong forum.

Could someone move this to the Networking forum?

---

### Post by king_arthur on 2006-04-13
[QUOTE=Sipefree]Here's my dilemma: I've got a Mac (Tiger) which is directly connected to my DSL router via ethernet slot 1, and an Ubuntu PC connected to the Mac via ethernet slot 2 (using a different network card).

I've set up Internet Sharing with Mac OS X with System Preferences -> Sharing -> Internet. This lets the Linux box access the web just fine. It can connect out just fine. I can also use SMB to connect to my Mac and view its Shared Folders.

The problem is trying to connect to the Linux box. No matter what I try to do, I can't get it to accept a connection. What I'm trying to achieve is a VNC solution so I can monitor the PC without having to have its monitor on.

I can ping it and get a response, and I can also try and connect via Cmd-K and typing in smb://<address>/path/to/folder, but it complains about an incorrect username or password every time. I tried a port scan on it and all the ports are closed.

The thing is I can't seem to figure out why it won't accept any connections. I installed Firestarter on the Linux box so I could change its firewall settings, and I opened the ports I needed, but every time I try to connect via VNC or even trying to "telnet <address> 5900" I get a Connection refused message.

I wondered whether the problem was with my mac, so I disabled the built-in firewall, but to no avail. The PC still did not accept connections.

I really need to get this problem fixed. The PC can't even connect to GAIM or XChat.

Got any ideas? :confused:[/QUOTE]
Hello Sipefree,

your problem is a common issue.. :)
First of all you need to "share" a folder in Ubuntu: this is done easily from the menu.

The tricky part is enabling a SMB working user on the Ubuntu box.
Linux users and samba users on the system are basically the same but have different passwords stored in different places.
You must create a password recognized by samba.

Go into terminal and type sudo smbpasswd *yourusername*, you shall be prompted for your usual password first.
Only after that you shall be requested a password for te samba user: you can use the same or a different one.
You will be requested a second time to confirm, that's normal.

That's it, you can now connect from the mac to the Ubuntu/Linux box. :)

/P

---

### Post by Sipefree on 2006-04-13
Did that, got this error:
[img]http://img358.imageshack.us/img358/9489/picture41zw.png[/img]

Also, this does not solve my blocked ports problem. I still can't ssh into the machine or connect via VNC. Interesting thing though, when I checked a port scan this morning I got this result instead of nothing being open:

```
Port Scan has started ...

Port Scanning host: 192.168.2.2

	 Open TCP Port: 	139		netbios-ssn
	 Open TCP Port: 	445		microsoft-ds
Port Scan has completed ...
```

Strange. Thoughts?

---

### Post by king_arthur on 2006-04-13
Not sure what's wrong there.
I have exactly the same setup here (iMac and Linuxbox) and it works just fine with Samba after the few modifications I just mentioned.

As for remote ssh connections, you have to enable this from the preferences in Ubuntu.

Go to the Menubar  System==>Administration==>Login Window and you may find the solution is there.

I am not sure about the names in English as I am on an Italian system but for sure I will check out some time tonight and revert to you.

Good luck

/P

---

### Post by Sipefree on 2006-04-13
I reckon it's got to be a problem with natd on my OS X box. I think it's only allowing outbound connections for HTTP.

I can't find the config file for natd, so I'm stuck.

---

### Post by guidotex on 2006-04-14
sipefree - 
   Sorry, I know that you're not dumb or anything, but the first thing that I would check is to make sure that your VNC server is running and configured correctly on the linux box.  Outside of that, I don't know much about VNC in your situation, but you may be able to get ssh by editing the file "ssh_config" in /etc/ssh.  You'll want to save off a copy first and change the permissions (so if you mess somethin up you can go back).  from a command line, do the following:

sudo cp /etc/ssh/ssh_config /etc/ssh/ssh_config.original
sudo chmod a-w /etc/ssh/ssh_config.original

Then go into the file an uncomment the following lines:
  PasswordAuthentication yes
  Port 22

Also check the file /etc/ssh/sshd_config to make sure that the line 'PubkeyAuthentication yes' is uncommented (if not, make backup and edit, etc)

Then restart the ssh server by using
  sudo /etc/init.d/ssh restart

After this you should be able to open a terminal (or the mac equivalent) and type:
 ssh -l<yourUsername> xxx.xxx.xxx.xxx(ip address of linux box)
This should give you a login prompt.

A good resource is the ubuntu linux server user's manual (you may find something in the chapter on networking):
   [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

Also, make sure that the ssh and VNC clients are both running correctly on your mac.

Good Luck!!

---

### Post by guidotex on 2006-04-14
I found another post by OfficeLinebacker about a similar problem.  He solved it by using the following:
   sudo apt-get install openvpn 

I guess openvpn is a VPN server or something -- maybe google it?

---

### Post by motionsiren on 2006-04-14
[https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679](https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679)

---

### Post by king_arthur on 2006-04-14
[QUOTE=motionsiren][https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679](https://launchpad.net/distros/ubuntu/+source/samba/+bug/23679)[/QUOTE]
Well, this makes sense, as I am using Dapper Drake and that one has the updated version of the Samba server.. :)

/P

**Update**: I have read the thread now. 
To me it looks like a different issue than the one Sipefree is having...

---

### Post by Sipefree on 2006-04-14
[QUOTE=king_arthur]Well, this makes sense, as I am using Dapper Drake and that one has the updated version of the Samba server.. :)

/P

**Update**: I have read the thread now. 
To me it looks like a different issue than the one Sipefree is having...[/QUOTE]

Yeah it is. As far as I can tell the Samba server and VNC server are working properly, the mac just refuses to see the PC.

---

### Post by aethiolas on 2006-04-25
I'm running dapper beta and I'm having the same issue with OSX mounting the smb share(one or ore required items could not be found...).  I had the passwd issue but thats gone away.  Anyone find a solution for this?!?!

---

### Post by st1100pilot on 2006-04-27
Yup, I'm watching this one too. I can see the Linux box from the Mac, but when I click "connect", I get the spinning beach ball, and I have to relaunch finder. I have 150 of beautiful space that I'd love to use as a file server, but I can't access it!

---

### Post by General_Tux on 2006-05-06
[QUOTE=Sipefree]I've set up Internet Sharing with Mac OS X with System Preferences -> Sharing -> Internet. This lets the Linux box access the web just fine.[/QUOTE]

Sorry, I am not able to help, but I have been trying to implement a similar internet sharing system between my PowerBook G4 with OS X 10.4.6 and my Ubuntu desktop, however, I have not had much success. I have internet sharing enabled on my notebook, and the ethernet card on my Ubuntu box (hopefully) set up properly. Any suggestions to how you were able to share the connection would be greatly appreciated. Thanks.

---

### Post by king_arthur on 2006-05-06
Hello Tux,

first of all: can the computers  at least "ping" each other?

And when you say, "not much success" what do you exactly mean?
Networking and file-sharing among different boxes works like a "breeze" :D with the mac.

Often enough, it's not the computers, it's just networking that is **hard** stuff.

/P

---

### Post by General_Tux on 2006-05-07
Well, as of right now, the computers cannot even ping each other, and no data is being recieved on the Ubuntu machine. 

The configuration that I have (currently): I have internet sharing through built-in ethernet enabled, then I access the internet on the PowerBook connected to the Ubuntu machine through a standard cat5 cable directly (as of right now I do not have a router). On the Ubuntu side, I have both of my ethernet cards active and have them set up to use DHCP. 

I am still rather new when it comes to networking, as this is the first project that I have done that required it. Any help would be greatly appreciated. Thanks!

---

### Post by king_arthur on 2006-05-12
[quote=General_Tux]and the ethernet card on my Ubuntu box (hopefully) set up properly.[/quote] 
I suspect that your problem is there. :)
If you can't ping the machines, your internet cards (or cabling) are not setup correctly.
Do you have leds on the card? are they flashing green?
How about the mac-side? what does your network status show up?

On the mac go to System preferences==>Network and check ports status from there.

On the Ubunu-box open a terminal window and type in "ifconfig", what does it show?

/P

---

