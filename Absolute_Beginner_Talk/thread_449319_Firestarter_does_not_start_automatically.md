---
title: "Firestarter does not start automatically"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Tallman on 2007-05-20
Using Ubuntu Fiesty, I tried to load firestarter at login.

System -> Preferences -> Sessions
see attachment Screenshot.png

After login, firestarter does not seem to be running. There is no icon in the panel and no process is running.

```
marpau@marpau-desktop:~$ ps -ef |grep firestarter
marpau   10330 10308  0 11:25 pts/0    00:00:00 grep firestarter
marpau@marpau-desktop:~$
```

What am I doing wrong here?

---

### Post by The Seeker on 2007-05-20
Maybe take a look at the instructions [here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall).

---

### Post by Tallman on 2007-05-20
> **The Seeker said:**
> Maybe take a look at the instructions [here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall).

The Seeker, thanks for your quick reply.

This is what I did with the Ubuntu Guide as a reference:

>  **How to make Firestarter start automatically at startup**

    * System -> Preferences -> Sessions -> Startup Programs -> New:
    * Name (field): 

```
Firestarter
```

    * Command (field): 

```
sudo firestarter --start-hidden
```

    * Press "OK" 

This resulted in the screenshot I posted in my first message and in firestarter not running automatically.

---

### Post by Ozeuss on 2007-05-20
do you have problems loading firestarter manually?
i don't load it at startup, since it's only a gui for iptables, so unless i want to check something or change firewall settings i don't load it.

---

### Post by infoseeker on 2007-05-20
As far as I remember the firewall is started automatically after Firestarter is installed.  The Firestarter GUI is the part that doesn't start on reboot.
Correct me if I am wrong.
OOPS :D too late :) Someone got there first LOL

---

### Post by Tallman on 2007-05-20
> **Ozeuss said:**
> do you have problems loading firestarter manually?

I copied and pasted the command from my Sessions screen:

```
marpau@marpau-desktop:~$ sudo /usr/sbin/firestarter --start-hidden
Password:
Firewall started
```

The firestarter icon appears in my panel as well.

> **Ozeuss said:**
> i don't load it at startup, since it's only a gui for iptables, so unless i want to check something or change firewall settings i don't load it.

```
marpau@marpau-desktop:~$ ps -ef | grep iptables
marpau   11975 11747  0 12:09 pts/0    00:00:00 grep iptables
marpau@marpau-desktop:~$
```

iptables doesn't seem to be running as well. Or shouldn't that be a running process?

---

### Post by Ozeuss on 2007-05-20
iptables comes ready with the installation, and your firewall is running (ports in ubuntu are also configured as closed). so, if your concern is only to have a software firewall- you do have one. firestarter is a GUI front end to iptables, so even when your not running it, you still have a firewall. but its a good program to open ports or monitor your computer.
having said that, you can try to put in sessions
```
gksu /usr/sbin/firestarter
```
or maybe, similar to your try
```
gksu /usr/sbin/firestarter --start-hidden
```
that code is in the menu entry for firestarter, maybe it'll do better. it should pop up a gui sudo-password box.

---

### Post by Tallman on 2007-05-21
Okay, I still don't know  why it didn't work initially, but after a bit of trial-and-error on the command line, I finally found the command that does what I want.

```
sudo firestarter --start-hidden &
```

Apparently, the ampersand is crucial :confused:

Thanks for your help.

---

### Post by jefferystone on 2007-06-25
Guys,

The way that I see it,  firestarter serves two purposes:

1.  It modifies iptables after being launched
2.  It displays information and collects logs including attempts to access certain ports.

I have come up with a solution for getting firestarter to run at startup:

I tried getting firestarter to automatically startup after logging in by adding it through System-> Preferences-> Sessions-> Startup Programs using --start-hidden (with or without the &) and rebooting.  I also tried editing the /etc/sudoers files like others suggested to eliminate a password window.  Nothing I tried allowed firestarter to run at startup.  However, after logging in, I could run firestarter from a terminal or menu and it worked just fine (verified by displaying the rules in iptables).

