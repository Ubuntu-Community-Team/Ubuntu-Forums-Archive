---
title: "Big Firestarter problem"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-01
Okay, well I was trying to get my Frostwire connection working and I came across a place on the internet that said it could have something to do with my firewall settings. So what I did was went in and stopped the firewall, and then locked it. Well, now I can't even open firestarter!! And I have to use a different computer entirely now to post this because that firewall is locked!](*,) 

What can I do!? I tried opening it with the terminal and it said that it didn't have admin/root privelages, so I tried using sudo but it just stalled and didn't do anything. I'm using dapper if that helps any.

---

### Post by ajgreeny on 2006-11-01
Try the following:-
1   Uninstall firestarter
2   Do the following in a terminal:-
sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo dpkg -P firestarter
sudo /etc/init.d/networking restart

This should make sure that your firestarter is removed completely, your iptables is cleaned and flushed and then networking is restarted.

After that install firestarter again if you want to.

---

### Post by ajgreeny on 2006-11-03
Hi again, voodoonirvana.  Just interested to know if you tried my method to sort out the problem and if it worked or not.  Let us all know either way, as it can be very helpfull to us if we know something has worked, and also if it hasn't.

---

