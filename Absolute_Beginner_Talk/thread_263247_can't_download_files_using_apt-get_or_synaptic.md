---
title: "can't download files using apt-get or synaptic"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by kkellner on 2006-09-22
every time I attempt to download and install something using apt-get the process freezes when it is "searching for headers" and then gives me a 504 proxy error.  I am working under a proxy server but I haven't had this problem before and I believe I have all the settings correct (i.e., in /etc/apt/apt.conf, and in the network settings).  my internet works properly in firefox and gaim. any ideas?

---

### Post by aysiu on 2006-09-22
Can you post the **exact** output of this command? ```
sudo aptitude update
``` Don't summarize the output--just copy and paste it exactly as is.

---

### Post by kkellner on 2006-09-22
ken@brutus:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... 72Writing extended state information... Done
Building tag database... 0%             Building tag database... Done
Writing extended state information... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [5161B]
Get:3 [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages [519B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                                                                                                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
  504 Proxy Error ( Connection timed out )
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
  504 Proxy Error ( Connection timed out )
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  504 Proxy Error ( Connection timed out )
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  504 Proxy Error ( Connection timed out )
Fetched 5871B in 27m33s (4B/s)
Reading package lists... 0%             Reading package lists... Done

---

### Post by aysiu on 2006-09-22
Proxy error, huh?

[This thread](http://ubuntuforums.org/showthread.php?t=183093) might help you.

---

### Post by kkellner on 2006-09-22
thanks for looking into my situation - I have already done the things recommended (edited apt.conf, included the export HTTP_PROXY environmental variable in my ./bashrc, and edited /etc/wgetrc to include my proxy address as well.  I recently installed some packages to give my terminal transparency (they were modified from edgy packages, I think) using [http://www.compiz.net/topic-4600-gnome-terminal-true-transparency-for-dapper]("http://www.compiz.net/topic-4600-gnome-terminal-true-transparency-for-dapper").  Maybe that caused the problem?  Thanks for helping me out.

---

### Post by kkellner on 2006-09-22
another note: I have actually been able to download some packages, such as an automatix update.  however if the package comes from archives.ubuntu.com then it will not download regardless if I try to get it in update-manager, using aptitude, or using synaptic.

---

### Post by aysiu on 2006-09-22
archive.ubuntu.com, you mean? (You wrote *archive**s**.ubuntu.com*)

Maybe try a mirror? *us.archive.ubuntu.com*, for example.

---

### Post by kkellner on 2006-09-22
I'll give that a try, thanks.  It could be too that my college internet is being difficult - that happens often enough.

---

### Post by someonedumb on 2006-09-23
Is there a different way to download packages? (for example, downloading packages from a website using a Windows computer)

---

### Post by wildseven on 2006-09-23
yes, there are multiple ways to download packages. besides using the repositories, which might i add are amazing lol, you can use wget.
example:
```
wget Http://www.random.com/example.tar.gz
```

or you can just open a browers in windows or linux and download the .deb or .tar or .tar.gz
 i havent played with .deb that much, but i beleive the command is something like this
```
dpkg -i example.deb
```

for a .tar you can

```
tar -xvf example.tar
```
and for tar.gz

```
tar -xvzf example.tar.gz
```

i know you can also download a redhat package ( i think its .rem or .rpm?) and there is some command to unpackage that.

good luck mate. i hope this helped a bit.

---

### Post by kkellner on 2006-09-23
I tried changing [http://archive.ubuntu.com](http://archive.ubuntu.com) to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) in my sources.list but it didn't work.  upgrade-manager can see the updates I need to download but it can't get them for some reason - I can connect to other sites in the terminal (getautomatix.com, and I can ping google) but anything archive.ubuntu.com won't work.  the add/remove programs gui can't download anything either, though I can see what I have installed and what's available.  I double checked all my proxies and they are set properly - this was working perfectly 2-3 days ago.  Is there any chance there's something wrong with the site I'm trying to get the packages from?

---

### Post by kkellner on 2006-09-23
Alright, I rewrote my sources.list to see if that was the problem.  I can connect and download updates from security.ubuntu.com and everywhere else except us.archive.ubuntu.com and archive.ubuntu.com.  The error messages always say that the repository is no longer available or that I have network problems.  I'm pretty sure I don't have network problems because I can get to the other repositories.  Is archive.ubuntu.com having problems or something?  Any other ideas?

---

