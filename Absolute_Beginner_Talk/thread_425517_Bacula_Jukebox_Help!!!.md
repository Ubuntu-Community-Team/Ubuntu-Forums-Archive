---
title: "Bacula Jukebox Help!!!"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by loesr on 2007-04-27
Alright, I finally bow to the awsomeness of the Linux world.  After Trying Vista out, and consequently rejecting the $300 DX10 update, I have now installed Ubuntu on 4 of my 7 PCs.  Next I convert the family.  SWAT, Samba, Beryl\Compiz, watching TV on my Haupagge card, no problem.

One thing I can't get going to save my life is Bacula for my file server.  I have done all of the Debian walkthroughs, sync'd up all of the .conf passwords, and googled extensively.  I can't in fact find a completed install walkthrough of 2.0.3 anywhere - Debian is for 1.38, and didn't work anyway.

Regardless of what I try, I keep getting 'ERR=Connection Refused'.  I have fiddled with ports, opened up security, verified DNS resolution (running locally anyway...), verified that all three services are up and running.  I can't connect with bconsole, the gnome console, or the KDE console.  I have tried this for kicks and grins on 3 boxes.

How do you get Bacula to work?  It's undoubtedly something silly I haven't tried yet...

---

### Post by Sef on 2007-04-27
Did you install it through Synaptic or another way?

---

### Post by loesr on 2007-04-28
I used Synaptic Package Manager.

---

### Post by loesr on 2007-04-30
FYI - This is the extended debug info off of bconsole:

loesr@LOESRVILLE:~$ sudo bconsole -d100
Connecting to Director LOESRVILLE:9101
bconsole: bnet.c:781 Current host[ipv4:127.0.1.1:9101] All host[ipv4:127.0.1.1:9101] 
bconsole: bnet.c:847 Unable to connect to Director daemon on LOESRVILLE:9101. ERR=Connection refused
bconsole: bnet.c:781 Current host[ipv4:127.0.1.1:9101] All host[ipv4:127.0.1.1:9101] 
bconsole: bnet.c:847 Unable to connect to Director daemon on LOESRVILLE:9101. ERR=Connection refused
bconsole: bnet.c:781 Current host[ipv4:127.0.1.1:9101] All host[ipv4:127.0.1.1:9101] 
bconsole: bnet.c:847 Unable to connect to Director daemon on LOESRVILLE:9101. ERR=Connection refused
30-Apr 08:33 bconsole:  Fatal error: bnet.c:859 Unable to connect to Director daemon on LOESRVILLE:9101. ERR=Connection refused


I checked firewall and security howto's from the [http://www.debianhelp.co.uk/bacula4.htm]("http://www.debianhelp.co.uk/bacula4.htm")  page.  No dice...

---

### Post by loesr on 2007-05-01
Solution found!  

The issue lies in how Bacula performs DNS hostname lookups.  

If you get the "ERR=Connection Refused" message, go into ALL of the bacula .conf files and change the hostname to the IP in the address areas.  

For example on my box, I changed LOESRVILLE to 127.0.0.1 in bacula-fd.conf, bacula-sd.conf, bacula-dir.conf, and bconsole.conf.

It worked on my standalone install perfectly.

---

