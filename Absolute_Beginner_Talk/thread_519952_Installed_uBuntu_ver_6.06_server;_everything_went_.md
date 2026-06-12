---
title: "Installed uBuntu ver 6.06 server; everything went ok; booted into system---only text"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by bhowerton on 2007-08-07
Hello all,
Well I downloaded Ubuntu ver 6.06 Server edition.  I installed it onto my pc (it is the only OS on the machine) and everything went very well.

When it was done and I booted into the OS for the 1st time...I thought I would be in a GUI environment, but there was nothing but a black screen with white text.  There was a $ as the prompt.

**Why did it boot into this DOS type environment?**

**How can I get it to boot into the GUI environment?**

I remember on the CD Bootscreen Menu, the 1st option (which I chose) said..."Install uBuntu onto the Hard Disk"

The 2nd option said..."Install uBuntu as a LAMP server" and then there were someother options about checking the cd for defects and booting from the 1st HDD and so on....

**Should I have chosen the 2nd option?**

I am running a custom built machine.  Here is a little information about my PC (I hope this machine is capable of running uBuntu):

CPU Type............................Intel Celeron II, 733 MHz 
Motherboard Name.................DFI CA61
Motherboard Chipset...............VIA VT82C693A Apollo Pro133
System Memory.....................512 MB  (SDRAM)
HDD...................................20GB
Video Card...........................ATI 3D Rage Pro  (8 MB)
Previous OS:........................Windows XP Pro

I would like to thank everyone, in advance, for their input!

BHowerton

---

### Post by dca on 2007-08-07
Server Ed has no GUI....   
 
If you want one:
 
sudo apt-get install ubuntu-desktop
 
at CLI...

---

### Post by bhowerton on 2007-08-07
What do you mean by:

CLI

---

### Post by xfceslacker on 2007-08-07
The command line. Login to the system and type sudo apt-get install ubuntu-desktop.

---

### Post by bhowerton on 2007-08-11
Hello well I typed what you said, &#8220;_sudo apt-get install ubuntu-desktop_&#8221;

I can see a whole lot of stuff that scroll across the screen.  It stops scrolling and displays at the bottom of the screen:

[B]0 upgraded, 813 newly installed, 0 to remove, and 11 not upgraded.
Need to get 375MB/442MB of archives.
After unpacking 1531MB of additional disk space will be used.
Do you want to continue [Y/n]?[/B]

I chose &#8220;Y&#8221;

Then I see a whole lot more stuff scrolling fast across the screen.  When it stops scrolling, it displays:
**Install these packages without verification [y/N]**

I chose &#8220;y&#8221;

Now once I press enter I hear the CD-ROM startup and I see a ton of stuff that shows something like the following:

[B][COLOR="Green"]   Connection failed [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libshout3 2.1-5
   Connection failed [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main ubuntu-sounds 0.3
   Connection failed [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main ubuntu-docs 6.06.2
   Connection failed [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libwpd8c2a 0.8.4-2
   Connection failed [IP: 91.189.88.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/mainlibsndfile1 1.0.12-3
   Connection failed [IP: 91.189.89.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main usplash 0.2-4[/COLOR][/B]
It stops every little bit and shows something like:
0% [connecting to us.archive.ubuntu.com (91.189.88.31)]

Then as a final action it displays the following information and returns the $ prompt:

[B]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.3](http://us.archive.ubuntu.com/ubuntu/pool/main/y/yelp/yelp_2.14.3) -0ubbuntu1_i386.deb    
Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3](http://us.archive.ubuntu.com/ubuntu/pool/main/z/zenity/zenity_2.14.3) -0ubbuntu1_i386.deb    
Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_0.120_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_0.120_i386.deb)    
Connection failed [IP: 91.189.89.6 80][/B]

**E: Unable to fetch some archives, maybe run apt-get update or try with &#8211;fix-missing?**
bobby@ubuntu-server:~$

My questions are:  What do I do now???  What does this question mean???

Thank you, in advance, for all of your help!!!

Bobby

---

### Post by Arisna on 2007-08-11
Does this machine have access to the Internet?  It needs it to retrieve the installation packages.

---

### Post by bhowerton on 2007-08-11
Yes it does...I have the internet going into my wireless router...I am posting to this forum on my wireless laptop.  This PC that I am trying to install Linux on is wired to the router.

I have checked the ip address and it is good...

I have also pinged other destinations and I get back nothing but replies...meaning I do not get any timeouts.

Thanks for the help!

Bobby

---

### Post by ghost_ryder35 on 2007-08-11
run "sudo apt-get update"

---

### Post by ghost_ryder35 on 2007-08-11
FYI the reason a "server" does not come with the GUI interface is to make it more reliable and free up system resources that would be used by a GUI interface if one was installed.  Not having a GUI are some of the reasons that Windows Server XXXX up times are much shorter than Linux server up times.

---

### Post by eentonig on 2007-08-11
If you didn't know that a linux server is Command Line Interface (CLI) by default,  it's a bit said you didn't do a bit more homework before installing. I'm afraid you're going for a disappointment now.

If you've got question, please don't be afraid to ask.

---

### Post by bhowerton on 2007-08-11
I ran the sudo apt-get update and this is what I got:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386) /Packages.gz
Connection failed [IP: 91.189.88.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz) 
Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz) 
Connection failed [IP: 91.189.88.8 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

Then it shows the $ prompt

---

### Post by eentonig on 2007-08-11
shouldn't be a problem. I have that regularly. I guess those server are a bit overcrowded.

Did someone already told you how to install the GUI?

If not. type this in the CLI

> sudo apt-get install ubuntu-desktop

---

### Post by radies on 2007-08-24
I have a similar problem, With a fresh install of 6.06.1 LTS Desktop. I got the error messages:

[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 91.189.89.6 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 91.189.89.6 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed [IP: 91.189.88.31 80]
...

Since I can open these files with my firefox browser, I assume the internet connection is working.
I tried to use the repository us.archive.ubuntu... and ca.archive.ubuntu... => the same problem.

Is there something missing?

radies

---

### Post by shearn89 on 2007-08-24
have you enabled all the repos? open a terminal and type "sudo nano /etc/apt/source.list"

Remove the starting hash from anything with "universe", "multiverse", and "main restricted".

Then press "ctrl O", "enter", "ctrl X"

and try "sudo apt-get update"

---

### Post by tszanon on 2007-08-24
If the OP wants a server with a GUI, wouldn't it be better if he just installed the Desktop version? Is there any difference?

---

### Post by chrome307 on 2007-08-24
What does the 'Desktop' update consist of?

Do you get all the applications ie GIMP, Mplayer etc

Or do you just get Synapic + Terminal ...

---

### Post by shearn89 on 2007-08-25
The Desktop version has GNOME (a graphical desktop), plus things like openoffice, some media players, nautilus file manager, firefox - its all you need (minus a few proprietary codecs) for a fully working home system.

---

