---
title: "IPtables for Samba and Synergy"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Tim Dub on 2006-03-31
Good morning, all. Me again. I've run into my first Breezy brick wall. I picked up an older PC from a coworker to use as both a file server and a web-browsing station. I don't plan on using that PC's Win98 install because (surprise) I needed 50 different freakin' files--the disks of which I didn't have--to configure the NIC. Regular Breezy installed on it just fine (didn't dig Xubuntu too much), recognized the NIC instantly, and I've since tried to install Synergy to allow me to control the Server from my Original PC.

No luck. The PCs can't even Ping each other. ](*,) 

I figured installing Samba on each machine should force these two PCs to play nice. I created a folder on each called "sharetest" with a text file named "sharetest" in each and shared each one out to the network with the share name "sharetest."

No luck. XP can "see" my server's "sharetest" just fine in My Network Places, but I can't connect to it. :confused: 

To give you an idea of what I'm working with, here's all you should need to know.

Four-port ethernet hub
Port 1 - DSL adapter
Port 2 - Dual-booted original PC, hostname "ubuntu"
Port 3 - Intended server PC, hostname "ubuntu2"
Samba workgroup on each is "MSHOME"
IP address granted by DCHP
IP addresses for each seem to be consistanly the same, according to Ifconfig.

Attempting to read up on how to configure IPtables gives me a headache instead of answers, and I cannot use Firestarter except as a content-blocker for the 10-year-old in the house ([see this thread here]("http://ubuntuforums.org/showthread.php?t=146435")), because Firestarter when running insists on blocking legitimate traffic both out to and back in from webservers I'm trying to access (for example, this very forum), no matter how many times I've clicked "allow connections" and "allow service" for this and that and even added the problem sites to the whitelist. It doesn't work.

All I need to know how to do is configure IPtables to allow all connections, on all ports, from a certain internal IP range (192.168.0.1 all the way up). I'm sure this is something ridiculously obvious, probably two lines in the terminal or some file to edit, but I'm not grasping it here, and search on both this forum and Google yield nothing.

If it *isn't* ridiculously obvious, it *should* be. I thought Ubuntu was supposed to "just work," and I don't want to have to go back to WinCrashXP because of what should be a very simple thing. :mad: 

Sorry for the rant, folks. It's been a long night. Can anyone please help?

~Tim

---

