---
title: "File and Print Server - How to do it?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by digitaldave on 2007-11-12
Hi all :).

Yesterday, I managed to install Ubuntu on an old PC, and I've got some grand ideas for it, but being a Linux newbie, I'm not sure where to start. What I'd like to do is to have the Linux box running as a file and printer server for use over our wireless network by me (I use an Apple MacBook Pro with OS X 10.5) and my wife (who uses a Dell laptop with Windows XP). So, I have a couple of questions...

1) File Server - how do I go about setting this up so that both my wife and I can access files on the server? Should I just create one area where we can both store files, or should there also be individual areas for each user that wants to access the server?

2) Printer server - this should be quite simple (I hope), all I want to do is to make the printer available to any user on the network so we don't have to continually swap the USB lead over every time we print from a different computer.

3) This is where it might get really complicated... Would it be possible to have the server as a headless one running the print and file servers? Unfortunately, it's not the quietest PC, so ideally, I'd love to have it be able to go to sleep when it's not in use, and wake up when it receives a print or file request - can this be done? If it is possible, can use my Mac to remotely access the server for administration etc., and if so, how?

Please bear in mind that I'm a complete Linux novice, so keep it relatively simple if you can :).

Many thanks,

Dave.

---

### Post by Daveski on 2007-11-13
> **digitaldave said:**
> 
1) File Server - how do I go about setting this up so that both my wife and I can access files on the server? Should I just create one area where we can both store files, or should there also be individual areas for each user that wants to access the server?

2) Printer server - this should be quite simple (I hope), all I want to do is to make the printer available to any user on the network so we don't have to continually swap the USB lead over every time we print from a different computer.


You can install Samba (server) - the Windows File and Printer sharing server. The Samba client is part of the default install and so Ubuntu can access Windows shares, but you have to install the server component from the Repos. Once you have Samba server configured, Windows and Macs can access these shares (although I am not familiar with how much you have to configure on the Mac).

The alternatives include using Linux native file sharing called NFS, of which there are clients available in both Windows and Mac.

---

