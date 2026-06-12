---
title: "Restricting access to selected network computers by iptables"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Hercules on 2006-12-03
I have a puzzle relating to iptables, and would appreciate any help!

I've got a home network containing a few computers, and the whole network has access to the internet via a router/modem.

There is a Linux computer on the network that acts as a file server, and I would like to limit which of the other computers on the home network can access its shared directories. The Linux computer also needs to access the internet for the usual tasks (web browsing, etc.)

I'm a relative with beginner with iptables, and am working out the best way to do the following in the Linux computer firewall ruleset:
1) Write a rule to filter out several computers by IP address
2) Order my rules such that it is still possible to access the web, etc.

Here are the relevant snippets from my rules. Does it look ok? I've included some comments which are the questions I am pondering!

> #---------------------------------------------------------------
# Seems sensible that this rule should go first?
#---------------------------------------------------------------

# Set the default policy for input to be drop
iptables -P INPUT DROP

#---------------------------------------------------------------
# I guess these rules should go next?
#---------------------------------------------------------------

# Allow loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow existing and related traffic
iptables -A INPUT -i eth0 -p tcp -m tcp -m state --state ESTABLISHED,RELATED -j ACCEPT

#---------------------------------------------------------------
# I guess the rules to filter out unwanted IP addreses should go
# next? If so, is there a way I can I filter out several specific
# IP addresses (but not a block) in one simple statement? I've
# tried using commas (as below) but that hasn't worked!
#---------------------------------------------------------------

# Only accept the IP addresses we want
iptables -A INPUT -i eth0 -s 192.168.0.10,192.168.0.20

#---------------------------------------------------------------
# And now that I know I am dealing with accepted IP addresses
# I can do the lower-level checks for http, https, ssh, etc.
# By the way, does it make a difference as to whether I specify
# the source or destination port? I've used source...
#---------------------------------------------------------------

# Allow http traffic
iptables -A INPUT -i eth0 -p udp -m udp --sport 80 -j ACCEPT

# Allow https traffic
iptables -A INPUT -i eth0 -p udp -m udp --sport 443 -j ACCEPT

# Allow ssh traffic
iptables -A INPUT -i eth0 -p udp -m udp --sport 22 -j ACCEPT


Any thoughts?

---

### Post by steve.horsley on 2006-12-03
You must use the destination port when filtering for service ports like HTTP, so those last 3 should use --dport instead.

Also, HTTP, HTTPS and SSH all use TCP and not UDP for their transport protocol.

There is an un-needed -m tcp in your line testing for RELATED,ESTABLISHED.

It would probably be easier if you were to use a GUI front-end such as firestarter or guarddog to create these condfigurations.

---

### Post by Hercules on 2006-12-03
Hi Steve, thanks for the reply.

Good point on the "UDP" and "-m tcp" mistakes. They were typos on my part (honest!), and my actual script on the Linux computer is correct in that respect. Although I did have "sport" instead of "dport" for ports 22, 80 and 443, so have changed that.

I believe there's also an unnecessary "--p tcp" in the RELATED,ESTABLISHED line, so have taken that out as well.

Also forgot to put a "!" and "-j DROP" on the IP line, and have added that in.

Here's the edited version:

> #---------------------------------------------------------------
# Seems sensible that this rule should go first?
#---------------------------------------------------------------

# Set the default policy for input to be drop
iptables -P INPUT DROP

#---------------------------------------------------------------
# I guess these rules should go next?
#---------------------------------------------------------------

# Allow loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow existing and related traffic
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

#---------------------------------------------------------------
# I guess the rules to filter out unwanted IP addreses should go
# next? If so, is there a way I can I filter out several specific
# IP addresses (but not a block) in one simple statement? I've
# tried using commas (as below) but that hasn't worked!
#---------------------------------------------------------------

# Only accept the IP addresses we want
iptables -A INPUT -i eth0 -s ! 192.168.0.10,192.168.0.20 -j DROP

#---------------------------------------------------------------
# And now that I know I am dealing with accepted IP addresses
# I can do the lower-level checks for http, https, ssh, etc.
# By the way, does it make a difference as to whether I specify
# the source or destination port? I've used source...
#---------------------------------------------------------------

# Allow http traffic
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT

# Allow https traffic
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 443 -j ACCEPT

# Allow ssh traffic
iptables -A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT

Thanks for the recommendations on the firestarter and guarddog GUIs - I'll have a look at them.

I think I'll persevere with the manual script for now (however dangerous that might be!) as I'm keen to understand how it all works. Having only been working with Ubunto for a week, I'm learning lots through all of this messing around, and am quite enjoying it.

---

### Post by steve.horsley on 2006-12-03
That looks good to me. But I'm no expert either.

I believe that guarddog is a KDE app and Firestarter is Gnome, but they both work. I'm less familiar with Firestarter, but guarddog I know creates a script called /etc/rc.firewall and you can read what it's doing in there. It's kind of long and hairy/scary.

For someone who's only been using Ubuntu for a week, you're really in at the deep end. Good luck, and enjoy.

---

