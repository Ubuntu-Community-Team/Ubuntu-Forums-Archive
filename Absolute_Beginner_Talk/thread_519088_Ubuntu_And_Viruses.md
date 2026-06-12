---
title: "Ubuntu And Viruses?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by jp316ad on 2007-08-06
I'M A COMPLETELY NEW USER TO UBUNTU / LINUX. WHAT PROGRAMS IF ANY DO I NEED TO INSTALL TO PROTECT MY COMPUTER. I HAVE SEEN THAT IT IS DIFFICULT FOR UBUNTU TO GET A VIRUS BUT NOT IMPOSSIBLE. I SAW THAT AVAST HAS AN ANTIVIRUS FOR LINUX; IS IT ANY GOOD? OR SHOULD I LOOK FOR ANOTHER ONE? 

LASTLY WHAT FIREWALL IS GOOD FOR UBUNTU? ANY OTHER TIPS FOR ME TO KNOW? :confused:

---

### Post by Gmbrdilos on 2007-08-06
viruses are for windows, you dont need anything ;)
for firewall you might wanna try firestarter.

---

### Post by eentonig on 2007-08-06
virusscanners for linux are basically only usefull to protect windows users you come in contact with via email or such. The chance to get infected on linux is practically nil.

Default firewall in linux is ip-tables and is installed on every linux distribution. But it's a bit hard to configure as such. Therefore, some good GUI's exist.

For basic usage, I recommend firestarter. If you want more advanced stuff, I use fwbuilder.


PS. Al caps are very annoying to read.

---

### Post by nichipet on 2007-08-06
You don't need to worry about viruses on Ubuntu. But if you share files with Windows or even Mac users and you feel like being kind to them, you could install ClamAV ([http://www.clamav.net](http://www.clamav.net)).

---

### Post by starcraft.man on 2007-08-06
> **jp316ad said:**
> I'M A COMPLETELY NEW USER TO UBUNTU / LINUX. WHAT PROGRAMS IF ANY DO I NEED TO INSTALL TO PROTECT MY COMPUTER. I HAVE SEEN THAT IT IS DIFFICULT FOR UBUNTU TO GET A VIRUS BUT NOT IMPOSSIBLE. I SAW THAT AVAST HAS AN ANTIVIRUS FOR LINUX; IS IT ANY GOOD? OR SHOULD I LOOK FOR ANOTHER ONE? 

LASTLY WHAT FIREWALL IS GOOD FOR UBUNTU? ANY OTHER TIPS FOR ME TO KNOW? :confused:

1) Don't use caps, we can read standard text. It is annoying and can be construed as rude.

2) Please read [this.]("http://www.psychocats.net/ubuntu/security") And [this.]("http://ubuntuforums.org/showthread.php?t=510812")

3) If you still want an AV, look for the KlamAV (the GUI for ClamAV) and ClamAV packages in the repositories (for information on installing see my blue link in my sig).

That should do it, IMO there is no rush to get an AV. Today, you probably have better odds of getting hit with lightning in broad day light. That's it, have a nice day.

---

### Post by Jimmyfj on 2007-08-06
Regarding viruses on Ubuntu, and GNU/Linux I'd say that as long as you are aware of what you are dbl. clicking on you'd be safe. Linux is practically immune to viruses but just to calm your mind you can install ClamAV on your box so you wont forward any viruses to a Windows user. I never install any anti virus software on my Ubuntu box. My router saves me a lot of configuration for a firewall too. Linux is about as safe as it comes.

---

### Post by HermanAB on 2007-08-06
What is a virus?

Seriously, you need not worry about it.  Relax and enjoy your Ubuntu - computing the way the computer god intended it to be, free of interference by gremlins, goblins and crapware.

---

### Post by Rocket2DMn on 2007-08-06
There are only a handful of viruses ever made for linux, and there aren't currently any in the wild (an active threat).  I haven't used firestarter, but I hear it's a rather nice GUI frontend for iptables.
The only reason to get a virus scanner for linux is to prevent forwarding of infected files to windows users.  In most of our opinions you shouldn't sweat this as it should be the windows users' job to protect their own computers - don't waste your own computer resources to protect them.

