---
title: "[SOLVED] Unable to run synaptic package manager"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Khalis7 on 2007-10-30
Hi. I would like to ask if somebody could please explain to me what is the cause of "Failed to run /usr/sbin/synaptic as user root. Unable to copy the user's Xauthorization file.Failed to run /usr/sbin/synaptic as user root." .

I got this error message when I tried to run the synaptic package manager.

---

### Post by taurus on 2007-10-30
Do you run it from your user account?  What happens if you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
Or
```
gksudo /usr/sbin/synaptic
```

---

### Post by Khalis7 on 2007-10-30
Yes, definitely I run the synaptic from my account. When I try "sudo apt-get update
sudo apt-get upgrade", this what I got:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy Release 
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates Release              
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Fetched 573B in 4s (120B/s)
Reading package lists... Done

When I try run "gksudo /usr/sbin/synaptic", I able to run synaptic. Before I forget, actually, before I ran the synaptic, I got full hard disc notification. Is there anyway it's related to the error message?

---

### Post by taurus on 2007-10-30
What's the output of this command from a terminal?

```
df -h
```

---

### Post by Lord_Dicranius on 2007-10-30
> I got full hard disc notification
The guy in [this thread](http://ubuntuforums.org/showthread.php?t=545412&highlight=Unable+to+copy+the+user%27s+Xauthorization+file), links to [this thread](http://ubuntuforums.org/showthread.php?t=431294) saying it worked for him.

---

### Post by Khalis7 on 2007-10-30
This what got from  "df -h"

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G     0 100% /
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   92K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda8             8.8G  169M  8.2G   2% /home
/dev/sda1              58G   24G   35G  41% /media/sda1
/dev/sda5             5.2G  3.4G  1.9G  65% /media/sda5
overflow              1.0M   32K  992K   4% /tmp
/dev/scd0             696M  696M     0 100% /media/cdrom0

May I know what does these information serves for?

---

### Post by taurus on 2007-10-30
> **Khalis7 said:**
> This what got from  "df -h"

Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda6             2.3G  2.2G     0 100% /[/COLOR]**
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   92K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda8             8.8G  169M  8.2G   2% /home
/dev/sda1              58G   24G   35G  41% /media/sda1
/dev/sda5             5.2G  3.4G  1.9G  65% /media/sda5
overflow              1.0M   32K  992K   4% /tmp
/dev/scd0             696M  696M     0 100% /media/cdrom0

May I know what does these information serves for?

To be sure that you have maxed out  your /.  I bet  you can't log in from GUI login screen anymore.  At the GUI login screen, press <Ctrl><Alt>F2 to get into another console.  Log in with your username and password.  Then at the prompt, run

```
sudo apt-get clean
df -h
```
Now, see what is the % for / from the output above.

---

### Post by Lord_Dicranius on 2007-10-30
From [here](http://unixhelp.ed.ac.uk/CGI/man-cgi?df):
> df - report file system disk space usage
> -h, --human-readable
	      print sizes in human readable format (e.g., 1K 234M 2G)

---

### Post by Khalis7 on 2007-10-30
Dear Taurus, I followed your advise and the root usage is 97%= 2.2GB.. Now, I would  like to know is there any way for me to clean up the root?

---

### Post by taurus on 2007-10-30
Well, things are going to be real tight on your machine since you only leave 2.3GB for / with Gnome.  Gnome would probably take that much space so remove whatever apps that you don't need to free up some more space.

If I were you, I would take some space from /home and make my / to be about 5GB instead of only 2.3GB.

---

### Post by Khalis7 on 2007-10-30
Ermm..seems that I need to increase the share size of root  but is it possible to increase the root size without the need to reinstall back Gutsy? Actually, I'm still very new to linux and all the Gutsy installation was done all by myself.

---

### Post by Khalis7 on 2007-10-30
Ermm..seems that i need to increase the ize of root but what way may I do it without need to reinstall Gutsy?

---

### Post by Khalis7 on 2007-10-30
Huhu..please help me to solve the problem...

---

### Post by Lord_Dicranius on 2007-10-31
Well, I know you can use are partition manager called "gparted" to resize 'em, just not sure if it'll effect the partition at all, especially being the / partition because you'll be booted into the OS to use it, ya know?  I think I remember seeing that there's a live CD with gparted, that might work a little better.  I would wait for somebody else to jump in on this though cuz they might know better than me if it's going to effect your / partition in a negative way or not.  Or you can jump on in the #ubuntu channel over at irc.freenode.net.  There's 1180 in there right now :-)

---

### Post by macogw on 2007-10-31
GParted is on the Ubuntu live cd and there's a GParted Live CD as well, but why bother downloading that iso and burning it when you have the Ubuntu cd already?  

If your /home isn't too full, you should be able to use GParted to shrink /home and do it so that the "unallocated" space is on the side of /home that meets / because if you do it on the other side, that doesn't help much.  It'll probably take a while because it'll have to move all the data since I'm thinking it's likely that / is before /home and so the /home stuff will have to be moved to the end of that partition.    Anyway, then you can resize / to have the unallocated space you just created.

If /home is pretty full, though, backup first.

---

### Post by Khalis7 on 2007-11-01
Thanks for the info guys. At last I managed to increase the size of / by shrinking the /home using GParted in Ubuntu Live CD. From "df -h", this what I got:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             5.8G  2.3G  3.3G  41% /
varrun                252M   96K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   92K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda6             5.3G  171M  4.9G   4% /home
/dev/sda1              58G   24G   35G  41% /media/sda1
/dev/sda5             5.2G  3.4G  1.9G  65% /media/sda5

So, basically, I have resolved my problem. Thanks a  lot to all people that had gave their views and opinions. Thanks once again.

---

