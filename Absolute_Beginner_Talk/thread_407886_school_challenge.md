---
title: "school challenge"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by crazyclown on 2007-04-12
I am taking a A+ course right for College.  We have installed new OS's on the machines.  Only two of us opted to but Linux on our machines.  Well he is going to try and hack my machine and will probably succeed, but what can I do to stop him.  I have given my user and the root 16 character passwords. What other suggestions do anyone have?  

The teacher knows we are going to have some fun and this is how I learned most of my Windows security by having someone hack my system.

---

### Post by sailor2001 on 2007-04-12
as long as you are not using sudo for extended periods of time, it becomes extremely hard to hack into.....and even more so if you are behind a router

---

### Post by solar george on 2007-04-12
Does 'he' have physical access to your machine?

---

### Post by phr0ze on 2007-04-12
Hack over a network or hack at the box? If it's over a network put in a firewall and make sure you aren't hosting VNC or anything else. If its at the box, I'd consider an encrypted volume, passwords on the BIOS and a physical lock on the case. Beyond an encrypted volume, there are too many ways in.

---

### Post by dacool25 on 2007-04-12
just wondering how do you go about encrypting a volume?

---

### Post by crazyclown on 2007-04-12
His access will be over the network and we are one the same switch.  He has Fedora loaded on his machine.  The encrypted volume is the only thing I could do to the machine.  THe professor will not allow BIOS password and no locks on the cases, due to other classes being taught in there to.

---

### Post by houstonbofh on 2007-04-13
Install fail2ban from the repositories, and configure it very tight.  Remove the root password, and only use sudo.

---

### Post by russell.h on 2007-04-13
Blacklist his IP.

---

### Post by crazyclown on 2007-04-13
Blacklist would not work, he has access to several Windows XP and 2000 machines in our class.  I know he will try to come in from on of them.  I would.

---

### Post by ghansel on 2007-04-13
Disable ssh root login?

---

### Post by hyper_ch on 2007-04-13
Hmmmm, ban the whole network except for the router's IP so that you get inet access...

ssh root login needn't to be disabled - by default openssh-server is not installed. If you did install it, then disable ssh root login...
There are several guides on encrypting drives/partitions :)

---

### Post by devnulljp on 2007-04-13
sudo aptitude install bastille
Also, install libpam-cracklib -- that will help you set secure passwords
and pam_abl -- to drop attackers

