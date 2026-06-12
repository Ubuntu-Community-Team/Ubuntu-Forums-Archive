---
title: "Rootkits: How exactly do they happen, and how do I prevent them?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2007-11-25
Right, so I've most definitely been rootkitted, as I logged in to find a number of porn pictures in my home folder that had not been there before. I've read a lot of threads stating that rootkits happen when you have an insecure password, throw sudo around, download stuff you're not sure about . . . I do use sudo a bit much, but not so much that I would've seen this happening, and I only download software via the SPM or the Mozilla website (with the sole exception of Flash, since it doesn't seem to want to work with either of those things). I do download a large number of images (from various places) and music (usually from eSnips), but again, I had been led to believe that that alone shouldn't have seriously undermined my security.

My password is as secure as I can make it (case-sensitive, alphanumeric with special characters, long, and a completely made up word), and I'm behind a firewall on my router (I'm running wirelessly from the router, which is connected to our main computer, which uses Windows XP). All of my ports are apparently secure.

RKhunter returns this:
```
     - /etc/rc.d/rc.local                                     [ Not found ]
     - /usr/local/etc/rc.local                                [ Not found ]
     - /usr/local/etc/rc.d/rc.local                           [ Not found ]
     - /etc/conf.d/local.start                                [ Not found ]
     - /etc/init.d/boot.local                                 [ Not found ]
   Checking rc.d files...                                     [ Not found ]
   Checking history files
     Bourne Shell                                             [ Not Found ]
   Scanning for hidden files...                               [ Warning! ]
---------------
/etc/.pwd.lock
/etc/.java /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools
---------------
Please inspect:  /etc/.java (directory)  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)
   Checking for logging to remote system...                   [ OK (no remote logging) ]
---------------------------- Scan results ----------------------------

MD5 scan
Scanned files: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 0

Scanning took 491 seconds
```

So basically my question is, when I wipe and reinstall, what can I do differently to stop this from happening again? I've heard of hardening the kernel, but I'm not entirely clear on the details.

---

### Post by PeterJS on 2007-11-25
You've got 6 warnings, and of those six I can tell you what most of them are. /etc/.java is put there by java, I'm pretty sure if you look you'll find that folder empty,  /dev/.static is where settings for non-plug and play devices are stored, /dev/.udev is where the udev hotplug manager keeps it's settings, the /dev/.initramfs entries are part of the boot up process that manages loading kernel modules at boot. I also have a /etc/.pwd.lock, it's empty and root read only, so it doesn't seem that out of the ordinary.

You might have to run some other tools, right now it looks like the porn is the only evidence of someone else being there. Is you home dir available from your XP machine? If so It might be the machine that's compromised.

---

### Post by glotz on 2007-11-25
I think you're jumping the gun. Then again, I'm no expert on the subject. There's a million ways of getting rootkitted. One minor slip is all it takes.

---

### Post by Halfling Rogue on 2007-11-25
> **PeterJS said:**
> You've got 6 warnings, and of those six I can tell you what most of them are. /etc/.java is put there by java, I'm pretty sure if you look you'll find that folder empty,  /dev/.static is where settings for non-plug and play devices are stored, /dev/.udev is where the udev hotplug manager keeps it's settings, the /dev/.initramfs entries are part of the boot up process that manages loading kernel modules at boot. I also have a /etc/.pwd.lock, it's empty and root read only, so it doesn't seem that out of the ordinary.

You might have to run some other tools, right now it looks like the porn is the only evidence of someone else being there. Is you home dir available from your XP machine? If so It might be the machine that's compromised.

/etc/.java has something called .systemRootModFile in it. Also, no, none of my directories are available from the XP machine (to the best of my knowledge). I [already dealt with a porn relink virus in this thread]("http://ubuntuforums.org/showthread.php?t=602795"), and since the problem wasn't in my user preferences, the consensus seemed to be that I had been rootkitted. I was a little doubtful then, but getting these images on my home drive just proves it.

