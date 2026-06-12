---
title: "did i get hacked? here are the details i'm supposed to put"
date: 2012-09-21
forum: Any Other OS
---

### Post by DeezyFaReal on 2012-09-21
1: What version of Ubuntu are you running? Are you dual booting, and is this system networked with other machines, if so what operating platform and versions are they running?
Linux Mint 13, Dual boot with Windows Vista SP 2
I use a Windows 7 SP1 Box with the same modem-- I don't know if that's considered a network

2 : Why do you think you were cracked? Please post a paste from the log file or a screenshot, or written description of what you are experiencing.
I keep noticing my Gmail accounts are being accessed from IP numbers in other US States. I checked under "recent account activity" on my inbox
Examples include : auth.log snippets, syslog snippets, av alerts, rkhunter/chkrootkit reports, odd browser behavior, IDS logs, etc.

3: If this machine is networked with other machines is the same behavior observed there?
Again I use the same modem for my Windows 7 box, but I don't know if you would consider that a network. (one modem, one ethernet cable, only one PC is connected to the web at a time)

4: Is this machine shared between multiple users, or is it for your use only. Also, is it using strong credentials for all forms of authentication?
I have 4 accounts on this computer -- 2 for Linux Mint and 2 for Windows Vista

5: What services are the machine in question running? Also are any other network services running on other machines on the network? If so what are they?
I don't know what services are running. I typed ssh, vnc, mysql, and apache in terminal, and only ssh returned something. The others said command not found are you sure you have " " installed.

6: Did you recently download or install anything from an untrusted source? (IE: PPA, or from the internet, including bash scripts)
I don't know if I got anything from an untrusted source. I only download apps from Official websites. I got Virtualbox from oracle.com

7: Is the compromised machine or network in question on a wireless network? If so what type of security measures are in place? WEP/WPA/WPA2/Open ?
The machine is a laptop, but I don't ever use wireless internet
8: What other security measures are you utilizing on your sytem? Apparmor? UFW? Firestarter? etc...
I'm using UFW uncomplicated firewall and clamtk virus scanner. I think I have apparmor

9: Have you added, modified, damaged or replaced any hardware in the system recently?
No.
10: Is the noticed activity repeatable?
The moment I notice one of my gmail accounts was accessed from a remote IP I delete the account, so I can't really answer this question. It has happened to two accounts recently, and one in the past.

---

### Post by houseworkshy on 2012-09-22
First with the gmail accounts and unknown logins go to the gmail  settings with the browser.  Log out of all of them.  If new ones appear  which are not to do with you change your password, if new ones continue  to appear contact google.  It's webmail so may not have much to do with  your machine.
You are using wireless, make sure that you have password secured the router.  
There  is a serious security flaw with the facebook/windows/wireless combo.   If you are using facebook take a look at this embarraceingly old video  about the still unfixed problem  [http://archive.org/details/FiresheepVs.Facebook](http://archive.org/details/FiresheepVs.Facebook).

Check your  firewall.  Open a terminal and enter "sudo ufw status", you'll need the  sudo because it's a root action.  If it's not running then set up the  safe defaults with "ufw default deny" then set it to run at start up  with "ufw enable".  The default settings for "sudo" give root powers for  15 minuets which is why I didn't preface the latter two commands with  it.  If you have taken longer than a quarter of an hour to enter them  after the first use of sudo you will need to prefex them with it.  It's a  good idea to kill that timer when you've finished with root power  actions, especially if online,  so use "sudo -k" to end the timer  early.  As with all commands in linux the manual page is very helpful,  to access it use the man command; just type "man" in front of any  command you want to know about, in this case "man ufw".  Check the  firewall in windows too. 
Well thats the stable door anyway.  I don't  do much networking, bar being connected to the internet, so hopefully  someone with more experiance will chime in later.
Meanwhile you could  browse around the manual pages.  You could try "apropos network" to  pull a list of command related to networking and then "man" them to see  if they are usefull.  "netstat" may be worth a look too.
rkhunter  looks mostly for rootkits.  If you don't have it, it is installable.   Once in "man rkhunter" will give details on it's use.  Tyger is another  one that can be useful.  Both of those are command line things.   Probably the most useful tool for seeing what is going on is "wireshark"  and that has a graphic user interphase.  Expect a bit of a learning  curve with all of them.
I hope some of that may be useful and also hope a real security expert replies to this soon.
It's a bump if nothing more.  Good luck.

EDIT Extra bit after looking again.

A PPA refers to the software collections, called repositories, which one can access through the software managers on a distribution.  In general it is better not to go via webpages.  There is a form of installing called apt;urls which can be embeded in web pages and they can install repositores.  So look at your software sources and see if one has been added to the defaults.  I avoid apt;urls unless I'm sure of the source.  In general it is better to use the software managers in the gui or "apt-get" and "aptitude" though the command line in the terminal, 'man' them for details.  Repository adding is something I prefer to do only deliberately.

---

### Post by DeezyFaReal on 2012-11-04
Thanks for the help.
Update: I got rid of Mint a long time ago.

---

### Post by northrup on 2012-11-05
I know this is already marked as solved, but if you continue to experience issues with unauthorized Gmail logins, you could try activating two-step verification, which adds a second step - a six-digit time-sensitive PIN - to login attempts on unverified machines.  I use this for my own Google account after seeing that there were logins from Russia and Ukraine; after setting two-step verification, I've yet to have further issues.

---

### Post by DeezyFaReal on 2012-11-16
Thank you, for reminding me.
That is a good idea. 2-step verification would work for me. 
++A recovery email, in case anything happens to my phone. <--- I know how hard it can be to recover a google account with no alternate email and a phone number that is no longer active.

**2-step verification works for me!**

---

