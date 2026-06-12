---
title: "PPPoE Issue With Non-Standard Settings Required by ISP"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by TAfricanski on 2007-02-02
Hi guys! It's my first really serious attempt to start using Linux, as last time I tried I mixed an Ext3 partition with a FAT32 one...
However, now I am backed with at least basic knowledge and have easily set up an Edgy/XP dual boot system with GRUB on a diskette. The last issue I can't handle is the fact that my ISP requiers me to set the following lines in the /etc/ppp/pppoe.conf file:

ACNAME=Day1-PPPoE

SERVICENAME=home-unl


I tried to find the above mentioned file after configuring PPPoE in the way explained in the support page of Ubuntu, but the file does not seem to exist.
I know the answer probably is 'RTFM', but nothing there seems to work. I've been trying for more than a month now...

Under XP I create a new PPP broadband connection using the 'Create new connection' wizard, then right-click the connection, open properties and change the Service name in the General page to 'home-unl'. I connect to the ISP via a LAN, plugged into my Eth1, over which a PPPoE connection is established.
That's all I know about my connection.
Please, if someone could tell me how to run it under Ubuntu, it will be a great help!!!

---

### Post by Stemp on 2007-02-02
If you used **pppoeconf** to create a connexion, you have a configuration file in :

/etc/ppp/peers/dsl-provider

---

### Post by TAfricanski on 2007-02-02
I've tried editing this file by simply adding the lines ACNAME=Day1-PPPoE and SERVICENAME=home-unl but this did not help and I got an error message saying that these were unknown commands or something like this.
I suppose this is the file I'll need to change but I have absolutely no idea what to do with it ;)

---

### Post by Stemp on 2007-02-02
Apparently it's a little bit more complicated.
Edit you dsl-provider and add this line in the beginning :
```
pty "/usr/sbin/pppoe -I eth0 -T 80 -S service_name -C ac_name"
```

I didn't try it so I hope it will work for you ;)

---

### Post by TAfricanski on 2007-02-02
This did not work but at least the error message has changed :D
I am pasting the 'dsl-provider' file before and after editing, the error message I get and the file 'provider':

dsl-provider before editing:
```
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth1
user "tafricanski088"
```

dsl-provider AFTER editing:
```
# Minimalistic default options file for DSL/PPPoE connections

pty "/usr/sbin/pppoe -I eth0 -T 80 -S home-unl -C Day1-PPPoE"
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth1
user "tafricanski088"
```

The error message:
```
root@user-desktop:~# pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
root@user-desktop:~# 
```

provider:
```
# example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "myusername@realm"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T ********"

# Serial device to which the modem is connected.
/dev/modem

# Speed of the serial line.
115200

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth
```


I tried to change the /dev/modem string in provider file to eth1 and ppp0 but none of these helped. However, I was just guessing ;)

---

### Post by Stemp on 2007-02-02
```
pon dsl-provider
```

---

### Post by TAfricanski on 2007-02-02
```
root@user-desktop:~# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@user-desktop:~# ping www.ubuntu.com
ping: unknown host www.ubuntu.com
root@user-desktop:~# plog
Feb  2 21:12:44 user-desktop pppd[5646]: Plugin rp-pppoe.so loaded.
Feb  2 21:12:44 user-desktop pppd[5648]: pppd 2.4.4 started by root, uid 0
Feb  2 21:12:44 user-desktop pppd[5648]: PPP session is 1224
Feb  2 21:12:44 user-desktop pppd[5648]: Using interface ppp0
Feb  2 21:12:44 user-desktop pppd[5648]: Connect: ppp0 <--> eth1
Feb  2 21:12:44 user-desktop pppd[5648]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Feb  2 21:12:44 user-desktop pppd[5648]: CHAP authentication failed: 8^TM-\M-7pbM-oM-7^F
Feb  2 21:12:44 user-desktop pppd[5648]: CHAP authentication failed
Feb  2 21:12:44 user-desktop pppd[5648]: Connection terminated.
root@user-desktop:~# 
```

Looks like I have a new problem?

---

### Post by Stemp on 2007-02-02
> Looks like I have a new problem?

Edit your /etc/ppp/pap-secrets and you should see a line like :

```
"user@provider" * "password"
```

verify it

---

### Post by TAfricanski on 2007-02-02
> verify it

I know it does not make sense, but they are correct! Both my password and username are correct... Pasting the pap-secrets file with my password substituted by 'correct_password':

