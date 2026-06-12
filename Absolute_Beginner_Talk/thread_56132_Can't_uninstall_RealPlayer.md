---
title: "Can't uninstall RealPlayer"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by alquimista on 2005-08-11
Hi,
I'm working under Kubuntu; I downloaded RealPlayer installer that is a ".sh" file and installed it ok; it worked well. Now that my Linux partition is packed, I want to uninstall it. But if I go to Kynaptyc/Synaptic I don't see it as installed, nor "apt-get remove realplayer" seems to work. How can I remove it? 

Thanx,
Guillermo

---

### Post by costoa on 2005-08-11
[QUOTE=alquimista]Hi,
I'm working under Kubuntu; I downloaded RealPlayer installer that is a ".sh" file and installed it ok; it worked well. Now that my Linux partition is packed, I want to uninstall it. But if I go to Kynaptyc/Synaptic I don't see it as installed, nor "apt-get remove realplayer" seems to work. How can I remove it? 

Thanx,
Guillermo[/QUOTE]
 Since RealPlayer was installed via it's own shell script and not a "dummy" package you'll need to manually remove it. "locate RealPlayer" on my machine shows everything is in /usr/local/RealPlayer so "sudo rm -fr /usr/local/RealPlayer" would remove it. Should be the same for yours but "locate RealPlayer" will confirm it.

**Please**, "rm -fr" is one of the most dangerous commands in GNU/Linux so use it with great care. Misuse can cause you to blow out your entire drive.

---

### Post by KingBahamut on 2005-08-11
Blowout is an understatement costoa. 

=)

---

### Post by alquimista on 2005-08-11
Thank you !
Guillermo

---

