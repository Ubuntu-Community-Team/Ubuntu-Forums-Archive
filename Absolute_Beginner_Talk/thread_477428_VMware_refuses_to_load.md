---
title: "VMware refuses to load"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-06-18
I have recently installed VMware Workstation but am having problems setting it up. It installed, compiled for my kernel etc fine, but everytime I run VMware through console or menus I get this:

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

When I reconfigure it, it finishes but the same error happens again. Any ideas?

Thanks.

PS; I'm running Ubuntu 7.04 Feisty i386..

---

### Post by dreadlord_chris on 2007-06-18
have you tried running it as root?
```

sudo vmware

```

---

### Post by Pas_sa on 2007-06-18
Same error occurs when running as root..

---

### Post by Bachstelze on 2007-06-18
Could you please paste the last thing you see when you run vmware-config.pl ? I guess it does not run successfully. Also, how did you install vmware ?

---

### Post by Pas_sa on 2007-06-18
[http://paste.ubuntu-nl.org/26194/](http://paste.ubuntu-nl.org/26194/)

How did I install it? I ran the installer as root and followed the prompts.

---

### Post by Pas_sa on 2007-06-18
Just wanted to move this up to the front page again.. I really need VMware for my work, if someone could help me fix the problem?...

---

### Post by fdrake on 2007-06-18
did this happen when u updated the kernel?? samething like that happened to me every time i update the kernel.

make sure u have all the neccesary modeules installed for vmware.
sudo aptitude search vmware 
and see for the module of your vmware server or player, whatever u using.

---

### Post by Pas_sa on 2007-06-18
No no, this is right after installing and it won't work..

Here is the output of aptitude search vmware:

```
andrew@andrewdesktop:~$ sudo aptitude search vmware
Password:
p   vmware-player                   - Free virtual machine player from VMware   
p   vmware-player-kernel-modules    - vmware-player kernel module dependency pac
p   vmware-player-kernel-modules-2. - vmware-player modules for Linux (kernel 2.
p   vmware-player-kernel-modules-2. - vmware-player modules for Linux (kernel 2.
p   vmware-player-kernel-modules-2. - vmware-player modules for Linux (kernel 2.
p   vmware-player-kernel-source     - Source for the vmware-player-kernel driver
p   vmware-server                   - Free virtual machine server from VMware   
p   vmware-server-kernel-modules    - vmware-server kernel module dependency pac
p   vmware-server-kernel-modules-2. - vmware-server modules for Linux (kernel 2.
p   vmware-server-kernel-modules-2. - vmware-server modules for Linux (kernel 2.
p   vmware-server-kernel-source     - Kernel modules for VMware Server.         
p   vmware-tools-kernel-modules     - vmware-tools kernel module dependency pack
p   vmware-tools-kernel-modules-2.6 - vmware-tools modules for Linux (kernel 2.6
p   vmware-tools-kernel-modules-2.6 - vmware-tools modules for Linux (kernel 2.6
i   xserver-xorg-video-vmware       - X.Org X server -- VMware display driver   
andrew@andrewdesktop:~$ 

```

Plus I am using VMware Workstation so I'm not sure if this is even relevant..

---

### Post by Pas_sa on 2007-06-19
Come on guys.. can't do any of my work until I get this fixed..

---

### Post by Pas_sa on 2007-06-19
I hate to be rude and keep bumping like this but this is mission critical for me - I need VMware working..

---

### Post by dreadlord_chris on 2007-06-19
> **Pas_sa said:**
> I hate to be rude and keep bumping like this but this is mission critical for me - I need VMware working..

Is there a particular reason you need Vmware *Workstation*? I'm running the latest Vmware Server, it's in the repositories, and it works great.

---

### Post by wirelessmonkey on 2007-06-19
I had to use the latest vmware-any-any patch to get it working.   
This is the direct link: [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update110.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update110.tar.gz)
this is to a description of how/why it works, sorta: [http://www.vmware.com/community/thread.jspa?threadID=26693](http://www.vmware.com/community/thread.jspa?threadID=26693)


Good Luck

---

### Post by Pas_sa on 2007-06-19
> **dreadlord_chris said:**
> Is there a particular reason you need Vmware *Workstation*? I'm running the latest Vmware Server, it's in the repositories, and it works great.
Yeah, I thought Workstation was better and I got a copy from work and was told to throw it on.. what is the difference?

wirelessmonkey I tried that and it did nothing :)

EDIT: Okay I'll make the switch.. just how do I uninstall vmware workstation first? Heh.. :(

---

### Post by dreadlord_chris on 2007-06-19
> **Pas_sa said:**
> Yeah, I thought Workstation was better and I got a copy from work and was told to throw it on.. what is the difference?

wirelessmonkey I tried that and it did nothing :)

EDIT: Okay I'll make the switch.. just how do I uninstall vmware workstation first? Heh.. :(

Not really sure what the difference would be - other then the versions in the repositories just seem to work :p

As for uninstalling workstation -Since it's not showing with aptitude, I don't know, probably similiar to how you installed it...

---

### Post by fdrake on 2007-06-19
try this link 
[http://levelsofdetail.kendeeter.com/2007/04/installing_vmware_workstation.html](http://levelsofdetail.kendeeter.com/2007/04/installing_vmware_workstation.html)

---

### Post by CaptainSteel on 2007-06-19
I used this guys website for VMWare Workstation and it worked like a champ. He goes step by step. Hope this helps =)
[COLOR="RoyalBlue"][http://www.linuxloader.com/modules.php?name=Content]("http://www.linuxloader.com/modules.php?name=Content")[/COLOR]

---

### Post by SenseiJonny on 2007-06-27
Hey, I came across this thread while having a problem with install VMware server in Feisty.  I originally had a problem with vmmon, but the "any-any" patch fixed that.

After that, I had this same problem where I would try to run VMware and it would tell me to reconfigure, even though it had configured successfully.  I fixed it by following [this post]("http://ubuntuforums.org/showpost.php?p=2142490&postcount=13").  I skipped down to step 5, which tells you to remove the "not_configured" flag from the vmware directory.  After that, I restarted vmware and ran it as that post said.  It worked just fine after that.  If you haven't fixed the problem yet, hopefully this will help.  At the very least, it may help other people like me who stumble upon this thread with the same problem I had.

---

