---
title: "samba printer"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ambre on 2008-03-30
Hi,

I am using 7.10 and am trying to set up a new printer using System|Administration|Printing.

The printer is on a WINXP machine and is shared under Windows.

Using 'Windows printer via SAMBA'; the browse function does not find my WINXP printer (or my WINXP machine that the printer is connected to).  However, if I use Places|Network I can see the printer folder (marked as FTP) together with my other WINXP machines and 'Windows Network'.

Why is the browse failing to see my share?

Thanks,
Fred

---

### Post by cmnorton on 2008-03-30
This is not a solution, but may be instead some places to start. First, I am not at work where I have this all set up, but this sounds very, very familiar. 

Our Windows domain ends in .local. I have posted all over the place to inquire why on Windows our domain shows up as workdomain and not workdomain.local. That however is for another discussion.

I had to put our full domain name in /etc/resolv.conf at the top of the file above the nameserver entries. I cannot say for sure it has to go at the top of the file,  but that's where it is in my resolv.conf.

I cannot remember in System -> Administration -> Printing if you use the full domain name or just the first part of the domain name. This obviously won't apply if your domain name is Fred and not Fred.local.

When I get to work tomorrow, I'll have a looksie to see how my printer is set up, and it might be a little wierder than yours, because I'm running XP (workstation), not server. From Linux and especially Ubuntu connecting to any printer that's networked is a piece of cake. You don't need samba, but instead JetDirect. The samba part is a little trickier.

I'll check back tomorrow. If you don't have an answer I'll post my config.

---

### Post by cmnorton on 2008-03-31
Here's what I have in printers.conf for my samba printer:

<DefaultPrinter lp>
Info HP LaserJet 1320
Location office
DeviceURI smb://my_user:my_password@MyDomain/my_user/my_printer
State Idle
StateTime 1205439550
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

my_user is both my Linux and Windows user name. my_printer is the Windows share name. Our domain is MyDomain.local, but I only use MyDomain.

You should be able to tweak all this right in the menus. I did, and it worked well. Ubuntu's interface is quite good. 

If you cannot get what you want there, either edit /etc/cups/printers.conf directly or use a browser localhost:631 (before which you'd add yourself to the lpadmin group).

---

