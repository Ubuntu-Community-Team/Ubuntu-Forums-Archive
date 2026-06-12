---
title: "Am I being attacked?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Hallvor on 2007-03-20
> Mar 20 07:15:01 hallvor-desktop kernel: [17314128.328000] Inbound IN=ra0 OUT= MAC=00:08:a1:8d:c6:57:00:40:10:20:00:01:08:00 SRC=86.135.98.97 DST=192.168.1.135 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=54966 DF PROTO=TCP SPT=4662 DPT=39194 WINDOW=64355 RES=0x00 ACK URGP=0 

Found this in my syslog. What does it mean? Is it an attack?

---

### Post by steve101101 on 2007-03-20
im not sure but overall linux in general is very safe compared to windows or mac.

---

### Post by PhatStreet on 2007-03-20
> **steve101101 said:**
> im not sure but overall linux in general is very safe compared to windows or mac.

No offense, but most people who have taken the time to educate themselves realize that, and no OS is bulletproof.

---

### Post by steve101101 on 2007-03-20
the key work is "GENERALLY" I never said that nothing ever happened or that it was bulletproof

---

### Post by sad_iq on 2007-03-20
Have you been using aMule? It appears like the source port used a lot by emule, amule...and the like!!! (I could be wrong though.)

---

### Post by Hallvor on 2007-03-21
No, you are not wrong. I use aMule all the time.

---

### Post by mcduck on 2007-03-21
> **Hallvor said:**
> Found this in my syslog. What does it mean? Is it an attack?

If it's just one entry from that address then consider it to be normal 'background noise' of the Internet. And as you can see the entry, that means it was blocked ;)

---

### Post by devnulljp on 2007-03-21
sad_iq beat me to it...those look like normal connections.
But, if you are worried about breakins (it happens, grep through your /var/log/auth.log file for fail) try denyhosts, which will boot an IP address if it tries too many times to log in without hte correct username/password. Easier to set up than the pam.d alternatives. Lots of other things you should consider...make sure root account is disabled, no root access via ssh, no telnet at all, use good passwords (and if you have multiple users, use pam_cracklib to enforce good passwords or rsh keys)--use pwgen to generate good unguessable passwords.
```
sudo apt-get install pwgen 
pwgen -nycs
```

---

### Post by Hallvor on 2007-03-21
Thanks. Will try that.

---

### Post by dv5237 on 2007-03-21
"sudo cat /var/log/auth.log | grep fail" gives me the following ouput:

Mar 21 07:52:50 edgyeft sshd[5593]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:52:53 edgyeft sshd[5597]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:52:56 edgyeft sshd[5601]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:52:59 edgyeft sshd[5603]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:03 edgyeft sshd[5607]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:06 edgyeft sshd[5609]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:09 edgyeft sshd[5613]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:12 edgyeft sshd[5617]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:15 edgyeft sshd[5619]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:19 edgyeft sshd[5623]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:22 edgyeft sshd[5627]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:26 edgyeft sshd[5629]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:29 edgyeft sshd[5633]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:41 edgyeft sshd[5639]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46

Does the output mean that someone was trying to acces my desktop?

---

### Post by mcduck on 2007-03-21
> **dv5237 said:**
> "sudo cat /var/log/auth.log | grep fail" gives me the following ouput:

Mar 21 07:52:50 edgyeft sshd[5593]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:52:53 edgyeft sshd[5597]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:52:56 edgyeft sshd[5601]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:52:59 edgyeft sshd[5603]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:03 edgyeft sshd[5607]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:06 edgyeft sshd[5609]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:09 edgyeft sshd[5613]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:12 edgyeft sshd[5617]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:15 edgyeft sshd[5619]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:19 edgyeft sshd[5623]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:22 edgyeft sshd[5627]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:26 edgyeft sshd[5629]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:29 edgyeft sshd[5633]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46
Mar 21 07:53:41 edgyeft sshd[5639]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=12.105.7.46

Does the output mean that someone was trying to acces my desktop?

Yes, someone from IP 12.105.7.46 tried to access your computer using SSH.

---

### Post by dv5237 on 2007-03-21
> **mcduck said:**
> Yes, someone from IP 12.105.7.46 tried to access your computer using SSH.

Is there something i should do or just ignore it? How did he/she "found" my computer?

---

### Post by h0ax on 2007-03-21
More than likely it's not a "he/she" but rather a bot that just runs down a predetermined set of IP addy's (you got to be a lucky one) -
They attempt to break into boxes remotely which have weak SSH passwords.
I eventually had to change the port on SSH because I must have been in a good IP-range where I would seriously get 100s of attempts a day.