---

### Post by Halfling Rogue on 2007-11-25
Bump.

---

### Post by Halfling Rogue on 2007-11-26
Bump.

---

### Post by bodhi.zazen on 2007-11-26
I think .systemRootModFile is a normal file, do a google search for ".systemRootModFile".

Rootkits are not all that complex, they are cracks that give unauthorized root access :

[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

They happen either via bugs or misconfigured servers or any number of cracking techniques, whole books / web sites are devoted to your question.

What to to:

Disconnect your computer from the internet.

Image you hard drive if you are interested in forensics.

Re-install and be very mindful of Security.

---

### Post by The Tronyx on 2007-11-26
I'm pretty sure the general consensus is that if you think you have a rootkit, you need to reinstall.  Rootkits aren't just a backdoor, they compromise the entire system and totally eliminating any backdoors put in place is quite a difficult task.  Since rootkits can be very system specific they work best when home brewed.  Rootkits can also hide processes and modify other essential system processes to keep themselves hidden.  Furthermore, assuming someone wanted to root your system and had the skills to do so, they could easily manipulate your logs only to cover their tracks further.

If your only evidence is some random pornography, my first question would be, who else has physical access to that machine?  It's not likely that someone would want to hack your box just to stash some porn.

You might also want to try:
> 
sudo chkrootkit


One last edit note...

If you really think you have been compromised but don't want to re-install, you should head over to servers and security section and get info on forensics as Bodhi.zazen mentioned.  Assuming you have been hacked you might be able to get evidence pretty easily.  Run Nmap on your localhost, see if there is a netcat port or other port that shouldn't be there.  You could also stop all your internet traffic for a few.  Download a program called Wireshark, it's a protocol analyzer and you should be able to see if there is any traffic that should not be there.  Open wireshark, start recording on your network interface card and while it's recording do not have any programs that use the internet open.  No instant messaging, no IRC, web browsing, etc.

If you need help looking at the logs feel free to send me a private message or leave a follow-up post here.  I'll be sure to check back.

---

### Post by Halfling Rogue on 2007-11-26
The only other person with physical access to my machine is my sister, and she has her own separate account and only uses my laptop when our main computer isn't working (in other words, she hasn't touched it for months). I'll run forensics and see what turns up, but I'll probably reinstall anyway. Thank you so much for all the advice.

---

### Post by Halfling Rogue on 2007-11-26
chkrootkit turned up this:
```
Searching for suspicious files and dirs, it may take a while...
/usr/lib/jvm/java-6-sun-1.6.0.00/.systemPrefs
/usr/lib/jvm/.java-gcj.jinfo
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/firefox/.autoreg
/lib/modules/2.6.15-29-386/volatile/.mounted
```

Other than that, everything was "not infected", "not found", or "nothing found".

Nmap gives me this:
```
halflingrogue@ubuntu:~$ nmap --version-trace localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-26 16:53 PST
--------------- Timing report ---------------
  hostgroups: min 1, max 100000
  rtt-timeouts: init 1000, min 100, max 10000
  msx-scan-delay: TCP 1000, UDP 1000
  parallelism: min 0, max 0
  max-retries: 10, host-timeout: 0
---------------------------------------------
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Hostupdate called for machine 127.0.0.1 state UNKNOWN/COMBO -> HOST_UP (trynum 0 , dotimeadj: yes time: 287)
Finished block: srtt: 430 rttvar: 5000 timeout: 100000 block_tries: 1 up_this_bl ock: 1 down_this_block: 0 group_sz: 1
massping done:  num_hosts: 1  num_responses: 1
mass_rdns: Using DNS server 192.168.1.1
Interesting ports on www.xscincorporated.com (127.0.0.1):
Not shown: 1694 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
25/tcp  open  smtp
631/tcp open  ipp
Final times for host: srtt: 1145 rttvar: 267  to: 100000

Nmap finished: 1 IP address (1 host up) scanned in 0.765 seconds
halflingrogue@ubuntu:~$
```

