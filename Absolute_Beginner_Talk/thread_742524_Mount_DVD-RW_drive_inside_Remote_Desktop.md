---
title: "Mount DVD-RW drive inside Remote Desktop?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by TMcKSmith on 2008-04-01
Is this possible?  Here's what I'd like to do.  I am running Kubuntu on my laptop.  I have a PC running Windows that I connect to via Remote Desktop (Krdc).  I do not have a DVD-RW drive on my PC, however I do on my laptop.  I have a DVD iso file I'd like to burn that is on my PC.  Is there a way I can map my DVD-RW drive to the Remote machine so I can burn the file on that system?  Or, is my only option to transfer the file from the remote machine to my laptop, and then burn (which would take forever)?  Thanks.

---

### Post by computermesh on 2008-04-02
Windows don't really allow you to mount/unmount drives. It's autodetected via plug and pray and just shows up when you boot your system. Try setting the computers up on a local network and make sure you can access the file thats on that pc. Then throw a blank dvd in the computer with the burner and click on make dvd. Then it should give you an option to search. See if your able to search for the file. I know I had to type in SMB:/// or something of that nature. Just write down the directory the file is in on the windows PC and make sure that it is shared. Hope that helps of give you a start.

---

