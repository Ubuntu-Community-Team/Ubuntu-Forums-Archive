---
title: "Newbie Here.. Looking for install advice"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-03-16
Hello all, I just got done playing with the LiveCD version and was throughly impressed with just the speed alone, I'm sure the only thing holding it back is the read speed of my CD drive with that being said I'm downloading the HD installer right now. One the things I was really impressed with was how it recognized my wireless keyboard and mouse with no problem. It's a MS product and even XP had problems installing the drivers for it.:mrgreen: 

I read through a tutorial on dual booting XP and Linux. I have a couple of questions. I'm thinking of just wiping my whole HD, it's about time to do the Windows dance (format & reinstall) again anyhow. :) I'll say up front I'm not very experinced with partitioning, so here goes a few questions. 

First off. Should I install XP first than Ubantu or vice versa? I'm pretty sure once I get used to Ubantu I'll be using it more than XP. 

Secondly, How would I choose which OS to boot into once both are installed?

I have an 80 GB HD. I was wondering should I create a seperate partition for all my documents, pictures, music etc? Basically I want XP and Ubantu to be able to read and write files. For instance I'd like to be able to edit OO files in both XP and U and play my MP3s in both OS

That's pretty much it for now. Luckily I have a laptop which I'll be able to get online with I completely fudge up me desktop. :D 

Thank you advance for your help, 

Dan

---

### Post by gord on 2006-03-16
you should install XP before ubuntu, that way when you install ubuntu it will install GRUB, which allows you to select which os to boot into when you start up your computer (if you install xp after ubuntu, it will overwrite grub). 

