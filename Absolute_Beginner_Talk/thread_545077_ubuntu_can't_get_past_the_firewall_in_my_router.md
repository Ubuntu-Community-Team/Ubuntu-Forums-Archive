---
title: "ubuntu can't get past the firewall in my router"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-07
I have 300kbs broadband connection, but by the time it gets to Ubuntu it's only 3.5kbs
I installed firestarter, and turned the firewall off on ubuntu and even enabled the 
the "work outside the NAT" feature on my router trying to solve this problem. Have had this problem for 3 weeks now getting worn out. Want to keep Ubuntu, but it's getting real hard to find ways to get around these things. no one seems to be able to help. Maybe I'm unlucky. I also so have issues with wireless usb adapter,  file sharing and 
intel modem, Outside of these networking issues. Ubuntu is the coolest software I've ever put on my Computer, and I know these things can work if someone is willing to help
me. I love the things Ubuntu allows me to do With the open office, gimp, pdf editors and  
all that good stuff, but you can only live with a wire-bound 3.5kbs network that can't share files for so long before you have to throw in the towel. so please help if you can thanks.

---

### Post by ajgreeny on 2007-09-07
Try stopping and uninstalling firestarter, flushing your iptables and then restarting networking.  Then reinstall firestarter if you really want to, it's not usually needed.

sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo dpkg -P firestarter
sudo /etc/init.d/networking restart

---

