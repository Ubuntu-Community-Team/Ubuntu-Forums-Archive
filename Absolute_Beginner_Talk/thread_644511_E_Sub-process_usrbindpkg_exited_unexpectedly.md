---
title: "E: Sub-process /usr/bin/dpkg exited unexpectedly"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by sapu on 2007-12-18
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/20309](https://answers.launchpad.net/ubuntu/+question/20309) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/20309](https://answers.launchpad.net/ubuntu/+question/20309) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ANYTHING dealing with dpkg will result in an error:
E: Sub-process /usr/bin/dpkg exited unexpectedly

Typing: sudo dpkg --configure -a
Results in: Bus error (core dumped)

Cannot update
Cannot install anything
Cannot do anything with dpkg

Full messages:
```
dpp@pmkcpu:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  unrar
The following NEW packages will be installed:
  rar
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/506kB of archives.
After unpacking 1036kB of additional disk space will be used.
E: Sub-process /usr/bin/dpkg exited unexpectedly

dpp@pmkcpu:~$ sudo dpkg --configure -a
Bus error (core dumped)

dpp@pmkcpu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be upgraded:
  libcairo2 libsmbclient samba-common smbclient
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9132kB of archives.
After unpacking 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com gutsy-security/main libcairo2 1.4.10-1ubuntu4.4 [524kB]
Get:2 http://security.ubuntu.com gutsy-security/main smbclient 3.0.26a-1ubuntu2.3 [4887kB]
Get:3 http://security.ubuntu.com gutsy-security/main samba-common 3.0.26a-1ubuntu2.3 [2835kB]
Get:4 http://security.ubuntu.com gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.3 [885kB]
Fetched 9132kB in 1m55s (78.8kB/s)                                             
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

---

### Post by macogw on 2007-12-19
Try
```
sudo apt-get install -f
```
I think the f means "fix", but I'm not sure.  I just know that it does tend to fix it when you have errors while installing.

---

### Post by Sef on 2007-12-19
> I think the f means "fix", but I'm not sure. I just know that it does tend to fix it when you have errors while installing.

From my understanding it means force, but both fix and force mean the same thing really.

---

### Post by macogw on 2007-12-19
> **Sef said:**
> From my understanding it means force, but both fix and force mean the same thing really.

manpage says -f is also the same as --fix-broken

---

### Post by sapu on 2007-12-19
Sudo apt-get install -f was my first attempt to fix it

```
dpp@pmkcpu:~$ sudo apt-get install -f
[sudo] password for dpp:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

Doesn't work.

---

### Post by macogw on 2007-12-19
I wonder if your dpkg is corrupted O_o  If it is, compiling a replacement dpkg (since it can't reinstall itself if it's broken) would be the only way to fix it, I think...and you'd have to have the compilers already because you can't install them...  hmm maybe you can replace it with a copy of the dpkg binary from the live cd (/usr/bin/dpkg).  I don't know if it'd work, but I guess you could try it (and make a backup copy of the one you have right now, just in case)

---

### Post by sapu on 2007-12-19
> **macogw said:**
> I wonder if your dpkg is corrupted O_o  If it is, compiling a replacement dpkg (since it can't reinstall itself if it's broken) would be the only way to fix it, I think...and you'd have to have the compilers already because you can't install them...  hmm maybe you can replace it with a copy of the dpkg binary from the live cd (/usr/bin/dpkg).  I don't know if it'd work, but I guess you could try it (and make a backup copy of the one you have right now, just in case)
I think this is called the Absolute Beginner Talk for a reason.
I wouldn't know the first step to any of that.

---

### Post by macogw on 2007-12-19
> **sapu said:**
> I think this is called the Absolute Beginner Talk for a reason.
I wouldn't know the first step to any of that.
It was kind of stream-of-consciousness rambling.  Sorry.  Anyway, if you don't know what any of it meant, then you've never compiled and so you wouldn't have compilers, so that part wouldn't work anyway.  

If the dpkg program is corrupted on your hard drive (well, that could be a bad sign that your hard drive is getting wonky if it's going about corrupting things), you can probably boot from the live cd (like when you installed), and go to Places > Computer and double click on your hard drive so it becomes mounted (able to be used).  In there double click on the folder called "etc" then in there on the one called "bin" and scroll until you see a file called "dpkg".  Rename it dpkg-backup (just to save it just in case).  Don't close that window.  Open up another Places > Computer window and double click on Filesystem (I'm hoping the live cd will say it like this...I'm sorry, my CD drive is broken so I can't actually test and see what it calls it) and go through the "etc" -> "bin" thing again.  Copy the dpkg file from that window to the one where you just renamed the old one (on your hard drive).  Reboot, and maybe that'll fix it.

---

### Post by sapu on 2007-12-19
> **macogw said:**
> It was kind of stream-of-consciousness rambling.  Sorry.  Anyway, if you don't know what any of it meant, then you've never compiled and so you wouldn't have compilers, so that part wouldn't work anyway.  

If the dpkg program is corrupted on your hard drive (well, that could be a bad sign that your hard drive is getting wonky if it's going about corrupting things), you can probably boot from the live cd (like when you installed), and go to Places > Computer and double click on your hard drive so it becomes mounted (able to be used).  In there double click on the folder called "etc" then in there on the one called "bin" and scroll until you see a file called "dpkg".  Rename it dpkg-backup (just to save it just in case).  Don't close that window.  Open up another Places > Computer window and double click on Filesystem (I'm hoping the live cd will say it like this...I'm sorry, my CD drive is broken so I can't actually test and see what it calls it) and go through the "etc" -> "bin" thing again.  Copy the dpkg file from that window to the one where you just renamed the old one (on your hard drive).  Reboot, and maybe that'll fix it.
Well I have a friend (who has a large amount of knowledge in Ubuntu/Linux) who help me set up the entire thing. If he sent me his dpkg, would it work if i overwrite it?

---

### Post by macogw on 2007-12-19
> **sapu said:**
> Well I have a friend (who has a large amount of knowledge in Ubuntu/Linux) who help me set up the entire thing. If he sent me his dpkg, would it work if i overwrite it?

If corrupted data is the problem and you're both using the same version, yeah, that should work.  Just put it as /usr/bin/dpkg and then in the terminal put ```
sudo chown root:root /usr/bin/dpkg
sudo chmod 755 /usr/bin/dpkg
```
The first line makes root own the binary (because it's a system file) and the second makes it executable.

---

### Post by sapu on 2007-12-19
> **macogw said:**
> If corrupted data is the problem and you're both using the same version, yeah, that should work.  Just put it as /usr/bin/dpkg and then in the terminal put ```
sudo chown root:root /usr/bin/dpkg
sudo chmod 755 /usr/bin/dpkg
```
The first line makes root own the binary (because it's a system file) and the second makes it executable.

So I do this after he gives me dpkg.

And if his version is different...
I was told that if I do anything on the Live CD, it'll delete itself (unless I use a flash drive).
This makes total sense, it's just a livecd, it's not an OS. So, explain again how I would access my HDD? Just... double click it, that easy?

---

### Post by macogw on 2007-12-19
Yeah, if you double click it, it'll get mounted.  Anything you do on the live cd that's *just* on the live cd gets deleted.  If you mount your hard drive and manipulate it, though, it really does write the changes to disk.  You don't need the live cd to copy his though, just to copy from the live cd.

---

### Post by sapu on 2007-12-19
> **macogw said:**
> Yeah, if you double click it, it'll get mounted.  Anything you do on the live cd that's *just* on the live cd gets deleted.  If you mount your hard drive and manipulate it, though, it really does write the changes to disk.  You don't need the live cd to copy his though, just to copy from the live cd.

Yes, I could understand that much.
I just love to have plan B's and C's if plan A doesn't work.

Hope for the best, prepare for the worst.

---

### Post by Beggar on 2007-12-19
Assuming that doesnt work, I have a few other ideas.

Have you tried doing an update?

```
 
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

```

What about using synaptic?
```
gksudo synaptic
```

If nothing else, what are the packages that your not upgrading

"0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded."

easy way to find them, (assuming synaptic opens), is press the "mark all upgrades" button in synaptic.

For future reference, as a new user you will most likely find synaptic to be much easier to deal with.

---

### Post by sapu on 2007-12-19
> **Beggar said:**
> Assuming that doesnt work, I have a few other ideas.

Have you tried doing an update?

```
 
sudo apt-get update
sudo apt-get install -f

```

What about using synaptic?
```
gksudo synaptic
```

If nothing else, what are the packages that your not upgrading (easy way to find them, assuming synaptic opens), is press the "mark all upgrades" button in synaptic.

For future reference, as a new user you will most likely find synaptic to be much easier to deal with.
If you've read the post, you would have known sudo apt-get install -f and update didn't and don't work. Dpkg is also what runs anything to do with installing. So update wont work.

Also, what would I do in the packet manager?
I can't install or update anything.

---

### Post by Beggar on 2007-12-19
> **sapu said:**
> If you've read the post, you would have known sudo apt-get install -f and update didn't and don't work. Dpkg is also what runs anything to do with installing. So update wont work.

Also, what would I do in the packet manager?
I can't install or update anything.


First of all being rude to people who offer suggestions is not necessary. 

As far as my suggestions, you have stated nowhere in your post that you ran apt-get update, you stated that you "Cannot update" but that does not necessarily mean you knew that to be a command you could run. I made that suggestion in case you didn't, in this case that is a potential fix which you have not stated that you ruled out.

"Dpkg is also what runs anything to do with installing. So update wont work."

Dpkg is running, the error your getting is that it is exiting unexpectedly. That does not mean that there is something horribly wrong with it. For all I know the problem is that your sources haven't been updated and its confused and trying to install a file it cant find. (A problem you might have if you haven't run update). Due to the nature of the error, IE no reason given, just that it is exiting unexpectedly you cant reasonably rule many things out. 

"What would you do in a package manager?"
Well you could do lots of things. For one you could tell me what updates you dont have installed. You could also try installing a package using it. Its a shot, but feasible that you are somehow doing something wrong.  By using a GUI that I trust, I can rule out any potential of you (an admitted new user) doing something incorrectly.



Another theory, is your computer running out of memory? It did just complete unpacking a bunch of files... Also, can you find the core file that gets created, Id be interested to hear what it has to say.

---

### Post by sapu on 2007-12-19
> **Beggar said:**
> As far as my suggestions, you have stated nowhere in your post that you ran apt-get update, you stated that you "Cannot update" but that does not necessarily mean you knew that to be a command you could run. I made that suggestion in case you didn't, in this case that is a potential fix which you have not stated that you ruled out.
Here is sudo apt-get update:
```
dpp@pmkcpu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Hit http://us.archive.ubuntu.com gutsy/main Packages                
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:4 http://security.ubuntu.com gutsy-security Release [51.2kB]               
Get:5 http://security.ubuntu.com gutsy-security/main Packages [50.2kB]         
Get:6 http://security.ubuntu.com gutsy-security/restricted Packages [14B]      
Get:7 http://security.ubuntu.com gutsy-security/main Sources [8394B]           
Get:8 http://security.ubuntu.com gutsy-security/restricted Sources [14B]       
Get:9 http://security.ubuntu.com gutsy-security/universe Packages [27.0kB]     
Get:10 http://security.ubuntu.com gutsy-security/universe Sources [4368B]      
Get:11 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]   
Get:12 http://security.ubuntu.com gutsy-security/multiverse Sources [833B]     
Fetched 145kB in 14s (9802B/s)                                                 
Reading package lists... Done

```
Sorry about the "hostility"
After a week of this, the frustration is just now getting to me

EDIT:
sudo apt-get upgrade is currently running...
...at 15kb/s

```
dpp@pmkcpu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libcairo2 libsmbclient linux-headers-2.6.22-14
  linux-headers-2.6.22-14-generic linux-image-2.6.22-14-generic samba-common
  smbclient
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.0MB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com gutsy-security/main linux-image-2.6.22-14-generic 2.6.22-14.47 [18.5MB]
Get:2 http://security.ubuntu.com gutsy-security/main libcairo2 1.4.10-1ubuntu4.4 [524kB]
Get:3 http://security.ubuntu.com gutsy-security/main linux-headers-2.6.22-14 2.6.22-14.47 [7776kB]
Get:4 http://security.ubuntu.com gutsy-security/main linux-headers-2.6.22-14-generic 2.6.22-14.47 [580kB]
Get:5 http://security.ubuntu.com gutsy-security/main smbclient 3.0.26a-1ubuntu2.3 [4887kB]
Get:6 http://security.ubuntu.com gutsy-security/main samba-common 3.0.26a-1ubuntu2.3 [2835kB]
Get:7 http://security.ubuntu.com gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.3 [885kB]
Fetched 36.0MB in 42m53s (14.0kB/s)                                            
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg exited unexpectedly
```
I'll attempt to replace dpkg via livecd tomorrow.

---

