---
title: "Can't download from servers"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by steelklvr on 2007-10-22
Hi,

I have been trying to use synaptic to install programs but i am unable to get any repo indexes from the server or download anything, I have tried multiple servers and this is always the case.

I can ping the servers with no issues but downloading is not possible (connection timeout error).

Everything worked fine in Feisty but when i upgraded to Gutsy the problems started.

Is there something I can change in my settings (wired connection) that would correct this problem?

Any help would be appreciated.

Thanks.

---

### Post by yabbies on 2007-10-22
post the outcome of 

```
cat /etc/apt/sources.list
```

---

### Post by steelklvr on 2007-10-22
Thanks for the prompt reply

Here is the output of that command:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by yabbies on 2007-10-22
everything lloks good in your sources list
are you able to get on the net through a browser?

---

### Post by steelklvr on 2007-10-22
Hey, 

Sorry for the late reply, been out for the day.

Yeah i can access the internet through firefox, it's just synaptic and the update manager. 

I've looked around on google and i've been hearing reports of DNS issues for ftp through synaptic in ubuntu, but i have been unable to find a solution.

Every server connected to through synaptic has an IP of 1.0.0.0 and the connection time out issue is given, however nothing has been changed settings wise on the router, the only thing that i've changed is upgrading to gutsy so i think the direct cause is there.

---

### Post by coront on 2007-10-22
I'm having the same problem

---

### Post by steelklvr on 2007-10-22
Update:

Fantastic (obviously not for you but i'm glad i'm not alone)

Here is my error message after enough failed attempts have gone through.

> [B]
Could not download all repository indexes[/B]

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[LIST]
[*][http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

[*][http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg:](http://wine.budgetdedicated.com/apt/dists/feisty/Release.gpg:) Could not connect to wine.budgetdedicated.com:80 (1.0.0.0), connection timed out
[/LIST]


I'm not sure but i assume the ":80" at the end of these suggests that it's an http transmission rather than ftp, and I can't download from WINE's sources either which suggests that it's quite likely to be a settings issue rather than a server issue.

And one final note:

I was unable to use the internet until network.dns.disableIPv6 value in about:config for firefox was toggled to true.

---

### Post by coront on 2007-10-22
Maybe this could be related to the "82%" freeze at the installation some people were having (including myself). I just unplugged the cable and proceeded with the installation.

---

### Post by steelklvr on 2007-10-22
My upgrade didn't freeze though (it successfully completed whilst i was asleep). However, anything's possible...

---

### Post by Shazaam on 2007-10-22
Try this (in terminal)..
```
sudo dpkg --configure -a
```

Then
```
sudo apt-get update
```

Then try Synaptic again.

---

### Post by steelklvr on 2007-10-22
No sorry, the code you posted initiates a download but it doesn't progress past 0%.

However:

I have done some additional snooping around and have found the root of the problem.

A file located at 

/etc/resolv.conf is the problem. It currently is set to my router's IP address (10.1.1.1) however, if i change that value to my ISP's DNS server address, I can download from synaptic!

Code used to edit resolv.conf

```


sudo gedit /etc/resolv.conf


```

The problem with this method is that, every time I restart my connection or reboot my PC, resolv.conf is overwritten with 10.1.1.1 and i need to change the file every time.

UPDATE:

I have found the answer to permanently saving resolv.conf, funnily enough in ubuntuforums' own archives.

Ok, step 1, enter this code into a terminal:

```
 sudo gedit /etc/dhcp3/dhclient.conf

```

Step 2 - Edit this file by adding this line into it;

> supersede domain-name-servers server-ip1 server-ip2 

here is a portion of my file to show what it should look like

> #send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
**#supersede domain-name-servers server-ip1 server-ip2;**
#prepend domain-name-servers 202.27.158.40;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;

Step 3 - Save the file and everything should work fine if you changed the resolv.conf file mentioned above and haven't restarted your connection.

Optional - Step 4 -  If it still isn't working, try restarting the connection using this code ```
 sudo invoke-rc.d networking restart 
``` 

UPDATE (again...): Another option if any of the above is not working for saving changes to resolv.conf (from ubuntu's help system)

> The changes you make in /etc/resolv.conf
will be erased when you reboot your machine. If you want to
make this change permanent, you should install
resolvconf package from the Universe repository and
update the DNS information in the
/etc/resolvconf/resolv.conf.d/base
file provided by that package.

It is possible to download the package as long as you don't restart your pc or net connection after editing resolv.conf

All should be good.

CREDITS - Most of this solution came from a user called nixfaced from the archives.
If you are still having a problem please post in this topic, otherwise this seems to have been solved. 


Thank you for all your help,

---

### Post by coront on 2007-10-22
> **Shazaam said:**
> Try this (in terminal)..
```
sudo dpkg --configure -a
```

Then
```
sudo apt-get update
```

Then try Synaptic again.

I tried this with no result :(

---

