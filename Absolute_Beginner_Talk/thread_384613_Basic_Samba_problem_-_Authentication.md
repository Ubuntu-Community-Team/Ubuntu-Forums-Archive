---
title: "Basic Samba problem - Authentication"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by OriginalGrumpyOldMan on 2007-03-14
So I'm giving Linux another try after a couple of attempts in the past that ended in frustration at the commandline. And it's not like I'm not open to do some research and learn new things... There's a number of issues I'm having with this attempt, but here's the most pressing one:

I'm trying to transfer my files over from a Windows XP to give it the boot (hardware's failing), on a mixed network.
- Mac OSX to WindowsXP: no problem: asks for authentication, then shows content of shared folder
- Ubuntu 6.10 to WindowsXP: no dice: finds Windows network, my group, then "The folder contents could not be displayed" EXCEPT -sometimes- it will show the machine, but that's the end of the road, never get to the share. Never asks for authentication.

So I tried the reverse:
Installed Samba on Ubuntu, shared a folder, opened the permissions as wide open as possible both locally and sharing.
- MacOSX: Sees the local group, the Ubuntu box inside, and lists the share, but then fails at the authentication
- Windows: exactly the same, sees everything, but then fails at the authentication.

I tried many times on both machines, using the username/password that I'm currently using on the Ubuntu box, so it is very unlikely it's a typo or case-sensitivity issue.

Help! I know I can dump the files on an external drive and copy it over that way, but in the long run there has to be a way to make this work?!

---

### Post by albs on 2007-03-14
I have the same problem - I want to transfer a file from my Edubuntu box over to my windows box.

I get asked for my username and password, and I've tried:

- my account
- root

and it'll just prompt me again, and windows changes the username to: "EDUBUNTU/my account"

I know it's probably some newbie error, but can someone please help me?

---

### Post by OriginalGrumpyOldMan on 2007-03-15
Replying to self, bad habit, I know.

But since there are so many unanswered (thus useless) posts, I thought I'd try to make this one a little more useful.

I have solved PART of the problem, namely getting from Ubuntu to my Windows PC.
- (The following may not be necessary) I made sure that in the general prefs of the "Shared folders" admin tool I set the correct workgroup (confirmed by the rather more involved commandline visit to the samba.conf file)
- I used the IP address method to get to the PC (hello fixed IP addresses, goodbye to this new-fangled Network browsing thing)
- When asked to authenticate, I LEFT THE DOMAIN FIELD BLANK (a workgroup is NOT a domain, of course) and finally I was in.

Of course trying to get from any other computer to my Ubuntu SMB share is still impossible, it simply will not accept any authentication.

---

### Post by mfrailing on 2007-03-16
Be sure to have opened the properties of the Windows folder(s), Sharing Tab, and have sharing enabled. I stumbled onto this and it helped me.

---

### Post by Scorpuk on 2007-03-17
To gain access to a samba share you will need to create a user on the samba server. 

Your samba server and your ubunto box have seperate user lists and, probably for security, your ubuntu's user list is not copied over to the samba servers list.


Not entirely sure as to the command line to add a user to samba server as I used webmin to do it, but this shoudl sort it out.

---

