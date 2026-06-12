---
title: "Firestarter gui won't start... (no icon)"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by TypeM on 2007-07-27
hi, this is my first post and i'm trying out ubuntu 7.04. and have problem with not getting the firetarter icon to show  at login.  i have followed diffrent "howto's" 

[HOWTO: Load Firestarter (Firewall) when session starts.]("http://ubuntuforums.org/showthread.php?t=26483") >  HOWTO: Load Firestarter (Firewall) when session starts.
These two simple steps will allow you to start Firestarter (Firewall) automatically right after you login. (Only for Gnome.)

My system is entirely in Spanish so some translations might not be correct.

First of all, since Firestarter requires sudo privileges to be started, we will add it to /etc/sudoers:

Code:

export EDITOR=gedit && sudo visudo

and add the following string at the bottom:

Code:

username ALL=NOPASSWD:/usr/sbin/firestarter

where "username" is YOUR OWN user name.

Now let's add it to the session.
Open "System->Preferences->Sessions" and click the tab "Start up programs" (the last).
Click the "Add button" and add the following string:

Code:

gksudo /usr/sbin/firestarter

This is all. Next time you start

and this ["How can I get Firestarter to load automatically when I log in as a regular user?"]("http://www.fs-security.com/docs/faq.php#trayicon")

I have in the past used 5.10 and up graded that one to 6.06LTS and there it work's!!! but i cant get it to work in 7.04. (on an new computer) 

ihave tried this command```
sudo /etc/firestarter/firestarter.sh status
``` and get that "Firestarter is running..."   if i now tries to start firestarter, nothing happens. if i instead comment out this > username ALL= NOPASSWD: /usr/bin/firestarter  i can start firestarter (clicking in menu) but need to type password.

Does anyone have a clue whats wrong?

(sorry if my english is bad)

/TypeM

---

### Post by p_quarles on 2007-07-28
If you can get it to run after typing your password, then Firestarter is working properly.

Here's the thing: you don't actually want Firestarter to load when you boot the system. Firestarter is not a firewall -- it's a firewall configuration utility. Whenever you set a rule in Firestarter, it becomes part of your firewall, and stays there, regardless of whether Firestarter itself is running. 

Also, Firestarter runs as the root user, so it's actually a security *vulnerability* to have it running when you're not changing firewall rules. 

If you want to monitor network traffic, there are other applications available for that, like Etherape and Wireshark. Despite the how-tos you read, running Firestarter all the time is a really bad idea.

---

### Post by por100pre1 on 2007-07-28
> **p_quarles said:**
> If you can get it to run after typing your password, then Firestart is working properly.

Here's the thing: you don't actually want Firestarter to load when you boot the system. Firestarter is not a firewall -- it's a firewall configuration utility. Whenever you set a rule in Firestarter, it becomes part of your firewall, and stays there, regardless of whether Firestarter itself is running. 

Also, Firestarter runs as the root user, so it's actually a security *vulnerability* to have it running when you're not changing firewall rules. 

If you want to monitor network traffic, there are other applications available for that, like Etherape and Wireshark. Despite the how-tos you read, running Firestart all the time is a really bad idea.
[B]
Thanks for the advice![/B] I have read a lot about it, but your explanation was above the rest. Again thanks for the advice. :)

---

### Post by TypeM on 2007-07-28
Thanks for the explanation... needed that one :)  

I now have removed  the entry in visudo 
> username ALL=NOPASSWD:/usr/sbin/firestarter

i have also removed the "autostart" entry in session. and tried the "sudo /etc/firestarter/firestarter.sh status" command after i reboot, i still get the answer that "Firestarter is running..." anything i missed ? or is it the answer that the firewall (iptables) is up and running. If not how can i check if the firewall (ip tables is running or get it running).

---

### Post by p_quarles on 2007-07-28
My understanding is that if you install Firestarter from the Ubuntu repositories, it continues to run as its own user, in the background. That way, any rules you have set up are persistent. Nothing to worry about.

IPtables is very different from a Windows-style firewall -- it's built in to the OS, and it basically gives your system a series of rules about which ports can accept incoming traffic, from whom, and for what services. If you do nothing to it, and aren't running any publically available services (ssh-server, ftp, web server, etc.), all your ports are closed -- meaning that you are for all intents and purposes invisible.

Of course, a really sophisticated hacker could still break in, but it's still a better software firewall than any available for Windows. 

Hope this helps.

---

### Post by TypeM on 2007-07-29
Yes, i installed from repository. 

I'm "damaged" from windows use :) i want to know when something knocks om my door (in or out) and i thought that i could use firestarter as a alert tool. the tools that was suggested Etherape and Wireshark looks a bit complicated for my need(want some thing simple).

Is it smarter to uninstall firestarter and install iptables only instead ? As i understand so are firestarter only a rule creator and iptables (firewall) installed with it and run in the backround.

---

### Post by pistcivet on 2007-07-29
> **TypeM said:**
> Yes, i installed from repository. 

I'm "damaged" from windows use :) i want to know when something knocks om my door (in or out) and i thought that i could use firestarter as a alert tool. the tools that was suggested Etherape and Wireshark looks a bit complicated for my need(want some thing simple).

Is it smarter to uninstall firestarter and install iptables only instead ? As i understand so are firestarter only a rule creator and iptables (firewall) installed with it and run in the backround.

