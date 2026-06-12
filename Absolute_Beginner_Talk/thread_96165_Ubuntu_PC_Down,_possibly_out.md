---
title: "Ubuntu PC Down, possibly out"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Stormspace on 2005-11-28
I shutdown my box on Tuesday and left town. When I returned on Sunday it booted without issue and I saw that a reply had been made regarding netbios on Ubuntu. I made the configuration change to the nsswitch.conf file and rebooted. Afterwards I was unable to sudo anything without getting a hostnotfound message of sorts. I dug around a little and each of the messages here pointed at the hosts file. I looked at it and there were no problems, so I did nothing to it. (Not that I could, since I only had read access.) 

Thinking that perhaps the issue revolved around the change I made to the nss file, I did a ctrl-alt-F1 and su'ed to root access(I had the foresight to set that up, otherwise I'd be completely hosed.) I used vi to restore the host line in the nss file and rebooted. 

This time I got a series of services on start that wouldn't load followed by a message to use ctrl-D or enter the root password. Since Ubuntu doesn't set up a root account this is likely something that needs to be changed, but since I already had a root account configured I did that and ran the suggested program, fschk (I think) It was something like that and it appeared to be a command line version of scandisk that prompted me to fix several things. I answered yes to each since it was the default answer and let it rip. 

Now, I cannot get the PC to boot to X at all. I keep getting the ctrl-D message each time, even a switch to root and manual attempt to startx fails. This certainly is cryptic and doesn't inspire confidence. If anyone knows of an easy fix by all means let me know. Perhaps some type of repair installation or something? At any rate, I've spent close to 40 hours getting the PC running and trying out things with now problems only to have this happen when I edited a text file. It's rather discouraging.

---

### Post by aysiu on 2005-11-28
No luck with ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by Mustard on 2005-11-28
Its not a bad description of your problem, but I think for troubleshooting purposes what you need to provide is the actual error messages you are receiving.  These are the clues that most people use to troubleshoot specific issues.

-edit-

One thing that puzzles me is that fsck cannot (or shouldnt) be run on a mounted partition.  A warning message to that effect is given when you attempt to do so.  Normally a liveCD would be used to run fsck on the umounted partitions.

-edit2-

I'd be curious what the contents of your /etc/hosts and /etc/hostname files are.

---

### Post by Stormspace on 2005-11-28
[QUOTE=aysiu]No luck with ```
sudo dpkg-reconfigure xserver-xorg
```?[/QUOTE]

None of the sudo commands function.

---

### Post by Stormspace on 2005-11-28
[QUOTE=Mustard]Its not a bad description of your problem, but I think for troubleshooting purposes what you need to provide is the actual error messages you are receiving.  These are the clues that most people use to troubleshoot specific issues.

-edit-

One thing that puzzles me is that fsck cannot (or shouldnt) be run on a mounted partition.  A warning message to that effect is given when you attempt to do so.  Normally a liveCD would be used to run fsck on the umounted partitions.

-edit2-

I'd be curious what the contents of your /etc/hosts and /etc/hostname files are.[/QUOTE]

I would have loved to give you some verbatim error messages, but the machine is at home and I'm at work. I do have a second machine I can post from once I'm there, but it'll be after 6:00 EST before I will even be in the vicinity of that box. :)

My hosts file has the standard localdomain.localhost localhost ubuntu as the first line and then several entries for machines on my network. This file has remained unchanged for over a week and no issues with sudo. Thus the reason I did not change it.

I haven't even looked at the hostname file, so unless something else made a change to it, it is sitting in a default configuration.

---

### Post by Stormspace on 2005-11-28
I ran fsck again and finnally got it to come up into X, however I get a message. 

> Could not look up internet address for ubuntu. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts

```

/etc/hosts
127.0.0.1 localhost.localdomain localhost ubuntu

192.168.1.103 	tivoserver
192.168.1.109	marg 		
192.168.1.111	mccalll		
192.168.1.113	DOO		
192.168.1.117	zack		
192.168.1.200	printer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hostname
ubuntu

```

---

### Post by Stormspace on 2005-11-29
Bump.

---

### Post by Stormspace on 2005-12-01
I was able to fix it. I edited my nsswitch.conf file changing this line

```
host: 		files dns 
```

to this

```
hosts: 		files dns 
```

---

