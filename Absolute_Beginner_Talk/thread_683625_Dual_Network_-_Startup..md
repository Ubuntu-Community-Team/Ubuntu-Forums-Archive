---
title: "Dual Network - Startup."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Broads on 2008-01-31
Total newb here,  I have recently installed a version of myth buntu,  which apears to be a more cut down specific version of ubuntu.

After installing some of the goodies back into the system I have a few more things to tweak before I am happy.  So if anyone can answer these questions.

I have 2 network cards in my pc,  One that the internet comes in on and a second that my network goes out on to my xbox's.   In the network manager on boot only my 2 network card is checked, every time I boot I need to enable my first network card.  How do I go about fixing this.

Once this is fixed,  I will also need to share my internet connection across the 2nd network card,  how do I go about doing this.


I presume,  I should also install a firewall and virus protection,  any ideas or suggestions into the software to use.

I also want to install freevo,  this came down from the site as a gzip image,  how do I go about extracting and installing?

Finally.  I will need to share my files from my NTFS partition across the network,  UPNP style.   Is there a program that can do this like mp11.

I think thats it for the moment,  I'm slowly coming around to ubuntu but it doesnt seem so easy as windows atm.  Im sure with time I will grow to understand ubuntu and i'm not giving up just yet.


Thanks for any assistance given.

---

### Post by emarkd on 2008-01-31
I can't help with your network issue, but I can hit a few of those others.

1.  You should know that MythBuntu is built on Xubuntu, so you'll want information specific to Xubuntu where it differs from Ubuntu.

2.  Firewall is installed by default.  It's called iptables and all ports are closed on a new install.  You don't need virus protection.  Linux can't be infected by Windows viruses and there have only been a few Linux viruses over the years and they don't get far.  There are no known Linux viruses in the wild now. 

3.  See this for installing tarballs in linux:  [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

Welcome to the community.  I hope you find what you need.

---

### Post by seventhc on 2008-01-31
Shouldn't you be using a router? I don't have any game consoles:( so not sure how they go but I would think a router would be the way to connect them.
correct me if I'm wrong anybody.

---

### Post by Broads on 2008-01-31
Thanks for posts so far.  

Im guessing then that since the firewall is not letting anything in then that is what i need to fix to get the network to my xboxs working.
 
I am   thinking of getting a router eventually,  but I started with 2 network cards on my windows environment and havent had any issues,  apart from having to have my pc on when gaming online,  but mp3 playback etc, needs the pc to be on anyway so I didnt bother.

Xbuntu?  ok,  I'll have to look that up.. told you i'm a total nube.

Chears.

---

### Post by emarkd on 2008-01-31
Don't worry about being a nube.  We all were at some time or other.  

If you need to open ports on your firewall, I recommend installing Firestarter.  It's a GUI interface to iptables, which is text-based only.  Firestarter is in the repositories.  Just click System > Administration > Synaptic and search for it.

Your network deal should work if you find the information you need to set it up.

---

