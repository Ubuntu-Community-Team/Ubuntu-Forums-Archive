---
title: "Reset to default"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by tolmun on 2007-12-22
On Ubuntu Gutsy 
After execute this:

$ sudo cp ~/Desktop/firewall /etc/init.d/firewall
$ sudo chmod 755 /etc/init.d/firewall
$ sudo ln -sf ../init.d/firewall /etc/rcS.d/S42firewall
$ sudo /etc/rcS.d/S42firewall restart

How to unistall the script and restore to default?

[Link]("http://users.piuha.net/martti/comp/ubuntu/en/install.html#10")

---

### Post by tgilber1 on 2007-12-22
if the firewall script is part of a debian or ubuntu package either of the two commands should work

sudo apt-get purge <pkg-name>

sudo dpkg --purge <pkg-name>

When using a remove or purge, make sure that you check to see what other dependencies these removal/purge commands will remove.  Otherwise, you may remove more than you want, especially when using wildcards.  For example, sudo apt-get purge mono* prompted me to remove more packages that I wanted.  Hence, I made the command more specific by naming each mono package specifically.

Another note, if your firewall is preventing Internet access, type "sudo iptables -t nat -F" & "sudo iptables -F" to clear the firewall.

At this point, you can reinstall the firewall package, which should give you back the original file you had to begin with.  Remember make a backup copy of config files you tweak in case you hose a file.

Lastly, to learn more about firewalls, more specifically iptables, you can check out the following URL [http://netfilter.org/](http://netfilter.org/)

Good Luck!

---

### Post by tolmun on 2007-12-22
I follow the firewall configuratin on this[ site]("http://users.piuha.net/martti/comp/ubuntu/en/install.html#10").
And apply it on new fresh ubuntu installation.
And now i woud like to restore to default.
If i remove the symlink and the firewall script its not enought?
The script make changes to ip tables?

Thanks.

---

### Post by tgilber1 on 2007-12-22
Before you remove the file the file /etc/init.d/firewall, you should stop the firewall first with the following command

sudo /etc/init.d/firewall stop

Then, remove the symbolic links out of your rc.# directories along with /etc/init.d/firewall.

At this point, you should be all set.  You should not have to reboot to be up and running.  Upon next reboot, your firewall should be open, i.e. policies and rules.

Note:  to be sure that the firewall is not in effect, run the following command

sudo iptables -L

policies should be set to ACCEPT - see example below

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by tolmun on 2007-12-22
Thank you very much, to help me resolve the enigma.

---

