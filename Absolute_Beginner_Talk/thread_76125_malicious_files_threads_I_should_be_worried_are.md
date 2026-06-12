---
title: "malicious files: threads I should be worried are?"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-10-14
hi,

I read many articles on how linux is secure and why there are no viruses (not may at least). But most of these articles were saying that even if you get infected, only the user (not the system) gets compromised. 

Here is the question: I am now paranoid about the security of the user. For example, I don't want keyloggers and staff like that spying on my passwords etc.

To date, the only thing I could find that was simillar to staff that worries me was rootkits and its security tool was chkrootkit (of course, I installed and checked immediately :)  ). What are other threads I should be concerned about? Any ideas welcome!

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=towsonu2003]hi,

I read many articles on how linux is secure and why there are no viruses (not may at least). But most of these articles were saying that even if you get infected, only the user (not the system) gets compromised. 

Here is the question: I am now paranoid about the security of the user. For example, I don't want keyloggers and staff like that spying on my passwords etc.

To date, the only thing I could find that was simillar to staff that worries me was rootkits and its security tool was chkrootkit (of course, I installed and checked immediately :)  ). What are other threads I should be concerned about? Any ideas welcome![/QUOTE]

I'll tell you what I do.  I take my most important files, the stuff I really don't want to lose, and I make them only accessable by the root user.

To do this, use the command:

gksudo nautilus

And right click on the files and change the permissions. Allow everyone but the root user to be able to just read the files, not edit. Then your most important data is protected by your password!

---

### Post by darkmatter on 2005-10-14
Not really a need to worry...

The biggest threat is that of getting rooted, and even that is highly unlikely.

As long as you make use of good ol' common sense, you'll be fine...

---

### Post by Qrk on 2005-10-14
Though you may want to install a firewall. It can't hurt. Firestarter is in the repositories.

---

### Post by towsonu2003 on 2005-10-16
thanks all :)

---