Iptables is built in to the kernel. Firestarter is just as easy way to configure iptables.
Firestarter is great for that purpose, but once iptables is configured, you don't need Firestarter anymore.
(until the next time you want to change the configuration of iptables)
If you want to use Firestarter to monitor blocked traffic, please go right ahead and use it that way.
Its just isn't necessary, so most of us don't bother.

---

### Post by p_quarles on 2007-07-29
I'll second most of what pistcivet says. IPtables is indeed part of the kernel, and it offers really good protection right out of the box. The only reason to configure it is if you want to start running network or internet services.

I'll say again, though, that in many cases it can be risky to run Firestarter to monitor traffic. Every book or tutorial on security that I've read says that whenever you run a process as the root user, you're opening yourself up to some attacks. That said, you will probably be okay as long as you're not running services. If you have anything that opens yourself to the internet -- an e-mail server, apache, ssh, ftp -- you don't want to keep it running.

Of course, Wireshark and Etherape both also need to run as root for full functionality, but this is somewhat safer, since they only monitor traffic, and cannot be used to change port access rules.

---

### Post by pistcivet on 2007-07-29
> **p_quarles said:**
> I'll second most of what pistcivet says. IPtables is indeed part of the kernel, and it offers really good protection right out of the box. The only reason to configure it is if you want to start running network or internet services.

I'll say again, though, that in many cases it can be risky to run Firestarter to monitor traffic. Every book or tutorial on security that I've read says that whenever you run a process as the root user, you're opening yourself up to some attacks. That said, you will probably be okay as long as you're not running services. If you have anything that opens yourself to the internet -- an e-mail server, apache, ssh, ftp -- you don't want to keep it running.

Of course, Wireshark and Etherape both also need to run as root for full functionality, but this is somewhat safer, since they only monitor traffic, and cannot be used to change port access rules.

Completely agree. Running Firestarter all the time could be a security risk (hadn't thought of that). 
You're first post in this thread was a great explanation of Firestarter.
Might just have to copy/paste it the next time this subject comes up - and give you credit of course. :)

---

### Post by p_quarles on 2007-07-29
Feel free to quote it. I just fixed the typos. :)

---

### Post by TypeM on 2007-07-29
now i have learnt something new (iptables part of kernal)  :)

A stupid question WHY is firestarter installed on ubuntu (from repository) running as default? it doesn't sound smart if it's a security risk.

---

### Post by p_quarles on 2007-07-29
Not a stupid question at all. As I understand it, Firestarter has two different processes: 1) the configuration utility which needs to run as root, and 2) the daemon which runs as a separate user and simply enforces the rules you setup while using the configuration utility. 

If I'm wrong, though, someone please correct me. I think I read that somewhere, but I can't find the source, so don't take the above as a conclusive fact. I'm fairly certain that's how it works, though.

---

### Post by ICUR2Ys on 2007-07-29
I have a problem with what has been said here.  Maybe someone would clarify this for me.  Every time I boot up feisty and I run this.

dace@dace-desktop:~$ sudo iptables -L -n
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
dace@dace-desktop:~$ 

Which means iptables is not configured.  But if I start firestarter and then immediately turn it off and then run this.

dace@dace-desktop:~$ sudo iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  192.168.0.1          0.0.0.0/0           
ACCEPT     tcp  --  198.6.1.3            0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  198.6.1.3            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       0    --  0.0.0.0/0            255.255.255.255     
DROP       0    --  0.0.0.0/0            192.168.1.255       
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        0    -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.100        192.168.0.1         tcp dpt:53 
ACCEPT     udp  --  192.168.1.100        192.168.0.1         udp dpt:53 
ACCEPT     tcp  --  192.168.1.100        198.6.1.3           tcp dpt:53 
ACCEPT     udp  --  192.168.1.100        198.6.1.3           udp dpt:53 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     tcp  --  69.89.31.92          0.0.0.0/0           tcp dpt:2078 
ACCEPT     udp  --  69.89.31.92          0.0.0.0/0           udp dpt:2078 
ACCEPT     tcp  --  69.89.31.92          0.0.0.0/0           tcp dpt:2096 
ACCEPT     udp  --  69.89.31.92          0.0.0.0/0           udp dpt:2096 
LSI        0    --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     0    --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
dace@dace-desktop:~$ 

Now iptables is configured.  So why don't I want to run firestarter when I boot up and then turn it off as I do?

---

### Post by p_quarles on 2007-07-29
> Now iptables is configured.  So why don't I want to run firestarter when I boot up and then turn it off as I do?
The "unconfigured" IPtables file is actually very secure if you aren't running any services. By default, a new installation of Ubuntu is not listening for requests on any port, and therefore won't accept them. 

If you are running services, and you want that particular IPtables configuration to start with your system, you just need to save it and add it to the bootup procedure (i.e., you don't actually need to run Firestarter to do that). Here's a tutorial on IPtables:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
Scroll down to the sections labeled "Saving iptables" and "Configuration on startup."

---

### Post by ICUR2Ys on 2007-07-29
Thank you very much I will read the tutorial right now.

---

### Post by TypeM on 2007-07-31
Thanx for all your answers ! now i only have to learn how to make rules  for my firewall. Onething i learnt is that IF you open a port (80) it's open for all programs for use. you don't have the windows type of firewall that can stop different programs from accessing internet..

---

### Post by Hilko on 2007-09-18
Thanks, now i can start the GUI again.

removing the line:

username ALL=NOPASSWD:/usr/sbin/firestarter

in my sudoers file worked for me too. I wonder how it got there in the first place.

---

