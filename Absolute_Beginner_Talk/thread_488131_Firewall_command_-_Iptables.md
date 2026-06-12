---
title: "Firewall command - Iptables"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by e6626550w on 2007-06-29
A poster recently listed how to open and close ports via the terminal. Below is the command he mentioned as to how to close a specific port. 

sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

I opened numerous ports with the port opening command but I've neglected to make a list of which ones they were. 

So, would someone be helpful and type out the command for me that will close all the ports and put Ubuntu back into it's default condition. What goes in place of the 6881? Also is there a terminal command that will tell you what ports are open? 

And to Rocket2DMN & Shinobi326 who were kind enough  to offer advice on my problem with uploading from a browser disappeared when I rebooted the router to default. Thank the lord it was that and not line problems because  we have only one dsl provider in my area and they get around to things when they want to. Thanks again.

eileen...

---

### Post by bodhi.zazen on 2007-06-29
Reboot and, unless you edited a config file, defaults will be restored.

See if this link helps : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by monsta on 2007-07-06
First type in

sudo iptables -L

to list all the rules that you have input. If you are still not happy with them then:

Just type in:

sudo iptables -F

this will completely '(f)lush' the whole of the iptables rules that you have input.
also get rid of any scripts that you have set up to make the iptable rules, otherwise, next time you restart your machine, iptables will be back to it's old self

---

### Post by r4ik on 2007-07-06
Try.

[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

Good luck !

---