I wouldn't worry about it if you have a strong password, and other steps you can do would be:
turn off ssh if you don't need it
change the port ssh uses

---

### Post by mcduck on 2007-03-21
> **h0ax said:**
> 
I wouldn't worry about it if you have a strong password, and other steps you can do would be:
turn off ssh if you don't need it
change the port ssh uses
In addition you could only set SSH to only allow connections from certain IP's (the ones that you need yourself), or configure your firewall to only allow connections from selected IP's to the SSH port.

---

### Post by dv5237 on 2007-03-21
Thanks for the responses. I got one more question concerning this subject. Is there a way i can check if someone has succesfully accessed to my desktop?

---

### Post by mcduck on 2007-03-21
> **dv5237 said:**
> Thanks for the responses. I got one more question concerning this subject. Is there a way i can check if someone has succesfully accessed to my desktop?

Just check the auth.log without grepping for failure, successful logins are also logged there. But if he/she/it would have succesfully logged on your machine he would most likely removed all traces of the attack, including the failed login attempts you now see.

---

### Post by julian67 on 2007-03-21
If you do use ssh then disable password log ins altogether and allow only  key authentication. If you allow password log in on ssh and  someone runs a brute force attack to gain your user name and succeeds they will then start on your password. If it even resembles a dictionary word or name they will probably get it and then have remote access to your PC. It would probably take them  2 entire seconds to realise it's a sudo set up and that root is powerless but 1st user is God. You will then be running Ubuntu rooty rooted instead of edgy eft ;)

Like the previous post says if you don't use it switch it off. Plenty of other distros install with it disabled by default and/or firewalled too. I know the Ubuntu line is that a firewall is not necessary but then it shouldn't install with ssh daemon up as default.  Seems to me that the security model can depend on a blameless  inexperienced user creating a strong password....brave/scary, take your pick.