Typing ***sudo iptables --list*** after a reboot revealed that there were no rules in iptables:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```


**Here is the solution that worked for me:**

I added ***sudo /usr/sbin/firestarter -s &*** to /etc/rc.local

My /etc/rc.local file looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo /usr/sbin/firestarter -s &
exit 0
```

If I hit <CTRL><ALT><F8>, the last line displayed is: **Firewall started**

Typing ***sudo iptables --list*** after a reboot now reveals:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
.......
```

You can always start the GUI firestarter after you have logged in to start collecting information, but at least the rules are in iptables.

By the way, I am using Firestarter 1.0.3 with Ubuntu 7.04 feisty.

Sincerely,

Jeffery S. Stone

---

### Post by swoll1980 on 2007-06-25
Firestarter is not a firewall. It is mearly a graphical tool used to configure the firewall that is on your ubuntu by default witch is callled IP Tables. IP Tables is always on from the moument you first install your ubuntu. IP tables is very secure by default and should only be reconfiguerd out of nesesity. if your computer is connecting to the internet then there is nothing to configure,and IP Tables should be left to it's own discretion

---

### Post by jefferystone on 2007-06-25
> **swoll1980 said:**
> IP tables is very secure by default and should only be reconfiguerd out of nesesity.

This is simply not true.  By default, there are no rules defined in iptables - all traffic is allowed.

Sincerely,

Jeffery Stone

---

### Post by Seisen on 2007-06-25
Also by default all ports are closed when you install Ubuntu and the ports only open when you use them such as 80, 443 etc...

---

### Post by swoll1980 on 2007-06-26
> **jefferystone said:**
> This is simply not true.  By default, there are no rules defined in iptables - all traffic is allowed.

Sincerely,

Jeffery Stone

All ports are closed by default. They do not allow traffic I know this for a fact because I installed my lan, and I could not ping or communicate with my Ubuntu PC in any way until I installed fire starter and allowed the IP address

---

### Post by Absorbed on 2007-07-05
I've just rebooted my computer about twenty times trying to figure this out.

It seems to me that once firestarter is installed it's policies are constantly in effect regardless, according to "sudo iptables --list". It keep any policy changes made after a reboot, with no need to add firestarter to System->Preferences->Sessions or /etc/rc.local. Firestarter's documentation says as much here: [http://www.fs-security.com/docs/persistence.php](http://www.fs-security.com/docs/persistence.php)

The only way I could open the GUI at startup was "gksu "firestarter --start-hidden"", which isn't perfect because it prompts you for a password. Adding the above gksu command -- or any other command, it seems -- to /etc/rc.local doesn't open the GUI. Adding "sudo firestarter --start-hidden &" to Sessions doesn't open the GUI for me. I'd like to start up the GUI without having to enter my password every time I boot up, if anyone knows a way.

---

### Post by CiriusX on 2007-07-18
Hi Absorbed,
You can autostart Firestarter without having to enter a password (but it does involve a security compromise) using the following :

How to make Firestarter start automatically at startup
* System -> Preferences -> Sessions -> Startup Programs -> Add

sudo firestarter --start-hidden

* Press "OK"

How to have Firestarter start without the root password

Note: THIS IS NOT SECURE !!

In Terminal:
export EDITOR=gedit
sudo visudo

• navigate to the # Defaults section
• and place a # in front of this line 'Defaults !lecture,tty_tickets,!fqdn'
• so it looks like this:

#Defaults !lecture,tty_tickets,!fqdn

• then add this line immediately after it:

Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

• At the very bottom of the file add this line:

  USERNAME ALL= NOPASSWD: /usr/sbin/firestarter

• Save and close the file

• This may cause problems with administrative applets that won't open due to the changes made to the visudo file
  including Synaptic and the Updater, which even after entering your password may no longer open. To fix this:

• For the next two lines, USERNAME = your username

~$ sudo ln -fs /home/USERNAME/.Xauthority /root/.Xauthority
~$ sudo chown USERNAME.root /home/USERNAME/.Xauthority

• Restart your computer
 
This should do the trick - tested it in Edgy & Feisty although I've now changed to Guarddog - IMHO a better ui and more intuitive to operate. Good luck.
CiriusX

---

### Post by shimoda on 2007-08-13
I'm in the same situation than **jefferystone**
After boot, if I type:
sudo iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

and
sudo /etc/init.d/firestarter status
```
 * Firestarter is stopped
