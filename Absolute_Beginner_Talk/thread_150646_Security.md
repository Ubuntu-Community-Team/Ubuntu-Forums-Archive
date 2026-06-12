---
title: "Security?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by scratched on 2006-03-26
I'm new to linux (just got ubuntu 5.10 installed friday) and I know that it is more secure out of the box than windows in a lot of ways, but I was wondering...

Should I consider installing firewall and virus scan software for ubuntu?

I'm not *too *paranoid about security and I don't usually download anything mysterious/questionable, but I'd also like to be relatively safe from hacker attacks & such.

Could someone possibly tell me how open to the internet ubuntu (and linux in general) is (like... are ports left open by default, etc.)?

---

### Post by Patrick-Ruff on 2006-03-26
hmm, well, thats kinda debatable. I know that if a hacker does infiltrate your system, there isant much he can do without knowledge of the root password. the root password is prompted for just about anything changing major stuff. including deleting etc. there are a few firewalls out there and a few antivirus'es to. heres a comparison table from windows programs to Linux programs, most all Linux programs are free. 

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by IYY on 2006-03-26
If you're really serious about security, you should download a firewall. A virus scanner is not needed, unless you want to scan Windows machines and files you may be sending to Windows machines.

Never make users with very common names and insecure passwords. For example, a machine with user 'guest' who has the password 'guest' is very easy to hack.

Also, don't install an SSH server if you don't need it.

---

### Post by mcduck on 2006-03-26
Ubuntu is fairly secure by default, there are no ports open to outside world. I ran it on my machine for 3 months until I started using a firewall, and I did that only because it was easy way to configure network connection sharing :)

If you want a firewall, you could try Firestarter, it's available in Ubuntu repositories, so you can easily install it with Synaptic or apt-get.

There is no need for virus scanner. It would only be usefull for finding windows virii anyway ;)

---

### Post by therunnyman on 2006-03-26
Hi scratched,

One the board's greatest members/helpers, Pragmatist, wrote this to me when I asked about security:

--begin quote--

Ok, first off, I'm no expert. However, I'll still throw in my two cents

common access control mechanisms: firewalls, TCP wrappers, xinetd, passwords, filepermissions

If your system hasn't been connected to the web yet, your in great shape. If not, you need to learn about common symptoms of a compromised computer.

Portsentry iptables, netstat, nmap, and others of their ilk, are tools to become familiar with.

tools to locate corrupted files. Tripwire, apt-get/package manager, diff The main idea here is that you keep a backup of files that are known to be clean (Tripwire can help with this). Then you can regularly compare those with the ones on your system. The diff command can help compare them.

Backups of your password file, group file and so forth.

Keep a written log of everything change you make to your system, as well as regular checks of files (as mentioned above) along with other baseline information such as users on the system (again keep a record of your system when you first start out, before connecting to the internet and then you can compare).

performance data can also be useful again using the baseline method with backups. Tools like: free uptime sar df

log files: you can use the syslog daemon to make log files to your specifications and use cron to automate tasks too. Again, backups and comparisons of log files can be very useful for security.

That is all for now. I got this from my Linux certification books, just so you know 

--endquote--

The first read is a little daunting, but it'll make sense in about a week.  Some of the things Pragmatist talks about have frontends - that is, GUIs - so that'll make things a little easier.  My suggestion: nab Firestarter and F-Prot for now (search the boards for thier location and installation) to put your mind at ease while you bone up on Linux security.

therunnyman

---