ubuntu can read but not write ntfs, so if you want to be able to access your xp partition from ubuntu, you'll need to install xp to a fat32 partition instead of ntfs. both xp and ubuntu can read/write fat32 drives so if you create a seperate partition for your mp3 files or what not in fat32, you'll be able to access them just fine. allthough you lose the advantages of using ext3 (which is what ubuntu by default uses) such as not needing to defragmentate it. there is a driver for windows [here](http://www.fs-driver.org/index.html) that will let you access ext2/3 drives from windows, allthough i can't comment on its stability

---

### Post by m.musashi on 2006-03-16
If you are thinking of doing a new windows install anyway, I'd leave it for now and install ubuntu. It will recognize XP and set up a dual boot for you. Almost automatic but be sure to read the screens. You can also use the ubuntu install to partition your drive. Since you are willing to reformat anyway, not doing so yet will give you a chance to see what happens. That way if you do goof up it's no biggy. Once you get the hang of it you can then reformat the whole drive and install XP first and then ubuntu.

Hope that helps.

EDIT: [This](http://users.bigpond.net.au/hermanzone/) is a pretty good all around dual boot guide. It discusses using a third partition for XP and Ubuntu swap space.

---

### Post by Danny Boy on 2006-03-16
I'm writing this from Firefox in Ubuntu. :D I decided to take musashi's advice and just install ubantu first before I did a format and reinstall of windows. 

The install went really fast, It was nice to have Firefox, OO and Gaim preinstalled for me. 

The only thing that gets me is my network connection is pretty slow. It takes a long time to find a website and even transfering between the laptop and desktop has been a lot slower than with windows. Any suggest how to fix that?

For some reason I cannot see the Windows partition from Ubantu. I went into system > Admin > Disks and enabled the first partition it still won't let me view it.

---

### Post by m.musashi on 2006-03-16
I'm still pretty new to all this too but I have a couple ideas regarding your problems. The first thing I think of when someone says their network is slow is DNS problems. A really good way to check that is to try to ping a website by name (i.e [www.google.com](www.google.com)) and by IP address. From a terminal type
```
ping www.google.com
```
It should look something like this
```
jim@ubuntu:~$ ping www.google.com
PING www.l.google.com (72.14.203.99) 56(84) bytes of data.
64 bytes from 72.14.203.99: icmp_seq=1 ttl=243 time=80.2 ms
64 bytes from 72.14.203.99: icmp_seq=2 ttl=243 time=81.2 ms
64 bytes from 72.14.203.99: icmp_seq=3 ttl=243 time=68.8 ms
```
Hit ctrl-c to stop it.
Then try pinging by IP address.
```
ping 72.14.203.99 (but use the IP address you have from the previous ping)
```
It should look something like this
```
jim@ubuntu:~$ ping 72.14.203.99
PING 72.14.203.99 (72.14.203.99) 56(84) bytes of data.
64 bytes from 72.14.203.99: icmp_seq=1 ttl=243 time=71.6 ms
64 bytes from 72.14.203.99: icmp_seq=2 ttl=243 time=73.0 ms
64 bytes from 72.14.203.99: icmp_seq=3 ttl=243 time=69.6 ms
```
The times should look similar. If your times on the [www.google.com](www.google.com) ping are a lot slower than the IP ping then it's probably a DNS problem. The fix usually involves letting ubuntu know what DNS server to use. I'll have to investigate a bit on that as I don't remember. Maybe someone else can help here. First, let us know what happens.

As for the reading of NTFS or other partitions you will need to set that up. The easiest tool I've found is [Diskmounter](https://wiki.ubuntu.com/AutomaticallyMountPartitions).

Good luck.

---

### Post by jimrz on 2006-03-16
Welcome,

   You will first need to properly mount your win partition. Look at [**_[COLOR="Sienna"]this[/COLOR]_**]("http://www.ubuntuguide.org/#automountntfs") for 'how to'. Be sure to do the u-mount thing first (may be a bit up the page from the ntfs mounting) and after mounting scroll down to the area that shows how to make it auto-mount whenever you spin it up.

---

### Post by Danny Boy on 2006-03-16
Thanks for the help guys, I'm in the middle of letting XP format the hard drive once XP installs I'll reinstall Ubuntu. 

What I noticed is once Firefox connects to a site it tends to go pretty fast. For instance, when first trying to get to ubuntuforums.org it takes a minute or two but after I get to the site viewing threads is normal speed. I don't think it's a FF problem because even when I was downloading Ubuntu updates it took a while to actually "find" the server once it found it everything was full speed. 

I tried installing a few programs, I couldn't get anything to install. I even followed the wiki for Firefox 1.5, for what ever reason it just wouldn't work. When I downloaded Opera it kept telling me that the archive was invalid even though I selected the correct U version from operas site. 

So far I'm 0 for 2, but once I get some of the basic commands down I think I'll be oaky.

---

### Post by m.musashi on 2006-03-16
Yeah, have fun with the XP. That is one lenghly install process and then all the updates. I think it took me about an hour to do service pack 2 and everything needed before you can even do that. I was shocked when I first installed ubuntu and it formatted the drive in about 10 seconds and the whole install was only 20 minutes or so including all the Oo.o and gimp stuff, etc.

Do the ping thing when you get installed again. It still sounds like a DNS problem to me. I had the same problem.

When you get installed you might want to have a look at [Automatix](http://ubuntuforums.org/showthread.php?t=138405) for help in adding FF 1.5, opera and a bunch of other useful stuff. It worked well for me. Of course if you like messing with the install piece then that's cool too.

EDIT btw, Automatix is currently only for Breezy. You can't use it on Dapper yet but it sounds like you are installing Breezy anyway so probably not a problem

---

### Post by Mustard on 2006-03-16
A slow connection could mean a problem with the ipv6 protocol not being recognised by your ISP/router.  There are a number of threads on disabling ipv6 in the forums.  I would try using the search function to find instructions on how to disable it.

-edit-

Just did a search myself. :)

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by m.musashi on 2006-03-17
ipv6 could be the problem too. There is another thread that has 2 or 3 methods for fixing network problems. I'll have to look for it. Without more info it's hard to pin down but ipv6 or DNS are good bets.

EDIT Found it. Check [this thread](http://www.ubuntuforums.org/showthread.php?t=78337). Look at post #4. This [wired ethernet troubleshooting guide](http://ubuntuforums.org/showthread.php?t=87643) also looks useful.

---

### Post by Danny Boy on 2006-03-17
Thanks for the advice guys, I have gotten XP reinstalled and U. For some reason even though I told U to only partition 20 GB it took 68 and left windows 10. It's not that big of a deal anyway, as once I get used to U I'll probably leave Window's all together. 

I tried the IPv6 thing it didn't work out for me, still very slow connecting to a server. 

Then I screwed up something I was trying to get my XP laptop to realize that my desktop still exsists on the network even though it's running Linux. I changed the domain name in Network Configuration it told me to log off. Now, every time I log back in it tells me that GNOME may not run correctly and I should edit etc/hosts. That file is empty so I have no clue what to do, and half of the things in Admininstration tools won't load, I click on it, it tells me its starting then it kills the process. Maybe a reinstall of U? 

Automatix is awesome, I installed a bunch of stuff. It told me it installed Frostwire but nothing is in the menus.

---

### Post by Mustard on 2006-03-17
[QUOTE=Danny Boy]Thanks for the advice guys, I have gotten XP reinstalled and U. For some reason even though I told U to only partition 20 GB it took 68 and left windows 10. It's not that big of a deal anyway, as once I get used to U I'll probably leave Window's all together. 

I tried the IPv6 thing it didn't work out for me, still very slow connecting to a server. 

Then I screwed up something I was trying to get my XP laptop to realize that my desktop still exsists on the network even though it's running Linux. I changed the domain name in Network Configuration it told me to log off. Now, every time I log back in it tells me that GNOME may not run correctly and I should edit etc/hosts. That file is empty so I have no clue what to do, and half of the things in Admininstration tools won't load, I click on it, it tells me its starting then it kills the process. Maybe a reinstall of U? 

Automatix is awesome, I installed a bunch of stuff. It told me it installed Frostwire but nothing is in the menus.[/QUOTE]

I'll just copy and paste a little guide I have written up about editing the /etc/hosts for another common problem that people get into, it should give you some idea of how to proceed....

HowToEditEtcHostsCreated Friday 20/01/2006 10:34

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

```
nano /etc/hosts 
```

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname #returns the current hostname
hostname <hostname>  #sets the hostname according to the value entered for <hostname>
```

---

### Post by Danny Boy on 2006-03-17
Thanks Mustard! I'm going to print that out and try it. 

You guys are great on this forum, very patient with newbies! :KS

---

