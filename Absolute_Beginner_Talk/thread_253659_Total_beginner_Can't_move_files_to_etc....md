---
title: "Total beginner: Can't move files to /etc/..."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-09-08
Hello,

I am totally new to Ubuntu and hope someone can help me out. I just downloaded Ubuntu-firewall and the readme file and says the script for the program should be placed in the etc/init.d directory. When I try to do this I goet a pop-up message telling me I do not have permission to paste a file there. Is there something I'm doing wrong or is there some way to turn off this blockage to this important /etc/  folder?

Hope to hear from someone soon, I really do appreciate it.

Andrew

---

### Post by TyphoonJoe on 2006-09-08
You don't have permission to put files there, so you need to use sudo.

Open a terminal and run:
```
sudo cp /path/to/source/filename /path/to/destination/filename
```

I think you could also launch nautilus with escalated privledges (root)  by running this from a command prompt:
```
gksudo nautilus
```

*Rule of thumb is to use sudo for running things "as root" on the command line and gksudo for launchign graphical applications as root.  
*Also read this helpful stick about root and sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by s6dalane on 2006-09-08
You need to copy the file/directory using sudo.
Open the terminal and type:

> sudo mv <name>

---

### Post by jISh on 2006-09-08
For the record, why not use Firestarter? Ubuntu already has a firewall installed (iptables) and Firestarter is a GUI frontend to configure it. 
sudo apt-get install firestarter

---

### Post by andrew222 on 2006-09-08
Thank you all, I'll try these out and get back to you about how I made out.

Andrew

---

### Post by andrew222 on 2006-09-08
I copied the folders sucessfully! Then I used the scripts necessary to install ubuntu-firewall and it worked like a charmI used the sudo cp command. I will study the sudo mv command as well for future use. 

BTW, how would I get a MP3 decoder for Totem 1.4.3?

Thanks again,

Andrew

---

### Post by AirRaven on 2006-09-08
> **andrew222 said:**
> BTW, how would I get a MP3 decoder for Totem 1.4.3?


The easiest method I can suggest is to use Automatix.

To install it, follow the guide for Ubuntu Dapper 6.06 [here](http://www.getautomatix.com/wiki/index.php?title=Installation), then choose to install a codecs package.

Brilliant tool- it'll get you up and running in no time.

For the record, I reccomend MPlayer and VLC for videos and "Banshee" or "Rhythmbox" for music- you might find them more to your liking than Totem.

---

### Post by andrew222 on 2006-09-08
Thank you very much Air Raven, I'll check it out :-)

Andrew

---

