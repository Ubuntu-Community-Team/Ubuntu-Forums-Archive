---
title: "Linux firewall and anti virus"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by ubdai on 2006-12-30
Can anyone tell me if I need to install a firewall and antivirus s/w.
If yes what do people recommend.

Previously used avg on w2k.

tia
ubdai

---

### Post by macogw on 2006-12-30
iptables is a firewall that's already there when you install Ubuntu.  You don't need an antivirus as Wine isn't good enough to run Windows viruses, and there are almost no Linux viruses.  The ones that exist would require you typing in your password and authorising them to run.  You can install clamav from the repositories if you want to keep from passing infected files that you get from one Windows user (which don't affect you) to another Windows user.

---

### Post by deadgobby on 2006-12-30
No not really needed. If you want you can do above post or install Firestarter firewall through Synaptic. It basicly controls the firewall in the system all ready. Adware or spyware is not really needed either. Some times it is good to delete cookies from time to time.
Gobby

---

### Post by macogw on 2006-12-30
I have my FF set to delete all privacy stuff except my passwords every time I close the browser.  Cookies and history are deleted automatically.

Firestarter is just a GUI for iptables.  If you don't intend to ever touch the firewall, no need for Firestarter.

---

### Post by OffHand on 2006-12-30
Use the search button. Nothing personal but I keep seeing these threads while a quick search would have given the answers.

[http://www.ubuntuforums.org/search.php?searchid=11971670](http://www.ubuntuforums.org/search.php?searchid=11971670)

---

### Post by deadgobby on 2006-12-30
Hi Off land,
 Your link is a dead end.
Gobby

---

### Post by angkor on 2006-12-30
> **deadgobby said:**
> Hi Off land,
 Your link is a dead end.
Gobby

:) I think offhand meant something like this:

[http://www.ubuntuforums.org/search.php?searchid=11976641](http://www.ubuntuforums.org/search.php?searchid=11976641)

---

### Post by OffHand on 2006-12-30
> **angkor said:**
> :) I think offhand meant something like this:

[http://www.ubuntuforums.org/search.php?searchid=11976641](http://www.ubuntuforums.org/search.php?searchid=11976641)

That's right  ;)

---

### Post by OffHand on 2006-12-30
> **deadgobby said:**
> Hi Off land,
 Your link is a dead end.
Gobby

You misspelled my name.

---

### Post by Frak on 2006-12-30
ClamAV and Firestarter (though both aren't needed)

Firestarter is just a GUI of IPTables, and was meant for people who are going to forward and close ports and what-not, mainly it was made for people who use a server, for websites and client computer interaction.

ClamAV was made to scan Windows client computers for viruses, over a network, when the computer with ClamAV is the server, (in this case Ubuntu), and as stated WINE isn't good enough to run Windows Viruses.

---

### Post by melancholeric on 2006-12-30
Someone should make a sticky about these somewhere. Just to save the new users from the trouble of making a new thread and others from answering again and again.

Plus, it's good marketing of linux for windows users who are tired of the malware issues.

Maybe it should be on the ubuntu.com frontpage, even. "Forget malware! No need for an antivirus! No need for a firewall!"

---

### Post by macogw on 2006-12-30
> **melancholeric said:**
> Someone should make a sticky about these somewhere. Just to save the new users from the trouble of making a new thread and others from answering again and again.

Plus, it's good marketing of linux for windows users who are tired of the malware issues.

Maybe it should be on the ubuntu.com frontpage, even. "Forget malware! No need for an antivirus! No need for a firewall!"

you still need a firewall to keep anyone from poking and putting in a rootkit.  The firewall just happens to already be there though.  Actually, Linksys routers are hardware firewalls on the basis that they run Linux and iptables is part of the kernel.

---

### Post by melancholeric on 2006-12-30
By default you don't need a firewall since there are no services running -> no open ports and no way to get access from outside.

Now, if you install say mysql or something and don't want anyone to access it from outside you're going to need it, but otherwise not.

---

### Post by deadgobby on 2006-12-30
> **OffHand said:**
> You misspelled my name.
Opps Off Land, Off Hand booth sound good to me. But me bad!
GObby

---

