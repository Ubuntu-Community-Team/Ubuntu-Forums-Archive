---
title: "Security Question!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Noobuntu61 on 2007-08-23
Hey guys i am a new linux user and i would like to know whether or not i need to install fire wall or internet security programs for protection. if so i would like to know the best software. I just dont want a virus.

---

### Post by splintercellguy on 2007-08-23
None. Ubuntu already has a firewall, namely iptables, and Firestarter can be installed from repos to manage it. There are some AVs in the repos, but they are there to prevent the spread of Windows viruses.

---

### Post by aysiu on 2007-08-23
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by likemindead on 2007-08-23
Search first! There are tons of threads that address this.... :)

---

### Post by misfitpierce on 2007-08-23
Yuo tons of threads but quickly firestarter - sudo apt-get install firestarter in terminal for firestarter is only tool you may need to manage built in firewall. No AV or Antispyware or any antimalware is needed unless trying not to pass a windows virus to windows pc on network which is doubtful anyways.

---

### Post by bodhi.zazen on 2007-08-23
aysiu's link is helpful.

This is also helpful : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

To answer the question, 

Discussions of firewalls are heated. A default ubuntu desktop install has no open ports, so a firewall is not needed.

The Linux (ubuntu) firewall = IP tables. The default configuration is permissive.

You may install a firewall, firestarter is nice. This will allow you to configure IP tables via a gui.

The problem is that if you install server software it will open ports. Sometimes this is not obvious, thus firestarter can help.

viruses/spyware is currently a non-issue.

---

