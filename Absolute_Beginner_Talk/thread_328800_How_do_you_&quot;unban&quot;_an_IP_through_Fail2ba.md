---
title: "How do you &quot;unban&quot; an IP through Fail2ban?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-31
I had setup fail2ban to ban ips indefineteley after 3 unsuccessful trials. Well, I usually connect to my ubuntu box from work through SSH and use PuTTY since I am on an XP machine there.
I was trying to set up an rsa-key login the other day which Putty wouldn't take as a key and my sshd didn't like because of the opposing formats (OpenSSH and SSH.com - i think).. anyways.. I apparently tried 3 time to login ands failed, hence my ip from work is banned... I feel stupid for asking this.. How do I unban this in fail2ban?

---

### Post by hyper_ch on 2006-12-31
I use denyhosts for that... and denyhosts stores the IPs in /etc/hosts.deny .... I assume fail2ban does the same... well, it may not but you can have a look whether it does :)

---

### Post by habtish on 2006-12-31
Nothing there

---

### Post by m4rqz on 2007-02-28
Don't know if this problem was solved or not, but I think fail2ban uses iptables to ban hosts. Check your iptables config.

---

### Post by 7echno7im on 2007-06-21
yes, fail2ban stores them in the iptables, user iptables -L

BUT
how do you ban indefinitely without using 999999999999999, is there a better syntax because 9999999999999 seconds will come someday, ESPECIALLY if I am using ubuntu server ;)
I am lost after that.  I am having some problems removing iptable entires, can someone help?  I know this is elementary, but I am still new at this.  I have read some posts and none see to help.

Also

I use webmin to manage my server, I see under networking that Linux Firewall is listed, I am assuming that is just a front end module to your iptables, but I am not seeing any of my entries there...

my question is, is there a webmin module that will allow me to edit and view my iptables?  The same way that I can see them listed by running iptables -L?

Thanks in adavce for your help

7im

---

### Post by St. Coin on 2007-07-18
7echno7im: try the value -1

- St. Coin

---

### Post by m2.g5ru6y7s on 2008-01-16
steps to unban banned user:
become root
su
iptables -L
look at the Chain fail2ban-ssh
notice the ip address to unban and count at which line number this is.
e.g.:
Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
DROP       0    --  61.236.117.xxx      anywhere            
DROP       0    --  61.236.117.yyy      anywhere
RETURN     0    --  anywhere             anywhere       
execute the following command:
iptables -D fail2ban-ssh <linenum>
if you want to unban user 61.236.117.yyy use:
iptables -D fail2ban-ssh 2

hint:
When the banned host is youself (localhost), no ip address is shown but a rare name for example:
c98xxx.upc-c.chello.nl
This is your own host.

---

### Post by x3dfxjunkie on 2008-03-28
> **St. Coin said:**
> 7echno7im: try the value -1

- St. Coin

I like the simplicity of this idea, I'll be giving it a shot later on after I (hopefully) get this other question answered:

Is there a way, without having to hack the code, to tell fail2ban **not** to unload/unban IP's when exiting?

The reason I ask is I had setup a custom apache rule to ban IP's that try to use some sort of cross-site attack or remote includes on our sites, but after about an hour fail2ban was dying for some as yet undetermined reason.  Of course, this then leaves the system vulnerable (sort of) again.

I don't have SSH open to the public on this target server, and (to date) hasn't been found to be vulnerable to the vast majority of these mostly scripted attacks.  This is mainly a prevention method, as well as a way to limit the number of records I have to sift through in snort.

---

### Post by Oldsoldier2003 on 2008-03-28
try -1 but seriously 9999999999999 seconds is more years than you or your server will be alive unless my math is waaaaaaaaaaaaay off this morning. 31K years....

---

### Post by x3dfxjunkie on 2008-03-31
After playing around with the config, -1 didn't work (at least for my setup).  Fail2ban would start, but never actually find anything to ban.

On a side note, I seem to hit a cap of some sort on how many addresses can be banned at once.  It's only able to add 71 items to iptables.  I can add more to the table manually, so it doesn't appear to be an iptables limitation.

---

### Post by Fireal on 2008-05-07
> **m2.g5ru6y7s said:**
> steps to unban banned user:
become root
su
iptables -L
look at the Chain fail2ban-ssh
notice the ip address to unban and count at which line number this is.
e.g.:
Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
DROP       0    --  61.236.117.xxx      anywhere            
DROP       0    --  61.236.117.yyy      anywhere
RETURN     0    --  anywhere             anywhere       
execute the following command:
iptables -D fail2ban-ssh <linenum>
if you want to unban user 61.236.117.yyy use:
iptables -D fail2ban-ssh 2

hint:
When the banned host is youself (localhost), no ip address is shown but a rare name for example:
c98xxx.upc-c.chello.nl
This is your own host.

Also, I had to clear out the instances of the recently unbanned ip from the program's log file (i.e. clear out XXX.XXX.X.XX from /var/log/apache2/error.log for apache2 or /var/log/auth.log for ssh) or fail2ban would "reban" them after a restart.

---

