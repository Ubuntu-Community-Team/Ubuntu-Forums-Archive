---
title: "update manager bug... any other way to update?"
date: 2007-07-12
forum: Apple PPC Users
---

### Post by neatokino on 2007-07-12
I've been away from my dual-boot first generation 12" powerbook for about a month.  When I try to update using update manager, I get the following message:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 48 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


OK, first of all, I don't know where or how to report the bug.  Can anyone help me with that?

Secondly, is there any other way to update my system?

Oh, and has anyone ever figured out a way to make this thing sleep?


TIA
Michael

---

### Post by reh4c on 2007-07-12
Greetings,
You can create a launchpad account and submit the bug report here:  [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
Please search through the current bugs to ensure someone hasn't alreadyreported it.  I'm using an iBook, so I can't really help you with the update issues.  My system is running well.  Good luck.

---

### Post by needtolookatascreenshot on 2007-07-12
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by stmiller on 2007-07-12
Nvidia-based macs are not able to sleep/suspend due to insufficient hardware info from nvidia. ATI machines only. There's hope with the Nouveau project in the future for nvidia folks.

---

### Post by neatokino on 2007-07-12
Thanks for the comments so far.  I did post on launchpad and am waiting for a response.

I'd like to get help here, but I'm such a newbie to Linux that I don't know how to post the contents of my /etc/apt/sources.list.   If someone could tell me exactly how I do that, I'll post it here!  

I'd love to get everything up to date on this computer, so any help would be greatly appreciated.

Thansks again

Michael

---

### Post by stmiller on 2007-07-12
Go to Applications>Add/Remove>Preferences 

and then go to third party software and uncheck any third party repos (for the time being).

Then see if that fixes things.

---

### Post by neatokino on 2007-07-12
Hello again--

When I go to Add/Remove, I can't access preferences because I get the following message:

'Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.'


Obviously, something is really in need of repair!   Any hints?  If I try running 'sudo apt-get update' from the terminal window, I get the following message:

E: Type '“deb' is not known on line 48 in source list /etc/apt/sources.list

---

### Post by linear on 2007-07-12
> **neatokino said:**
> I'd like to get help here, but I'm such a newbie to Linux that I don't know how to post the contents of my /etc/apt/sources.list.   If someone could tell me exactly how I do that, I'll post it here!

Go to Applications > Accessories > Text Editor

Then: File > Open...

Navigate to /etc/apt and open sources.list

Copy contents and paste into a message here.

---

### Post by neatokino on 2007-07-12
Thanks everyone for your help... I got rid of some 'automatix' stuff and everything is working fine now!

M

---

### Post by stmiller on 2007-07-12
Yeah automatix does not really work with PowerPC Ubuntu. Not sure if it is really supposed to work at all with PPC.

---

