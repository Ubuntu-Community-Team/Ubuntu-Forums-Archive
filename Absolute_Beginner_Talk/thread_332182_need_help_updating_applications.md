---
title: "need help updating applications"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Tanchelm on 2007-01-05
I attempted to update when I added universe and multiverse software sources however the update failed.  From terminal I tried the following

tanchelm@edgy:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                                               
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                             
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_US                                    
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Translation-en_US                              
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_US                                
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/multiverse Translation-en_US                              
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)]

I recently got Firefox working by disabling IPV6, 

to modprobe.d I have added 

# following three lines added by tanchelm to disable IPV6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
# alias net-pf-10 ipv6 ======= original line #ed by tanchelm

any help would be appreciated - thanks

---

### Post by scrooge_74 on 2007-01-05
Try pinging those servers, try using other servers to update, are those servers in australia? You may being affected by the communications problems in Asia do to the quake in Taiwan

---

### Post by Tanchelm on 2007-01-12
I had the option to use Australia as a server location, but I haven't seen that option now for about 6 days.  I can choose between 'Main' and 'US' servers but neither allow me to update - 

I could not ping the above listed addresses

---

### Post by Delkster on 2007-01-12
> **Tanchelm said:**
> Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

If I interpret that at all correctly, for some reason it seems to think that the IP address of security.ubuntu.com (and also the other servers) is 1.0.0.0, which is definitely not correct.

Do other network connections work? Could you post the contents of your /etc/hosts file?

---

### Post by Tanchelm on 2007-01-12
how do I get a copy of the /etc/hosts file?

---

### Post by Delkster on 2007-01-12
> **Tanchelm said:**
> how do I get a copy of the /etc/hosts file?

You can open it in Gedit, and then copy and paste the contents. Either browse to /etc in the file browser and locate the hosts file, or enter the following command in the terminal:
```
gedit /etc/hosts
```

(Note that this will open the file only for viewing, not for editing, since modifying it would require administrative privileges.)

---

### Post by Tanchelm on 2007-01-12
Thanks Delkster, 

the contents of /etc/hosts is as follows:

127.0.0.1	localhost
127.0.1.1	edgy

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Delkster on 2007-01-12
There seems to be something quite wrong, but I can't really figure out immediately what it could be. Hopefully someone who's in a sharper mood (I'm not, not right now anyway) will come in.

Edit: I mean that there's nothing with the hosts file that would immediately strike me as wrong, so there's probably a problem somewhere else.

---

### Post by Tanchelm on 2007-01-12
I had to disable IPV6 so I could use Firefox - would this cause problems... I am guessing yes - Ubuntu servers would probably require IPV6 or it wouldn't be included in the ubuntu package... I will play around with my IPV6 settings and see if this helps.  I will be eagerly awaiting any further help - and if I manage to jag a fix myself I'll let anyone interested know! until then ](*,)

---

### Post by jvc26 on 2007-01-12
I dont think its is a problem with the hosts - i checked yours out with mine and they are the same and mine is functional.
Il

---

### Post by stijn_pol on 2007-01-12
Doesn't this look like a DNS problem? ( check resolv.conf )
Do you have internet connection in other programs?

---

### Post by shareMenaPeace on 2007-01-12
This reminds me of updateing my hosts file aswell, to block ads et cetera.

[http://en.wikipedia.org/wiki/Hosts_file](http://en.wikipedia.org/wiki/Hosts_file)
Here is 1 example, if someone knows a good hosts file with 70.000 or more entrys, than please post a link
[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

---

### Post by scrooge_74 on 2007-01-12
> **Tanchelm said:**
> Thanks Delkster, 

the contents of /etc/hosts is as follows:

127.0.0.1	localhost
127.0.1.1	edgy

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Check your resolv.conf file

you can put in there Open DNS servers, that may help

nameserver 208.67.220.220
nameserver 208.67.222.222

---

### Post by Tanchelm on 2007-01-12
i added the suggested nameservers but still unable to update software.
I can connect to internet on firefox and post this message

---

### Post by scrooge_74 on 2007-01-12
there is something wrong with the servers you are using if you can connect to the internet with no problem

---

### Post by Tanchelm on 2007-01-13
surely not all servers?/??:-?

---

### Post by Delkster on 2007-01-14
> **scrooge_74 said:**
> there is something wrong with the servers you are using if you can connect to the internet with no problem

The problem seems to be that for some reason apt tries to connect to a completely wrong address.

Tanchelm, could you enter the following command in the terminal and report the results?
```
host security.ubuntu.com
```

---

### Post by Tanchelm on 2007-01-14
I decided that if I'm going to invest some time into learning the ins and outs of Ubuntu I should opt fot the Long Term Support so I installed Dapper Drake and formatted hard drive.

an error in loading when it could not access security updates.

From what I learned from my experience in Edgy I did the following:

1 changed the Grub so Windows XP is the default (for other members of my family)
2 disabled ipv6 in Firefox (about:config) as I could not connect to the net and this fixed the problem.
3 changed resolv.conf nameserver from 10.1.1.1 to 208.67.220.220 & 208.67.222.222

I was then able to do the updates and instal other programs.  :D 

why does my resolv.conf revert back to nameserver 10.1.1.1 everytime I reboot - even if I save it? actually I don't care why - I just want to stop it reverting back to 10.1.1.1

---

### Post by exile on 2007-01-14
Are you using DHCP or static IP? It sounds to me that 10.1.1.1 is something that an adsl router appliance would specify.

Can you post up your /etc/network/interfaces?

---

### Post by Tanchelm on 2007-01-14
/etc/network/interfaces is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Delkster on 2007-01-14
> **Tanchelm said:**
> why does my resolv.conf revert back to nameserver 10.1.1.1 everytime I reboot - even if I save it? actually I don't care why - I just want to stop it reverting back to 10.1.1.1

Do you have a home router, a switch or something like that sharing an internet connection? Judging by the interface configuration the computer is set to obtain an IP address and settings automatically via DHCP, so if your router is also acting as a DHCP server for the internal network, that's probably where the DNS settings are coming from on every boot.

You could try configuring your router so that the name server address it passes on via DHCP is one of those you know to work. It may be that it's now set to give the DHCP clients its own address for DNS.

I still don't completely understand why other things would work but not apt, though.

---

### Post by Tanchelm on 2007-01-14
I have an adsl modem (D-Link DSL-502T) between my computer and the telephone line all connected by hardwire (not wireless) connected by ethernet to my computer - not USB.

I don't want to play around with the modem too much - I'd have a sad time if others could not get WIndows XP working on the net because I changed something to make Ubuntu work.  I guess for the time being I will have to manually change nameserver each time I need to download software and updates.

I'll keep checking this thread to see if anyone comes up with a solution to this prob.... now for my next trick!

my next task is to be able to get Amarok or Soundjuicer (not sure which I will choose yet) to get a few thousand MP3s from my Windows drive.  so I'm hunting the forum to see how it's done!!!

---

### Post by stijn_pol on 2007-01-14
resolv.conf changes at boot, because of a make_resolv_conf method in /sbin/dhclient-script.
You can comment the content of this method, put # for each line.
I believe there is a better way to disable this automated resolv.conf but don't remember, you could search the forum, but this did work for me.
grtz

---

### Post by scrooge_74 on 2007-01-14
my resolv.conf has the details of other DNS server I put myself and there still there

---