```


But if after that I load firestarter 
sudo /etc/init.d/firestarter start

appear a lot of policies in iptables...



But, my question is... In a normal desktop use (and using a router with integrated firewall), it's really necessary to change iptables settings?

I say this, because after some testings in "Shields Up"
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

the results are the same with or without Firestarter...

thanks!!

---

### Post by Mawy on 2007-08-27
Heyas,

After trying a few of the suggestions here I found the right thing to put in (System> Preferences> Sessions> Startup Programs > New

```
gksu "firestarter --start-hidden" &
```

A password window pops up after you log in, which is fine with me.

I know Firestarter is just a GUI for iptables, but I like having it running when I log in. I like seeing the events as they happen, and it also seems like a simple way to keep tabs on your network usage per session.

Cheers! :)
Mawy

---

### Post by crjackson on 2007-08-27
> **swoll1980 said:**
> Firestarter is not a firewall. It is mearly a graphical tool used to configure the firewall that is on your ubuntu by default witch is callled IP Tables. IP Tables is always on from the moument you first install your ubuntu. IP tables is very secure by default and should only be reconfiguerd out of nesesity.** if your computer is connecting to the internet then there is nothing to configure,and IP Tables should be left to it's own discretion**

True for the most part, but I too use Firestarter for easy port opening and closing to facilitate my FTP server.

---

### Post by Malibu Illusion on 2007-08-27
"iptables" isn't "secure by default" any more than a Windows box is "secure by default."  The reason ports are closed is the simple fact that no daemons are listening on them.  Your firewall doesn't have to flag the ports as "closed"; they're "closed" as there's nothing there opening them.  You don't need a firewall at all to achieve this.

As for the Firestarter GUI app; don't run it at startup.  That simple, really.  It's just another program that you're executing as a root user and that, in itself, is ironically creating a potential security issue all alone.  You must get out of the Windows mentality and not require a visual firewall cue constantly on your desktop.  It should be used as a graphical frontend to configure iptables if need be and closed after configuration is complete.

Take care.

---

### Post by por100pre1 on 2007-08-27
> **Mawy said:**
> Heyas,

After trying a few of the suggestions here I found the right thing to put in (System> Preferences> Sessions> Startup Programs > New

```
gksu "firestarter --start-hidden" &
```

A password window pops up after you log in, which is fine with me.

I know Firestarter is just a GUI for iptables, but I like having it running when I log in. I like seeing the events as they happen, and it also seems like a simple way to keep tabs on your network usage per session.

Cheers! :)
Mawy

I used to think the same, but I learned that keeping gksu running means any other commands with gksu won't need to ask for password. That's actually a security breach right there! :!:

---

### Post by Mawy on 2007-08-27
Ah! Thanks for the info on gksu! Guess I won't be using that anymore unless I really need to.

---

### Post by por100pre1 on 2007-08-27
> **Mawy said:**
> Ah! Thanks for the info on gksu! Guess I won't be using that anymore unless I really need to.

You're welcome! If you only use it for configuring ports and close it afterwards you'll be just fine. :)

---

### Post by citizenphil on 2007-09-02
It seems to be common knowledge that Firestarter is just a GUI for iptables and, once configured, will do its thing without any user intervention.  The only thing is, this common knowledge seems to be wrong.

I just installed and configured Firestarter on a fresh Ubuntu 7.04 installation and have been using Shields Up to test it.  If I reboot and run Shields Up, almost all ports show as closed.  It's not until manually starting Firestarter that I'm able to get a full "stealth" rating.  After starting the GUI, I can shut it down and it still works, but I do have to initialize it manually.

Given that even the official Firestarter documentation says the iptables settings should persist after a reboot, I'm lost.  Does anyone have any idea why this is happening?  Or how to fix it?

Here's the link to Shields Up:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by jefferystone on 2007-09-04
citizenphil,

I can corfirm that the iptables settings are not persistent after a reboot.  Just type iptables -L after a reboot and after starting/exiting firestarter and you'll see a big difference. 

That's why I put "sudo /usr/sbin/firestarter -s &" in /etc/rc.local and it doesn't require a password to be entered.

Sincerely,

Jeffery Stone

---

### Post by -SpaZ on 2007-09-04
iptables always runs, Firestarter is just a gui for iptables.

---

### Post by nvteighen on 2007-09-05
> **citizenphil said:**
> It seems to be common knowledge that Firestarter is just a GUI for iptables and, once configured, will do its thing without any user intervention.  The only thing is, this common knowledge seems to be wrong.

I just installed and configured Firestarter on a fresh Ubuntu 7.04 installation and have been using Shields Up to test it.  If I reboot and run Shields Up, almost all ports show as closed.  It's not until manually starting Firestarter that I'm able to get a full "stealth" rating.  After starting the GUI, I can shut it down and it still works, but I do have to initialize it manually.

Given that even the official Firestarter documentation says the iptables settings should persist after a reboot, I'm lost.  Does anyone have any idea why this is happening?  Or how to fix it?

Here's the link to Shields Up:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Go [here]("http://ubuntuforums.org/showthread.php?t=542756").

---

### Post by jefferystone on 2007-09-05
nvteighen,

Thank you for the information.  Thankfully someone confirms what I've been saying.

I had an alternate solution - this would run firestarter after the networking was started.

> 
Here is the solution that worked for me:

I added sudo /usr/sbin/firestarter -s & to /etc/rc.local

---

### Post by citizenphil on 2007-09-15
Thanks, nvteighen, that fixed it for me.

I'm not sure exactly how this works, but if this fix just makes Firestarter work like it's supposed to, shouldn't it be a default setting when you install the package?  Is this the type of thing that should be officially submitted so the package can be changed?

---

### Post by Blind Tiger on 2007-09-22
Based upon my testing, my reading of these forum posts, and Firestarter documentation, I have come to the following conclusions:
(1) after installing and using Firestarter to configure iptables, it causes an error on system startup because of a scripted test loop that gives a faulty result because it is set to run before the network is up.
(2) this faulty test result then in turn causes iptables to not function.
(3) this leaves the user with the end result of having to start Firestarter to reactivate iptables with the given set of rules/policies.
(4) so now, understandably, it is a reasonable desire to have Firestarter start automatically at system startup.  this is a security issue as pointed out by several folks -- because you either modify the GUI's need for sudo password, or you run it all the time after entering your admin password.
(5) i believe i read one posting that modified the script to work around the timing issue with network startup, but I am not sure if this is the best solution to this dilemma!

Anyone have an authoritative final say???!!!

---

### Post by Blind Tiger on 2007-09-26
I'm not sure if it has to do with some recent updates (some involving the kernel), but now the session startup command for Firestarter "sudo firestarter --start" seems to launch firestarter and implement the correct policies into iptables.  "sudo iptables --list" shows a functioning firewall at startup!

--update-- 
The automatic start-up is not consistent, therefore I still have to check to determine if iptables if functioning properly.

---

### Post by Blind Tiger on 2007-10-27
Upgrade to Gutsy solved this error involving Firestarter and the Network start up.  No problems now whatsoever.

---

### Post by jefferystone on 2007-11-16
Same result - upgrade to Ubuntu 7.10 resolved issue.  Was able to remove entry in /etc/rc.local

Sincerely,

Jeffery S. Stone

---

