---
title: "How can I run a security check on my Linux computer"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-12-24
Is there a security checking programs available that I can run on a Linux computer to test for any breaches of secuity, such as virus's, spyware or open ports etc?

---

### Post by lgambett on 2007-12-24
An antivirus program is almost useless in practice; anyway you can try AVG for Linux (three programs, AVG antivirus, antispyware and antirootkit). 
For the open ports use the terminal and give the command
netstat -anutd

---

### Post by ~LoKe on 2007-12-24
Viruses and spyware only work in theory, so you don't need to worry about those too much.

As for open ports...maybe [this](http://whatsmyip.org/ports/)?

---

### Post by barbedsaber on 2007-12-24
You don't need to do any of that anymore, which is the main reason I went to linux, NO VIRUSES!

---

### Post by Paqman on 2007-12-24
Viruses: Don't worry, you are effectively protected just by using Linux
Spyware: Same. All the software in the repos is 100% trustworthy
Open ports, etc: Linux has a built in firewall, and all ports are stealthed by default. There is a good GUI for configuring the firewall available, called Firestarter. It'll allow you to see what connections are active, etc.

There is one nasty thing that can happen to a Linux box, it's called a rootkit. Basically it allows someone to gain root access to your system. If you're feeling paranoid there are rootkit scanners in the repos. I wouldn't lose any sleep over it though.

---

### Post by hyper_ch on 2007-12-24
well, you can run rkhunter and chkrootkit... both will check for installed root kits....

---

### Post by Existentialist on 2007-12-24
Nessus, which is free for non-commercial use, is a great tool for vulnerability scanning.  Iv never used the linux version but I'm sure it is just as good if not better than the one for windows.

[http://www.nessus.org/nessus/](http://www.nessus.org/nessus/)

---

### Post by Josh1 on 2007-12-24
I pen test my network every 2-3 weeks depending, as well as running ClamAV since I share files with Windoze users.
You can have a look at pen test tools at sectools.org.

---

### Post by dnvikram on 2007-12-24
Nmap and Nessus are pretty effective tools for vulnerability testing and netstat command with some specific options is also useful in showing what ports are running what and etc.

Firestarter can also be configured to set specific firewall rules and alerts for the packets coming in and out.

AppArmor and Clamv are also some nice tools which help in securing your box.Most importantly,if you dont use a service,turn it OFF asap.Prevention is better than cure.Turn on only those services which you really use.In a way, ubuntu takes that precaution after the default installation.Viruses,worms and trojans practically cant scratch ubuntu or to the matter of fact most of the unix or linux distros due to the way its designed,especially the File Access Permissions,getting around which is itself is a stumbling block for any malicious program.

Ultimately,a computer is as good(secure) as its user.So,even God cant help a dumb user with root access or a careless,overconfident administrator.

---

### Post by coffee on 2007-12-30
I just ran rkhunter on my box and got this warning. should I be worried about this, if so what do I need to do to fix it?

[16:30:19]   Checking for hidden files and directories       [ Warning ]
[16:30:19] Warning: Hidden directory found: /etc/.java
[16:30:19] Warning: Hidden directory found: /dev/.static
[16:30:19] Warning: Hidden directory found: /dev/.udev
[16:30:19] Warning: Hidden directory found: /dev/.initramfs

Thanks

---

### Post by SPr on 2007-12-31
> **coffee said:**
> I just ran rkhunter on my box and got this warning. should I be worried about this, if so what do I need to do to fix it?

[16:30:19]   Checking for hidden files and directories       [ Warning ]
[16:30:19] Warning: Hidden directory found: /etc/.java
[16:30:19] Warning: Hidden directory found: /dev/.static
[16:30:19] Warning: Hidden directory found: /dev/.udev
[16:30:19] Warning: Hidden directory found: /dev/.initramfs

Thanks

It's nothing to worry about. I think rkhunter flags them because it doesn't like finding hidden files in certain directories.

---

### Post by jvc26 on 2007-12-31
Another possible would be to use tripwire or integrit to see whether any changes have been made to system files without your permission. Note: The latest integrit in the repositories is broken, but you can use the v3.5 (I think) instead without too much trouble.

Rhkunter and chkrootkit are also useful tools, but these have already been mentioned.

Il

---

### Post by Tux.Ice on 2007-12-31
how about avg free edition for linux???????

---

### Post by Tux.Ice on 2007-12-31
google-avg

---

### Post by hyper_ch on 2008-01-01
You don't need an anti-virus program.

---

### Post by bryncoles on 2008-01-14
ive read about turning services off for security in linux.... but as im a bit green around the gills, im not sure i understand! im a new migrant from windows (bless me!)... how / what services should i turn off (i know, i know.... depends what ive installed and what i want to do). 

i mainly need to use office documents, and surf the web (mostly academic websites, journal databases etc, on account of me being cool...)

pre-emptive thanks for your help!

---

### Post by (((X))) on 2008-01-14
hello
bryncoles

If you want more security, disable all not used programs and services
some of them are ssh(to login remotely), ntfs-3g(to read-write to ntfs), samba(for sharing files over a network), programs like gaim, kmail, akregator if you do not use mail-client..
just open package manager and uninstall what you dont use, all packages have good discription..

---

### Post by Paqman on 2008-01-14
> **bryncoles said:**
> ive read about turning services off for security in linux.... but as im a bit green around the gills, im not sure i understand! 

I'm not much of a security guru either, by my understanding is that even with ports open you wouldn't be at much risk unless a service was listening on that port. So the more services (eg: servers like Samba) you have active the more potential vectors you give an attack.

So if (for example) you had Samba installed but didn't actually need it, then you should get rid of it.

---

### Post by bryncoles on 2008-01-15
ok cool, thank you both for that advice. i am looking though my installed packages now - it may sound silly but it didnt even occur to me that i could do that!

;-)

---

### Post by 3rdalbum on 2008-01-15
Bryncoles, unless you have installed a server application, you will not need to turn off any additional services. Ubuntu ships with no ports open by default.

Also do a Google search for "Shields Up". It's a free web-based port scanner that will find if you've got any ports open on your computer. In the unlikely event that you do, it will tell you what is open, so you can disable the service.

---

### Post by hyper_ch on 2008-01-15
> **3rdalbum said:**
> Ubuntu ships with no ports open by default.
That's wrong. Ubuntu ships with ports open but no applications that listens to them.

---

### Post by philinux on 2008-01-15
> **hyper_ch said:**
> That's wrong. Ubuntu ships with ports open but no applications that listens to them.

+1 for that.

The best protection so far is a router with a hardware firewall.

---

