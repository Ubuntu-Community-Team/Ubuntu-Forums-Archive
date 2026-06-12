---
title: "Help: Can't add packages"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by rich86 on 2007-06-11
Hi, from today it seems i can't add packages, what ever i try doing to install them i get this error:
```
E: /var/cache/apt/archives/[package name].deb: failed in buffer_read(fd)
```
what have i done why is it not working?

any other info you need?

---

### Post by Bachstelze on 2007-06-11
Delete the offending file and try again.

---

### Post by rich86 on 2007-06-11
thanks for quick reply but i tried that, I have attaches a screenshot of what i get.

its the same for all packages

i tried rebooting as well

---

### Post by Bachstelze on 2007-06-11
Try to clean the cache :

```
sudo apt-get clean
```

---

### Post by rich86 on 2007-06-11
still get the same error

---

### Post by rich86 on 2007-06-11
i looked in some other threads and have tried:

sudo dpkg --configure -a

and repairing broken packages but still not working

i also tried installing from terminal and same error

i notice this has been a problem on 64bit version but i am on the 32

---

### Post by rich86 on 2007-06-11
i have tried some random packages and removing some other packages, an i always fail at the same point with the same error "failed in buffer_read(fd)"
is this a corrupt database? is there anyway to recover it or to reinstall the package manager?

i have also tried removing sources.list and rebuilding the package list but no help.

---

### Post by rich86 on 2007-06-11
OK i ran
"sudo touch /forcefsck"
rebooted ran fsck to check the file system, it found quite a few errors but fixed them
 and now i have a new error when installing or removing packages:

"files list file for package `ndisgtk' is missing final newline"

i edited ndisgtk in /usr/bin with a newline
i also found a ndisgtk.list in /var/lib/dpkg/info/
i cannot edit that at all even in pico in terminal any other way to try?

please help someone!

right i give up for now, this error does not even exist on google, i need some sleep. anyone with any ideas in the mean time please leave them here

---

### Post by rich86 on 2007-06-12
*bump*

right its a new day anyone out there got any ideas?...i might have to resort to restoring an image from a few days ago....

---

### Post by SkyNet2029 on 2007-06-12
Have you tried 

```
$sudo aptitude -f install
```

?

this command tells aptitude to check for any missing dependencies/broken/unconfigured packages
and to fix them...

---

### Post by rich86 on 2007-06-12
have now! this is the output:
```
richard@richards:~$ sudo aptitude -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  clamav-base clamav-freshclam libclamav2 libgmp3c2 
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav2 libgmp3c2 
The following packages will be REMOVED:
  ekiga{p} gpsdrive{p} 
The following packages will be upgraded:
  file libexif12 libmagic1 libpng12-0 mplayer 
5 packages upgraded, 5 newly installed, 2 to remove and 0 not upgraded.
Need to get 11.6MB/16.2MB of archives. After unpacking 13.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://security.ubuntu.com feisty-security/universe libclamav2 0.90.2-0ubuntu1.2 [371kB]
Get:2 http://gb.archive.ubuntu.com feisty/main libgmp3c2 2:4.2.1+dfsg-4build1 [436kB]
Get:3 http://security.ubuntu.com feisty-security/universe clamav-base 0.90.2-0ubuntu1.2 [204kB]
Get:4 http://security.ubuntu.com feisty-security/universe clamav-freshclam 0.90.2-0ubuntu1.2 [9694kB]
Get:5 http://security.ubuntu.com feisty-security/universe clamav 0.90.2-0ubuntu1.2 [870kB]
Fetched 11.6MB in 47s (242kB/s)                                                 
Preconfiguring packages ...
(Reading database ... dpkg: error processing ekiga (--purge):
 files list file for package `ndisgtk' is missing final newline
Errors were encountered while processing:
 ekiga
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

thanks for quick response any other suggestions

---

### Post by rich86 on 2007-06-12
right ok, i am going to restore my image unless anyone has any last minute ideas.

one question can i just copy the home/[username]/ folder to restore all my settings that have changed?

---

### Post by SkyNet2029 on 2007-06-12
answer to restoring your home directory: yep. in the installer menu(partitioning) copy files from other partition will do the trick.. so will NOT formatting said partition.

The only info via Google, is that of an ndiswrapper bug.. not fixed, and references to installing ndiswrapper from source. Dunno if that even applies to you, but that is what the ndisgtk error you are hitting seems to be pointing at. 
Take a look here, if you still fell up to bashing your head on the desk. 

[http://ubuntuforums.org/showthread.php?t=286924]("http://ubuntuforums.org/showthread.php?t=286924")

---

### Post by christhemonkey on 2007-06-12
See this thread:
[http://ubuntuforums.org/showthread.php?t=12737](http://ubuntuforums.org/showthread.php?t=12737)

---

### Post by rich86 on 2007-06-12
omg thanks, just in the brink of time, i had all home backed up and finding the image tool disks!
so the solution is to anyone that finds this thread with a similar problem:
mv /var/lib/dbkg/info /var/lib/dbkg/info_old
mkdir /var/lib/dbkg/info4
apt-get update, apt-get -f install
mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
rm -f /var/lib/dpkg/info
mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

well you can do more that is all i did and it all works now. i also did a full file system check and it found some corruption run:
sudo touch /forcefsck
and reboot, it will do a full check of your root disk.

many thanks to everyone that helped. defiantly sticking with this linux disto the support community is brilliant.

---