How about using pwgen to generate a good password? Or better still, block passwords on ssh 
and use only rsh keys? If you must use passwords, make sure they're not something like bob -- should look something like this: kf<Bj6oU#X72>rj?* (you'd be amazed how easy that kind of passwd will be to remember in a week or so of constant use). But rsh keys only is still more secure.
(*obviousy, don't use that one.)

Make sure you aren't allowing telnet or ftp on your machine (see bastille). 
Use denyhosts [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/) to auto block ips that try to break in.
Edit your sshd_config to allow only certain users (i.e. you, with a better user name than just your name), and certainy block access from  root (as well as users such as mysql, postgres, uest, www-user, etc.). 
use only ssh version 2 (not 1)

sshd_config changes:

PermitRootLogin no
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication no

That last part disables login via passwd and only allows you in over ssh with a key (see here: [http://www.g-loaded.eu/2005/11/10/ssh-with-keys/](http://www.g-loaded.eu/2005/11/10/ssh-with-keys/))

Set your machine so it doesn't respond to nmap scans or to pings or to anything else (bastille will help you do this) 

Firewall everything. change the ssh port (not really secure, but if nmap can't get a response from you it will be harder to figure out which port to come in on).
Disable anything you don't actually need to run (do you need apache? sendmail? etc.)
Diable all user accounts you don't need (sudo passwd -l <username>)
Put a password on grub (that's different from you user or root password....but then you've already disabled root right?)
Put a (different) password on single user mode
Put a bios boot password, prevent booting from cd/dvd/floppy/network, so even physical access shouldn't matter too much
Lock the case so s/he can't just jimmy out your drives and gain access thatway
Mount you system partitions read only, so even if s/he does get in, s/he can't change any system files.
install logwatch and tripwire, and set them to send you an alert on attack attempts
monitor /var/log/auth.log (logwatch should do that for you) 
chroot jails

You could always have some fun with a honeypot too: [http://packages.ubuntulinux.org/warty/admin/tinyhoneypot](http://packages.ubuntulinux.org/warty/admin/tinyhoneypot)

Failing that, turn the thing off, and encase it in concrete??

---

### Post by crazyclown on 2007-04-13
I will be trying these.  Thanks for the help.  I will pass along updates when something happens.

---

### Post by crazyclown on 2007-04-17
Well the machine is very secure, the NIC is bad.  Have to wait until the Prof. lets me T/S and replace it.   I used Live CD on another machine to make sure Ubuntu reconizes the NIC. 

The game must wait...

---

### Post by n3tfury on 2007-04-17
> **devnulljp said:**
> sudo aptitude install bastille
Also, install libpam-cracklib -- that will help you set secure passwords
and pam_abl -- to drop attackers

How about using pwgen to generate a good password? Or better still, block passwords on ssh 
and use only rsh keys? If you must use passwords, make sure they're not something like bob -- should look something like this: kf<Bj6oU#X72>rj?* (you'd be amazed how easy that kind of passwd will be to remember in a week or so of constant use). But rsh keys only is still more secure.
(*obviousy, don't use that one.)

Make sure you aren't allowing telnet or ftp on your machine (see bastille). 
Use denyhosts [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/) to auto block ips that try to break in.
Edit your sshd_config to allow only certain users (i.e. you, with a better user name than just your name), and certainy block access from  root (as well as users such as mysql, postgres, uest, www-user, etc.). 
use only ssh version 2 (not 1)

sshd_config changes:

PermitRootLogin no
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication no

That last part disables login via passwd and only allows you in over ssh with a key (see here: [http://www.g-loaded.eu/2005/11/10/ssh-with-keys/](http://www.g-loaded.eu/2005/11/10/ssh-with-keys/))

Set your machine so it doesn't respond to nmap scans or to pings or to anything else (bastille will help you do this) 

Firewall everything. change the ssh port (not really secure, but if nmap can't get a response from you it will be harder to figure out which port to come in on).
Disable anything you don't actually need to run (do you need apache? sendmail? etc.)
Diable all user accounts you don't need (sudo passwd -l <username>)
Put a password on grub (that's different from you user or root password....but then you've already disabled root right?)
Put a (different) password on single user mode
Put a bios boot password, prevent booting from cd/dvd/floppy/network, so even physical access shouldn't matter too much
Lock the case so s/he can't just jimmy out your drives and gain access thatway
Mount you system partitions read only, so even if s/he does get in, s/he can't change any system files.
install logwatch and tripwire, and set them to send you an alert on attack attempts
monitor /var/log/auth.log (logwatch should do that for you) 
chroot jails

You could always have some fun with a honeypot too: [http://packages.ubuntulinux.org/warty/admin/tinyhoneypot](http://packages.ubuntulinux.org/warty/admin/tinyhoneypot)

Failing that, turn the thing off, and encase it in concrete??

great post! some good security advice there.

---

### Post by Swab on 2007-04-17
> **crazyclown said:**
> Blacklist would not work, he has access to several Windows XP and 2000 machines in our class.  I know he will try to come in from on of them.  I would.

Blacklist the entire subnet?  Unplug the Ethernet cable?  No wait, remove power from the machine!

---

### Post by PilotJLR on 2007-04-17
> **Swab said:**
> Blacklist the entire subnet?  Unplug the Ethernet cable?  No wait, remove power from the machine!

Destroy all computers entirely - then they are unhackable! Keep everything important written in a notebook, hidden in your closet.   :p

---

### Post by Tundro Walker on 2007-04-17
I was going to recommend password-protecting GRUB, but the other poster beat me to it.  I think the best recommendation I've heard about security is that you don't have to make your computer unhackable (no system is unhackable)...you just have to make it so dang hard that folks will give up before they do.

I'm assuming you'll both be trying to hack each others computers during class.  But, if it's a case where he can try to hack it anytime via remote, it might be funny to (without him knowing), boot the machine to GRUB command-line and leave it there indefinitely.  Then, disconnect the monitor from the computer so it looks like its in suspend/sleep mode.  He'll see it on in class (thinking its in screensave / standby), and it'll still technically be hooked up to the network, since you won't disconnect the ethernet.  He'll try hacking it like it's fully running Ubuntu, and start cussing cause it's really not.

Or, boot it with a Windows Emergency Boot Disk...or an old Dos 6.0 disk.  Or, my personal favorite, Hactar, a little OS [SIZE=2]Alessandro Ghignola whipped up in his spare time...[/SIZE]

[http://anywherebb.com/hactar.html](http://anywherebb.com/hactar.html)

Your cohort will spend so much time trying to hack Linux without realizing you've booted a totally different OS, especially one like Hactar, which not many people have come across.  

When the jokes over, though, I think he'll have a hard time hacking your actual Linux install.  Well, a harder time then a Windows install...

---

### Post by kevinlyfellow on 2007-04-18
> **Tundro Walker said:**
> I was going to recommend password-protecting GRUB, but the other poster beat me to it.  I think the best recommendation I've heard about security is that you don't have to make your computer unhackable (no system is unhackable)...you just have to make it so dang hard that folks will give up before they do.


Putting a password on grub wouldn't do much, all it takes is a livecd.  I think the game is being played to only allow remote attacks.  A password on the bios would be much more effective if your looking to prevent a local attack.  Best way to protect your computer from a local attack: install your os and data on your pen drive and carry it around with you :-)

---

### Post by crazyclown on 2007-04-19
Well the Prof fixed the NIC while I was out of class.  So far other people in class want to see what it looks like

---

### Post by LaRoza on 2007-04-19
Take your computer off the network and unplug it.:)

---

### Post by crazyclown on 2007-04-19
> **russell.h said:**
> Blacklist his IP.

I just re-read this post.  I can blacklist the entire subnet.  I will try this.

---

### Post by lamalex on 2007-04-19
> **crazyclown said:**
> I just re-read this post.  I can blacklist the entire subnet.  I will try this.

that's not really beating him though, in reality you can't black list every hacker, play the game like you don't know he's doing it, not dirty tricks. you'll learn a lot about linux security.

---

### Post by jeffmetal on 2007-04-19
yeah banning the entire subnet or his ip is plain cheating. 

are there any rules for this like you must have certain services running. say webserver,ssh,telnet others?

if you dont at least give him something to target its a pretty pointless excercise.

---

### Post by johnny4north on 2007-04-19
i found this on line.. [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)  give this try.  it will be a step in the right direction.:)

---

### Post by .rdg on 2007-04-21
First of all - I wouldn't see encrypted drive as being in any way useful in this remote hack-in example - if your partitions are mounted during startup (and you give a password for it) they become accessable AFTER successful login to your machine. So - encryption is good when you want to protect from hdd theft (people can't break the passwd for each encrypted partition easily).

Second thing - you should start thinking protecting the outside first, then protecting the inside.

So first thing would be:

netstat -autn (can omit n - see man on netstat for what it does) | grep LISTEN

so you have a clear picture of what ports are open for connections

Then DO INSTALL sshd daemon - if these are games, you should make most of it, so at least in real situation you would know how to secure a server, not a desktop (which is so much easier).

As it goes for a ssh daemon - there would be few things you should do.
First  - go and configure /etc/ssh/sshd_config (some changes to that file were already described by devnulljp - really good info). Keep in mind these settings:

Port 22 - leave that, security through obscurity isn't always the best thing
Protocol 2 - DON'T use version 1 ssh protocol
Listen xxx.xxx.xxx.xxx - if you use subinterfaces bind ssh daemon to only 1 IP (not always the case, but good to know it's useful in some cases)

LoginGraceTime 20 - so the connection slot is only 20 seconds
PermitRootLogin no - obvious
StrictModes yes - see man
MaxAuthTries - see man also
AllowGroups somegroup - only the members of that group will be able to connect

PasswordAuthentication yes - while sometimes the keys are a good thing, they're NOT ALWAYS the right way

Now don't forget to create "somegroup" (or whatever the name you wish). Add your allowed users to that group (i prefer manually editing /etc/group and just adding the names of users there).

Then we set PAM. Go to /etc/pam.d/ and edit files:
su - settings for a su command
  here add the line 
  auth required pam_wheel.so - only members of "wheel" group are allowed to switch to root (good practice, but not so much useful for ubuntu - keep in mind though)

login - settings for local logins
  here add the line
  account required pam_access.so - /etc/security/access.conf file comes in; you can restrict who can connect from where (well in this case it's local anyway)

ssh - settings for ssh logins
  here add the line
  account required pam_access.so - same as above

So now we edit the mentioned /etc/security/access.conf file. It's self explainatory, but at least what you could do is add the line at the end like:

-:ALL EXCEPT somegroup:ALL

Don't forget to add an empty line after the one I gave there - it's a must. Better yet is to add a different group to a system and have your used added to both. Naturally you should use different groups in /etc/ssh/sshd_config and /etc/security/access.conf.

So now your sshd is more secure. Then there's a firewall. I don't see setting the Port 22 to something different the best option. It's much better to use some kind of firewall (well a frontend for iptables it is) - personally I chose shorewall. You should read some stuff about PortKnocking. The basic idea is - you have to connect to some strange port (like 43182; it doesn't have to be open) and then the firewall opens port 22 for you to connect. This way port 22 doesn't seem to be open for an attacker (port scanning won't show it as open), but it actually is. This alone would turn around most of the attackers.

So now you could say your ssh daemon is more secure. And only sshd. You could always add DenyHosts just to be extra sure - if someone finds your port to knock (hard to do) you would always use additional security by using TCP Wrapper (/etc/hosts.allow and /etc/hosts.deny comes in by using DH).

Next there are things like others told you already - bastille to tighten security, /etc/fstab (or /etc/crypttab for encrypted devices) for better security of your filesystem.

Useful trio is snort + logwatch + tripwire. This would be something you should keep in mind for EACH SERVER (I won't give a detail description as I still learn those things myself). Read about them - and read a lot.

Also - if you plan on launching some extra network services (httpd / email etc) always read about how to secure them and think if you need them on all IP addresses you use.

Whoa, that was a long write :) hope it's useful for more people.

---