How do I find the Wireshark package? SPM doesn't seem able to find it.

---

### Post by The Tronyx on 2007-11-26
> **Halfling Rogue said:**
> 

How do I find the Wireshark package? SPM doesn't seem able to find it.

> 
sudo apt-get install wireshark


Should do the trick

But in all honesty your best option is to backup /home or rather what files you feel you must have and do a clean install.

Your nmap scan looked somewhat strange, scanning the localhost is fine but if it was a remote attacker they weren't able to scan from within your network.  You could go to whatsmyip.org and use that as your target to scan.  Also, run the scan in SYN stealth mode.  If you run it from the command line, use sudo otherwise you won't have all options and try the nmap GUI, you can find it as nmapfe.

> 
nmap -sS -O -PI -PT xxx.xxx.xxx.xxx

If you are running it from the command line

---

### Post by Halfling Rogue on 2007-11-26
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wireshark
halflingrogue@ubuntu:~$
```

I did apt-get update but it still can't find it. Ran nmap as you said, got this:
```
halflingrogue@ubuntu:~$ sudo nmap -sS -O -PI -PT 24.69.174.94

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-26 17:17 PST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 4.986 seconds
halflingrogue@ubuntu:~$ sudo nmap -sS -O -P0 -PI -PT 24.69.174.94

Starting Nmap 4.20 ( http://insecure.org ) at 2007-11-26 17:19 PST
Note: Host seems down. If it is really up, but blocking our ping probes, try -P0
Nmap finished: 1 IP address (0 hosts up) scanned in 3.915 seconds
halflingrogue@ubuntu:~$
```

---

### Post by The Tronyx on 2007-11-26
You could look for the old version known as ethereal.  What version of ubuntu are you on?

---

### Post by Halfling Rogue on 2007-11-26
Dapper, 6.06. I've been debating upgrading to Feisty, but I have issues with mounting my external hard drive and I'm worried that upgrading will stop it from mounting at all.

Also, chkrootkit turned this up, and I have no idea if it's relevant or not:
```
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/dhclient3[29652])
```

---

### Post by The Tronyx on 2007-11-26
> **Halfling Rogue said:**
> Dapper, 6.06. I've been debating upgrading to Feisty, but I have issues with mounting my external hard drive and I'm worried that upgrading will stop it from mounting at all.

Not that I am trying to be rude, but if you are so concerned that your system has been compromised, which is a very valid concern, why not just backup what you need, inspect those files by hand at a later date, wipe out your Dapper install and upgrade to gutsy?  

If you have problems with your drive mounting in gutsy, you know early on and can go back to dapper.  Either way the best advice I can offer, which is advice people don't often like to get, is that you should do a clean install.

---

### Post by Halfling Rogue on 2007-11-26
Because I can't backup my files. My HD won't mount to any Windows machine (it *used* to, but now it just makes the system freeze), and I don't have access to any Linux machines with enough disk space to back up my files (about 20 gigs).

But yeah, I guess I could always back-install if it doesn't work. I'll give Gutsy a shot.

---

### Post by The Tronyx on 2007-11-26
> **Halfling Rogue said:**
> Because I can't backup my files. My HD won't mount to any Windows machine (it *used* to, but now it just makes the system freeze).

That is another very valid point you might want to try and have resolved in this forum as well before you move.

---

### Post by Halfling Rogue on 2007-11-26
I was trying to resolve the Linux problems with it [over here]("http://ubuntuforums.org/showthread.php?t=590437"), but no one quite seemed to know what to do. And I have no idea how to resolve the Windows problem if it won't even let the system move while it's plugged in.

---

### Post by barney385 on 2007-11-26
[http://www.wireshark.org/](http://www.wireshark.org/)

---

