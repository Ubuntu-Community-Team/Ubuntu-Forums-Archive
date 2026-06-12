---
title: "apt-get is broken"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by waxyfresh on 2007-04-07
this has been going on for like 4 days and i cant seem to get the issue resolved any help would be greratly apreciated.sorry for reposting this
\
\
\
root@sleepless:~# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...er/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...er/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...es/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://seveas.theplayboymansion.net/...as/Release.gpg](http://seveas.theplayboymansion.net/...as/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg](http://us.archive.ubuntu.com/ubuntu/...ts/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://wine.budgetdedicated.com/apt/...er/Release.gpg](http://wine.budgetdedicated.com/apt/...er/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://deb.opera.com/opera/dists/etch/Release.gpg](http://deb.opera.com/opera/dists/etch/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://people.ubuntu.com/~jbailey/sn..././Release.gpg](http://people.ubuntu.com/~jbailey/sn..././Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://medibuntu.sos-sts.com/repo/di...er/Release.gpg](http://medibuntu.sos-sts.com/repo/di...er/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/dists/d...al/Release.gpg](http://archive.canonical.com/dists/d...al/Release.gpg) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
root@sleepless:~#
Last edited by waxyfresh : 1 Minute Ago at 10:39 AM. Reason: purple monkey dishwasher
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
waxyfresh
View Public Profile
Send a private message to waxyfresh
Find all posts by waxyfresh
Add waxyfresh to Your Buddy List
  #2   Report Post  
Old 2 Days Ago
Happy_Man's Avatar 	
Happy_Man Happy_Man is offline
A Carafe of Ubuntu
	  	
Join Date: Jan 2007
Location: Philadelphia, YEEAH!
Beans: 156
Ubuntu 6.10 Edgy User
Re: are the repos down?
Well, is your internet connection configured correctly? And another thing, any reason you are in root? In Ubuntu, you can use the sudo command (super user do) in front of anything to execute that task with root privileges. So, instead of doing

Code:

sudo su
apt-get update

you can just do
Code:

sudo apt-get update

Much easier.
__________________
A great man once said: "We must be the change we wish to see in the world." I wish I knew who the guy who said this was. Does that mean I have to be the guy?
Reply With Quote Multi-Quote This Message Quick reply to this message
Happy_Man
View Public Profile
Send a private message to Happy_Man
Find all posts by Happy_Man
Add Happy_Man to Your Buddy List
  #3   Report Post  
Old 2 Days Ago
bapoumba's Avatar 	
bapoumba bapoumba is offline
Ubuntu French Roast
	  	
Join Date: Sep 2006
Location: France
Beans: 1,241
The Feisty Fawn Testing User
Send Message via Jabber to bapoumba
Re: are the repos down?
Quote:
Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Are you behind a proxy ? Have you declared one somewhere ?
__________________
-wysinawyg-
forum francophone Ubuntu ; radio bazarnaom ; Planet Ubuntu Users
Linux user #413984 ; Ubuntu user #178
Reply With Quote Multi-Quote This Message Quick reply to this message
bapoumba
View Public Profile
Send a private message to bapoumba
Send email to bapoumba
Visit bapoumba's homepage!
Find all posts by bapoumba
Add bapoumba to Your Buddy List
  #4   Report Post  
Old 11 Hours Ago
waxyfresh waxyfresh is online now
First Cup of Ubuntu
	  	
Join Date: Apr 2007
Bean Count Hidden
Re: are the repos down?
i shouldent be behind a proxy,how do i tell
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
waxyfresh
View Public Profile
Send a private message to waxyfresh
Find all posts by waxyfresh
Add waxyfresh to Your Buddy List
  #5   Report Post  
Old 10 Hours Ago
waxyfresh waxyfresh is online now
First Cup of Ubuntu
	  	
Join Date: Apr 2007
Bean Count Hidden
Re: are the repos down?
acording to whatsmyip.org i dont have a proxy unless its an invisible one.jso what else coudl this be?
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
waxyfresh
View Public Profile
Send a private message to waxyfresh
Find all posts by waxyfresh
Add waxyfresh to Your Buddy List
  #6   Report Post  