edit: to check your PC after you disable/secure sshd you can install rkhunter and chkroot from the Ubuntu repos and scan for rootkits. They're very quick and easy tools to use. If you have any suspicion at all that your PC has been rooted I would back up personal data and format and reinstall offline and don't go online until you have disabled ssh. Use a strong password, make it from a phrase you can easily remember using the first letter of each word. Use lower & upper case, add symbols. i.e. a phrase like "My Ubuntu box got rooted on the 21st" could give you a password mUbgrot21:( 

Install a firewall. Guarddog is very easy to set up.

---

### Post by dv5237 on 2007-03-21
Thanks, some time ago i read something about ssh and key authentication ill look it up again and give it a try.

---

### Post by mcduck on 2007-03-21
> **julian67 said:**
> 
Like the previous post says if you don't use it switch it off. Plenty of other distros install with it disabled by default and/or firewalled too. I know the Ubuntu line is that a firewall is not necessary but then it shouldn't install with ssh daemon up as default.Ubuntu doesn't have SSH server by default, only client.

---

### Post by julian67 on 2007-03-21
> **mcduck said:**
> Ubuntu doesn't have SSH server by default, only client.

That's a relief. It seems the OP installed it then. It does seem that if it's installed from the repos it allows password log in by default. I know that's standard across different distros but as Ubuntu is by default not firewalled and is aimed to a large degree at new Gnu/Linux users that seems like an invitation to trouble. I have never worked out why Ubuntu doesn't install with pre-configured ip tables firewall and a nice gui front end and some docs to help out.  It wouldn't hurt.

---

### Post by mcduck on 2007-03-21
> **julian67 said:**
> That's a relief. It seems the OP installed it then. It does seem that if it's installed from the repos it allows password log in by default. I know that's standard across different distros but as Ubuntu is by default not firewalled and is aimed to a large degree at new Gnu/Linux users that seems like an invitation to trouble. I have never worked out why Ubuntu doesn't install with pre-configured ip tables firewall and a nice gui front end and some docs to help out.  It wouldn't hurt.
Most likely because there is no need for it unless you install some server yourself. In default install there's no applications listening to any port so there's no need for a firewall.

---

### Post by devnulljp on 2007-03-22
Well, someone using an AT&T WorldNet Services ATT IP address was trying to log into your box via ssh.
To see details of the attempts, try: 
```
grep 12.105.7.46 /var/log/auth.log
```
and 
```
grep Invalid /var/log/auth.log
```

My guess is it will look something like this:
```

Mar 14 15:30:50 localhost sshd[7113]: Did not receive identification string from 12.105.7.46
Mar 14 15:33:46 localhost sshd[7121]: Invalid user bob from 12.105.7.46
Mar 14 15:33:48 localhost sshd[7123]: Invalid user foo from 12.105.7.46
Mar 14 15:33:52 localhost sshd[7125]: Invalid user pgsql from 12.105.7.46
Mar 14 15:33:55 localhost sshd[7127]: Invalid user admin from 12.105.7.46
Mar 14 15:33:58 localhost sshd[7129]: Invalid user root from 12.105.7.46
Mar 14 15:34:00 localhost sshd[7131]: Invalid user ftp from 12.105.7.46
```

You might see something like this:

```
/var/log/auth.log.0:Mar 18 08:24:58 localhost sshd[11732]: reverse mapping checking getaddrinfo for mail2.cruisesystem.com failed - POSSIBLE BREAKIN ATTEMPT!

```
These kind of breakin attempts are very common (I've seen pages of attempts from a single IP on an old unprotected RedHat box).
 
With denyhosts, they'll only be able to try a few times then any further connections will get dropped and your logs will look like this:

```
Mar 21 11:23:26 localhost sshd[8261]: refused connect from ::ffff:12.105.7.46 (::ffff:12.105.7.46)
```

For hardening, try bastille (it's in universe I think) and denyhosts, use cracklib to make sure you have good passwords, I'd also disable the root account, add any users that don't need to have ssh access (and root) to  /etc/ssh/sshd.deny, depending on how many users you have you may want to specifically add those users that do requires ssh access to /etc/ssh/sshd.allow (or you can specify users that do not have ssh access by adding a line to /etc/ssh/sshd_config like this:

DenyUsers       root user1 user2 user3

Lots of ways to do it.

---

### Post by devnulljp on 2007-03-22
> **h0ax said:**
> I eventually had to change the port on SSH because I must have been in a good IP-range where I would seriously get 100s of attempts a day...change the port ssh uses
Don't know I'd trust security through obscurity -- a quick nmap scan of your subnet would reveal the port. 
Better to drop the IPs those bad login attempts are coming from---try denyhosts or pam_abl, as well as all the other usual security stuff (good passwords or only rsh keys, disable root account, deny root ssh login, etc.)

---

### Post by brennydoogles on 2007-04-11
> **mcduck said:**
> Yes, someone from IP 12.105.7.46 tried to access your computer using SSH.

How about this one?
```
Apr 10 21:28:28 brennylinux sudo: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=brendon

```

---

### Post by arron on 2007-04-11
> **devnulljp said:**
> 
 With denyhosts, they'll only be able to try a few times then any further connections will get dropped and your logs will look like this:

Thanks for the info.  This is a great app, i already have 8 on my deny list!  Very useful i think.

Can you feed this into a sniffer to sniff the ip that scanned you?  I see where it feeds the IP into another program, i just don't know any prompt scanners/sniffers.  Even just to say hey i see you to the hacker, it don't have to do anything really, just scan the ports or something, or is this asking for trouble?

---

### Post by arron on 2007-04-11
ok, found one called nmap.  simple enough, but is this asking for trouble?

---

### Post by Patrick K on 2007-04-12
> **julian67 said:**
> ... Ubuntu is by default not firewalled... 
Iptables are installed by default. The Firestarter frontend isn't. There is a iptables man page available, too.

---

### Post by arron on 2007-04-12
WOW !  My list is up to 30 or so, this thing is really working!  I recommend this to anyone with any kind of server running.

Once again thanks for this info for denyhosts!

---

### Post by brennydoogles on 2007-04-12
> **brennydoogles said:**
> How about this one?
```
Apr 10 21:28:28 brennylinux sudo: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=brendon

```

Was this an attack, or some sort of failed login attempt of my own??

---

### Post by FuriousLettuce on 2007-04-12
I'm no expert, but to me it looks like you failed a sudo authentication - you just typed your password in wrong.

---

### Post by julian67 on 2007-04-15
> **Patrick K said:**
> Iptables are installed by default. The Firestarter frontend isn't. There is a iptables man page available, too.

Yes it's in every distro because it's part of the Linux kernel. But in Ubuntu it isn't configured to do much by default. It might be a better idea to have a gui config tool as part of the default install and to have only dhcp client, http, https, ftp, pop3, secure pop3, imap etc allowed by default with everything else blocked. A gui frontend might be made fairly simple, perhaps to mimic personal firewalls in Windows, and anyone needing more control has a choice of tools for iptables already available. 

For people behind a router it's not such a big deal but there are also plenty of people using cable modems (unlike a router these offer no protection) and even isdn and dial up, they should have a pre-configured firewall out of the box. Ubuntu and other distros respond to pings by default so they are visible online. And it doesn't take long after a new install for people to start installing new stuff and running services maybe without even realising and I also think it might be unrealistic to expect new users to be using truly strong passwords.

---

