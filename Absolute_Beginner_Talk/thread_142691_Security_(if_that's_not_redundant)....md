---
title: "Security (if that's not redundant)..."
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-03-11
Hi All,

On a whim, I installed Ubuntu last night.  Absolutely no hitches, not a one; my RAID got picked up, even.  In the words of Jeff Spicoli, "Awesome, totally awesome."

I dabbled in Unixery back in the '60s (don't tell my Mom), and am familiar with computing.  I'm new, though, to Ubuntu, and Linux OSs in general.  That being, I have a couple of questions.

First, I see there is a frontend firewall, and I'll nab that momentarily.  Aside from that, are there any other security-related things you'd recommend?  I don't fear the various virii, having written some fun harmless ones, again, back in the '60s (everyone was doing it back then), and, if I'm understanding the OS correctly, there's no real need for spyware protection.

Second, I see long lists of "must-have" items on the boards.  The thing is, they're *long*...is there a short list?  If I've got everything I need, perfect (and not surprising).  I like to keep a lean clean machine, if at all possible.

Thanks for your attention.

therunnyman

---

### Post by Pragmatist on 2006-03-11
Ok, first off, I'm no expert.  However, I'll still throw in my two cents :)

common access control mechanisms: firewalls, TCP wrappers, xinetd, passwords, filepermissions

If your system hasn't been connected to the web yet, your in great shape.  If not, you need to learn about common symptoms of a compromised computer.

Portsentry iptables, netstat, nmap, and others of their ilk, are tools to become familiar with.

tools to locate corrupted files. Tripwire, apt-get/package manager, diff  The main idea here is that you keep a backup of files that are known to be clean (Tripwire can help with this).  Then you can regularly compare those with the ones on your system.  The diff command can help compare them.

Backups of your password file, group file and so forth.

Keep a written log of everything change you make to your system, as well as regular checks of files (as mentioned above) along with other baseline information such as users on the system (again keep a record of your system when you first start out, before connecting to the internet and then you can compare).  

performance data can also be useful again using the baseline method with backups.  Tools like: free uptime sar  df

log files: you can use the syslog daemon to make log files to your specifications and use cron to automate tasks too.  Again, backups and comparisons of log files can be very useful for security.

That is all for now.  I got this from my Linux certification books, just so you know :)

---

### Post by therunnyman on 2006-03-11
Blessings on your house, pragmatist.

therunnyman

---

### Post by pradtf on 2006-03-11
[QUOTE=Pragmatist]Ok, first off, I'm no expert.  However, I'll still throw in my two cents :)
[/QUOTE]
your 2 cents are worth a lot!

what about security regarding your own users?
for instance, any user can wander around /etc because there are world read privileges (take that away and all kinds of things stop working).

read privileges unfortunately mean cat is allowed so your own users can look at file contents. this could be a major issue in something like a postfix-mysql setup where you store the mail database password in text files (got around this by making those files accessible only by the postfix user).

users can wander around var too.

so is there a way to keep them boxed up in their own little space?

---

