---
title: "Im so lost"
date: 2012-01-30
forum: Any Other OS
---

### Post by Hypnopirate on 2012-01-30
Im trying to use my vpn on backtrack 5 the directions are > 


**Command-line based start:**             

[LIST]
[*]1. Install openvpn package by using apt-get install openvpn
[*]2. Extract anonine_openvpn.zip ([download here]("https://www.anonine.com/files/anonine_openvpn.zip")) into /home/<USERNAME>/openvpn              directory
[*]3. Start connection with:
               sudo openvpn --client --config $HOME/openvpn/anonine.ovpn --ca $HOME/openvpn/anonine.ca.crt
[*]4. Enter username
[*]5. Enter password
[/LIST]

step one* is done openvpn was already installed 

step two* Ive downloaded the Zip but i can not figure out where to stick it ...

can anyone help with step by step direction PLEASE! ive been going at it for 2 hours already and im about to throw my computer out the window 

I thought I had it right but i keep getting this message > Options error: In [CMD-LINE]:1: Error opening configuration file: /root/openvpn/anonine.ovpn
Use --help for more information.


thanks in advance

---

### Post by overdrank on 2012-01-30
Moved to Other OS/Distro Talk

---

### Post by Double.J on 2012-01-31
Hi there!
Never used the software, but looking at the installation guide, step 2 doesn't need to be done in the command line. you could just navigate to /home/user/Downloads in the file browser, then double clicking on the zip file should open up an archive manager - then you can choose where to extract it to - your guide says /home/user/openvm

Is this what you meant?

All the best!

---

