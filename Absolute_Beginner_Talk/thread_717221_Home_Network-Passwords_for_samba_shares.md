---
title: "Home Network-Passwords for samba shares"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by rbc on 2008-03-06
Finally, finally, finally I had a breakthrough, thanks to all you wonderful folks. I have a Vista laptop, an Ubuntu laptop, and an Xubuntu laptop. On the *buntu computers, I think Samba-common was already installed in Synaptic. I installed Samba, or vice versa, then followed these instructions (very helpful!!):
[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm), then ran “sudo apt-get install smbfs. Now all three computers can access one another. Here is the question:
1.When I initially accessed the Linux *buntu computers from the Windows one, I had to type the computer name and password (which I gathered is actually the samba user password). I no longer have to do that, but....I prefer that. What has to be done so that a password has to be entered to access the remote computer at all, or at least the shared folder?


I have come a long way with Linux and Ubuntu, but ignorant people terms/explanations would be appreciated.

---

### Post by njparton on 2008-03-07
Windows caches (remembers) network passwords which is why you've not been asked to do it again.

I don't think this can be changed unfortunately, but I may be wrong.

---

### Post by tact on 2008-03-07
> **rbc said:**
> Finally, finally, finally I had a breakthrough, thanks to all you wonderful folks. I have a Vista laptop, an Ubuntu laptop, and an Xubuntu laptop. On the *buntu computers, I think Samba-common was already installed in Synaptic. I installed Samba, or vice versa, then followed these instructions (very helpful!!):
[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm), then ran “sudo apt-get install smbfs. Now all three computers can access one another. Here is the question:
1.When I initially accessed the Linux *buntu computers from the Windows one, I had to type the computer name and password (which I gathered is actually the samba user password). I no longer have to do that, but....I prefer that. What has to be done so that a password has to be entered to access the remote computer at all, or at least the shared folder?


I have come a long way with Linux and Ubuntu, but ignorant people terms/explanations would be appreciated.

On the linux boxes check the /etc/samba/smb.conf files and look for the "security=....." line.

Security = share       means that no password or username is required to access the share as per normal windows networking.

security = user     means username and password (samba username/password) will be required.

---

### Post by jonabyte on 2008-03-07
njparton is correct. Windows does store network passwords in a file. This saves you having to enter passwords every time you access something on the network.

---

### Post by Oldsoldier2003 on 2008-03-07
> **jonabyte said:**
> njparton is correct. Windows does store network passwords in a file. This saves you having to enter passwords every time you access something on the network.
Ubuntu has this ability also. seahorse (gnome) allows you to cache local passwords and credentials for varying amount's of time. in Kde i think its the wallet (don't remember its been awhile since i've used Kubuntu)

---

### Post by rbc on 2008-03-07
Unfortunately I am at work so i cannot test any of this, but from what I'm gathering, even if I edit the smb.conf file so that "security=user", Windows is going to cache the password?

---

### Post by njparton on 2008-03-07
> **rbc said:**
> Unfortunately I am at work so i cannot test any of this, but from what I'm gathering, even if I edit the smb.conf file so that "security=user", Windows is going to cache the password?

Correct.  I'd also like to do what you want but I haven't found a way.

---

### Post by rbc on 2008-03-07
njparton, does this look like a fix? It involves messing with the registry, which I'm always a little hesitant to do? If it cannot be done, no big deal. I mean, I'm sharing between my own computers on my own home network, so having passwords for the shares is completely unnecessary.

---

### Post by rbc on 2008-03-07
Sorry. Forgot to include the link:
[http://www.vistax64.com/tutorials/76354-cachedlogonscount.html](http://www.vistax64.com/tutorials/76354-cachedlogonscount.html)

---

### Post by njparton on 2008-03-07
> **rbc said:**
> njparton, does this look like a fix? It involves messing with the registry, which I'm always a little hesitant to do? If it cannot be done, no big deal.

No that's for user account logons, not network drive password caching.

> **rbc said:**
> I mean, I'm sharing between my own computers on my own home network, so having passwords for the shares is completely unnecessary.

Doesn't that completely undermine your whole post? :)

---

### Post by rbc on 2008-03-07
I should have clarified that a little better. What I meant was that even though it is unnecessary, I still would like to at least have the option to force password usage

---

### Post by njparton on 2008-03-08
Me too, and although I've not done a lot of research, I gave up after I found out it was a windows issue and I couldn't find any obvious options to control this in windows.

---

### Post by rbc on 2008-03-13
Watch this:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Then, read this:
[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)

---

### Post by njparton on 2008-03-14
That's not a bad guide for someone trying to get samba up and running for the first time but it doesn't address the point of this thread for which there currently appears to be no solution.

Caching of passwords is a windows issue not a linux/samba issue.

---