Old 10 Hours Ago
waxyfresh waxyfresh is online now
First Cup of Ubuntu
	  	
Join Date: Apr 2007
Bean Count Hidden
Re: are the repos down?
dont think this will help much but here it is anyway.so im deffintly not behind a proxy right?


Portscan on IP 199.2.58.25

Checking for a SMTP server....
Testing port 25: Connection timed out....

Checking for a POP3 Server....
Testing port 110: Connection timed out....

Checking for a open proxy server....
Testing port 1080: Connection timed out....
Testing port 81: Connection timed out....
Testing port 8080: Connection timed out....

Checking for a open Windows share....
Testing port 136: Connection timed out....
Testing port 137: Connection refused....
Testing port 138: Connection refused....

Checking misc ports....

Results:
Tested ports that are closed:
25, 110, 1080, 81, 8080, 136,

Tested ports that are Open but not accepting connections:
137, 138,

Tested ports that are Open and accepting connections:
None
Edit/Delete Message

---

### Post by xopher on 2007-04-07
Make sure your /etc/hosts file is intact, it seems to re-route all ip's to your localhost (127.0.0.1).

Other possible problems could include dns etc.

---

### Post by HeelsFan on 2007-04-07
I had a weird problem when I upgraded from Edgy to Fiesty beta a couple of days ago.  I did a upgrade through terminal (not through CD) and when it booted up it said that apt was not installed and to use apt-get to install it.  Unfortunately, you can't install a program with itself.

So Fiesty would not boot in the latest kernal, but when I selected an earlier kernal from the grub boot loader it worked fine.  So, I then installed Fiesty via CD and I could actually boot up into the OS through the latest kernal.  Unfortunately, Fiesty would never shut-down correctly.

Given those issues, I'm back to Edgy for the time being (probably for at least a couple of months after Fiesty is officially released).

---

### Post by zvacet on 2007-04-07
```
sudo aptitude apt
```

---

### Post by waxyfresh on 2007-04-07
didint know which one you were talking about so heres hosts : 
127.0.0.1	localhost.localdomain	localhost	sleepless

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




and heres host.conf

order hosts,bind
multi on

---

### Post by waxyfresh on 2007-04-07
sudo aptitude apt returned unknown commnand "apt"

---

### Post by sailor2001 on 2007-04-07
I think there has been some trouble with ip-6  check previous  posts about ip-6

---

### Post by waxyfresh on 2007-04-07
cant find anythging on it,i probly am n ot searching for the right stuff

---

### Post by Maestro23 on 2007-04-07
> **waxyfresh said:**
> cant find anythging on it,i probly am n ot searching for the right stuff

You can disable Ipv6 if you want: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6)

---

### Post by waxyfresh on 2007-04-07
i disabled it but still noluck.

---

### Post by chalex on 2007-04-07
What does your /etc/apt/sources.list look like?

---

### Post by chalex on 2007-04-07
Can you post the output of "netstat -rn"?

---

### Post by Maestro23 on 2007-04-07
.

---

### Post by waxyfresh on 2007-04-07
r00t@sleepless:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG        0 0          0 eth0
r00t@sleepless:~$






# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main



ive also already run all the gpg keys,and this is uneditewd from source-o-matic

---

### Post by waxyfresh on 2007-04-07
[http://forums.debian.net/viewtopic.php?p=1209](http://forums.debian.net/viewtopic.php?p=1209)

loks like this guy had the same problem,i uninstalled anon-proxy now what?apt still isint working

---

### Post by phoenixfirebird on 2007-04-09
What happens when apt-get is totally missing?  I was able to boot into Feisty this morning, but when I tried in the afternoon it refused to boot.  It kept telling me that apt-get was missing, and it won't let you go beyond that.

---

### Post by carlosp on 2007-04-13
I had the same problem after playing around with tor and privoxy.

I solved it by editing my .bash_profile.
I had to comment the following lines:

```
http_proxy=http://127.0.0.1:8118/
HTTP_PROXY=$http_proxy
export http_proxy HTTP_PROXY
```

and voilá!

---

