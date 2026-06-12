---
title: "Fire wall disabled?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by alan-1 on 2007-12-09
Fire starter reports that my fire wall status is disabled.
Failing to start because device eth1 is not ready.
I had been trying to get a usb wireless device to work but failed (it worked perfectly well with Puppy  linux)
I connect to my router no problem on eth0 (wired)
All I want to do is erase all trace of eth1 and the wireless device and get back to a single wired connection that the fire wall accepts.
I am an Absolute Beginner and will need very simple instructions can any one help please.

---

### Post by ruibernardo on 2007-12-09
Hi alan-1,

run the wizard again (menu Firewall > Wizard in Firestarter) and choose the right active network interface in it. As an example to set up Firestarter with the wizard: [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

---

### Post by alan-1 on 2007-12-09
epimeteo

I have run the wizard many times it only shows one interface eth0 but if i try to run firestarter i get the message eth1not ready

---

### Post by ruibernardo on 2007-12-09
> **alan-1 said:**
> 
I connect to my router no problem on eth0 (wired)
All I want to do is erase all trace of eth1 and the wireless device and get back to a single wired connection that the fire wall accepts.

Hmm, maybe you have this option enabled.

[IMG]http://www.debianadmin.com/images/firestarter/4.png[/IMG]

Uncheck it so Firestarter doesn't try to share Internet. This way it will not try to use the other network interface.

---

### Post by alan-1 on 2007-12-09
no the sharing box is not checked

---

### Post by ruibernardo on 2007-12-09
In the start of the wizard you do select the connected device?

[IMG]http://www.debianadmin.com/images/firestarter/3.png[/IMG]

If you did, maybe you have to uncheck the not working network interface in "Network manager".

---

### Post by alan-1 on 2007-12-09
eth1 does not appear at any point during the wizard nor is it in network manager.

if i plug the device into a usb port then eth1 does appear in firestarter and network manager sees a wirless connection although i can't make it work and firestarter still reports eth1 not ready.
Which is my reason to get back to basic wired eth0 only

---

### Post by p252 on 2007-12-09
Firestarter won't work unless an interface is up and running. If you can't get eth1 to work (have a valid ip assigned to it and passing traffic) then firestarter will be disabled. You can get around this bad firestarter design, and have it bring up the firewall no matter what (even if no interfaces are active) by editing the script. See this post [http://ubuntuforums.org/showthread.php?t=508392](http://ubuntuforums.org/showthread.php?t=508392) There is a post by kukibird1 in there that tells you how to get around this problem. Sounds like the problem might be that you can't get the wireless usb device to work. . .

---

### Post by ruibernardo on 2007-12-09
Yes, that would solve the problem. 

I was supposing alan-1 was using Gutsy, because in Gutsy Firestarter should be connected to the interfaces that are on Network Manager only.


From the Firestarter [debian changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/f/firestarter/firestarter_1.0.3-6ubuntu1/changelog"):
> firestarter (1.0.3-2ubuntu2) gutsy; urgency=low

  * LP: #42759
    - debian/firestarter.NetworkManagerDispatcher: script to let NetworkManager
      start/stop the firewall when the interface goes up/down
    - debian/control: suggests network-manager
    - debian/rules:[B] installs firestarter.NetworkManagerDispatcher to
      /etc/NetworkManager/dispatcher.d/50firestarter[/B]

 -- Lionel Le Folgoc <mrpouit@ubuntu.com>  Sun, 20 May 2007 12:01:00 +0200


---

### Post by alan-1 on 2007-12-09
yes i am using Gutsy i followed the link to kukibird1's post the instruction is to comment out 4 lines of code i found the lines in question but how do i change them it looks like adding a # to the start of each line is whats required. How do you do that?  The # key doesn't work when viewing this file

---

### Post by ruibernardo on 2007-12-09
Vi is hard to work with. Try using nano instead, or try the following to use gedit:
```
gksudo gedit /etc/firestarter/firestarter.sh
```
if your using kubuntu (KDE) use:
```
kdesu kate /etc/firestarter/firestarter.sh
```

---

### Post by alan-1 on 2007-12-09
Success.
Thank you very much epimeteo, p252, I'm much happier now it worked. Fire wall now enabled, I had to run the wizard to get back on line, it still reports eth1 not ready, but now, that fact doesn't disable it.

---