---

### Post by por100pre1 on 2007-08-06
> **jp316ad said:**
> I'M A COMPLETELY NEW USER TO UBUNTU / LINUX. WHAT PROGRAMS IF ANY DO I NEED TO INSTALL TO PROTECT MY COMPUTER. I HAVE SEEN THAT IT IS DIFFICULT FOR UBUNTU TO GET A VIRUS BUT NOT IMPOSSIBLE. I SAW THAT AVAST HAS AN ANTIVIRUS FOR LINUX; IS IT ANY GOOD? OR SHOULD I LOOK FOR ANOTHER ONE? 

LASTLY WHAT FIREWALL IS GOOD FOR UBUNTU? ANY OTHER TIPS FOR ME TO KNOW? :confused:

avast! will do a decent job checking for viruses so you won't share viruses with Windows users. It is an on-demand scanner which is more than what you actually need (nothing).
If you wanna have some scanning fun, let's scan for **rootkits** with **chkrootkit** and **rkhunter** in a terminal:

Install them:
```
sudo aptitude install chkrootkit rkhunter
```

to use them:
```
sudo chkrootkit
```
```
sudo rkhunter --update && sudo rkhunter -c -sk
```

Hope this helps. :)

---

### Post by jp316ad on 2007-08-06
Sorry guys for putting in my question in all caps but I was working on something that requires all caps. Just forgot to switch it. :)

---

### Post by xpod on 2007-08-06
I think i installed clamav on my very first Ubuntu install.......after all,even my short time with Windows left that *need* to be just scanning *something*:)

I never bothered with the av on the re-install a week or so later though and it`s never been used or even installed since......not on any Linux install.

I`ve even been slated on certain other places for such ignorance & assumption:)

EDIT:[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

Of course,not entirely impossible it seems...lol

---

### Post by old_geekster on 2007-08-06
> **eentonig said:**
> 
PS. Al caps are very annoying to read.
All caps mean that you are yelling on forums.  This is not a forum that requires even raising your voice.:):)

---

### Post by bodhi.zazen on 2007-08-06
> **jp316ad said:**
> I'M A COMPLETELY NEW USER TO UBUNTU / LINUX. WHAT PROGRAMS IF ANY DO I NEED TO INSTALL TO PROTECT MY COMPUTER. I HAVE SEEN THAT IT IS DIFFICULT FOR UBUNTU TO GET A VIRUS BUT NOT IMPOSSIBLE. I SAW THAT AVAST HAS AN ANTIVIRUS FOR LINUX; IS IT ANY GOOD? OR SHOULD I LOOK FOR ANOTHER ONE? 

LASTLY WHAT FIREWALL IS GOOD FOR UBUNTU? ANY OTHER TIPS FOR ME TO KNOW? :confused:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by aysiu on 2007-08-06
As someone said in another thread, anti-virus definitions are necessarily **re**active, not **pro**active.

So installing anti-virus *before* a desktop-threatening Linux virus comes into the wild is pretty much worthless. Once we're aware the virus threat exists, it'd take less time to install the anti-virus than it would the anti-virus maintainers to update definitions.

---

### Post by por100pre1 on 2007-08-06
Many widespread malware like Code Red, Nimda and Blaster were the result of known Windows vulnerabilities that the guys at Microsoft didn't care to fix until it was too late...

Linux has the advantage of being open source so any vulnerability is quickly discovered and patched. That with the architecture of Linux, permissions, etc. makes Linux hard to break by malware.

---

### Post by kinematic on 2007-08-06
If you're gonna install a rootkit detector put it on a floppy,that way you prevent it being tampered with.

---

### Post by Gremlinzzz on 2007-08-06
sudo aptitude install chkrootkit
to use sudo chkrootkit
dont for get to check for madcow
sudo apt-get moo
:guitar:

---