```
# LIC: GPL
# Edit this file and place it in /etc/ppp/pap-secrets

#User			#Server		#Password	#IP
tafricanski088	*		correct_password	*

# Replace bxxxxx@sympatico.ca with your Sympatico user-ID
# Replace my_password with your Sympatico password

# For Magma, use xxyyzz@magma.ca

"tafricanski088" * "correct_password"
```

---

### Post by Stemp on 2007-02-02
I don't understant your file, it's not like it must be.
Are you sure you used **sudo pppoeconf** to create it ? 
Here is my file /etc/ppp/pap-secrets

```
#
# /etc/ppp/pap-secrets
#
# This is a pap-secrets file to be used with the AUTO_PPP function of
# mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option
# which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)
# after a user has passed this file. Don't be disturbed therefore by the fact
# that this file defines logins with any password for users. /etc/passwd
# (again, /etc/shadow, too) will catch passwd mismatches.
#
# This file should block ALL users that should not be able to do AUTO_PPP.
# AUTO_PPP bypasses the usual login program so it's necessary to list all
# system userids with regular passwords here.
#
# ATTENTION: The definitions here can allow users to login without a
# password if you don't use the login option of pppd! The mgetty Debian
# package already provides this option; make sure you don't change that.

# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password



"euxxxxxxxx@tele2.fr" * "xxxxxxxx"

```

of course xxxxxxxx is my real password ;)

---

### Post by TAfricanski on 2007-02-02
Well I just replaced the contents of my pap-secrets file with yours, in the last line I wrote my username and password in the correct places and then... :

```
root@user-desktop:~# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@user-desktop:~# ping www.ubuntu.com
ping: unknown host www.ubuntu.com
root@user-desktop:~# plog
Feb  2 23:03:44 user-desktop pppd[4870]: CHAP authentication failed: 8M-TM-[M-7p"M-oM-7^F
Feb  2 23:03:44 user-desktop pppd[4870]: CHAP authentication failed
Feb  2 23:03:44 user-desktop pppd[4870]: Connection terminated.
Feb  2 23:03:48 user-desktop pppd[3456]: PPP session is 954
Feb  2 23:03:48 user-desktop pppd[3456]: Using interface ppp0
Feb  2 23:03:48 user-desktop pppd[3456]: Connect: ppp0 <--> eth1
Feb  2 23:03:48 user-desktop pppd[3456]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Feb  2 23:03:51 user-desktop pppd[3456]: CHAP authentication failed: 8^TM-\M-7pbM-oM-7^F
Feb  2 23:03:51 user-desktop pppd[3456]: CHAP authentication failed
Feb  2 23:03:51 user-desktop pppd[3456]: Connection terminated.
root@user-desktop:~# 
```

I hate my ISP... :\

---

### Post by Stemp on 2007-02-02
Excuse me but no more ideas :( sorry

---

### Post by TAfricanski on 2007-02-02
> **Stemp said:**
> Excuse me but no more ideas :( sorry

Thank you very much for your efforts! Good night from me for today.

Please, if someone has solution, help, because no matter what a wonderful OS Ubuntu is, it is not suitable for work without access to the Internet...

---

### Post by TAfricanski on 2007-02-03
Is there a reason why noone is writing? Is it because it is Saturday or because I should have posted this in the networking section for advanced users?

---

### Post by shareMenaPeace on 2007-02-03
Maybe run again

pppoeconf with the default values and NO password?

Than add the additions again.

---

### Post by TAfricanski on 2007-02-05
Nope. Didn't help. :( Same error messages. 

How can I bring this thread to the attention of other advanced users not reading this section of the forum without spamming?

---

### Post by TAfricanski on 2007-02-07
Feeling pretty lonely here... :(

---

### Post by randiroo76073 on 2007-02-07
You might try posting in the "Networking and Wireless" section of forums, don't forget to link back to this thread.  Sometimes posting in two places will find you an answer :)

---

### Post by TAfricanski on 2007-02-08
> **randiroo76073 said:**
> You might try posting in the "Networking and Wireless" section of forums, don't forget to link back to this thread.  Sometimes posting in two places will find you an answer :)
Done more than a day ago but no answers yet :(

[http://ubuntuforums.org/showthread.php?t=355377]("http://ubuntuforums.org/showthread.php?t=355377")

---

