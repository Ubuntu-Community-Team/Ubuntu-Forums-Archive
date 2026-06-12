---
title: "Windows printer by name"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by adwatkin19 on 2007-06-28
Hi all

I use my ubuntu laptop in work, purely on preference, and upto now i have only been able to connect to printers using the IP address of the printer (had to get a status page to find this out)

We have an event on monday that requires me to connect to a printer, but it isnt there yet, but is installed on the network, basically i need to use the name, but it just doesnt seem to be having any at all. 

the printer is named: \\server1\reception$

obviously server1 is where the printer is.

can anyone help me with this as its just a little bit of any issue, and i wont have the time to collect a status printout and then connect on the day.

any help would be appreciated!!

Adwatkin19

---

### Post by Pragmatist on 2007-06-28
> **adwatkin19 said:**
> upto now i have only been able to connect to printers using the IP address of the printer (had to get a status page to find this out)
Why is connecting using the IP address insufficient?  What is a "status page"?

> **adwatkin19 said:**
> We have an event on monday that requires me to connect to a **printer**, but it **isnt there yet**, but is installed **on the network**, 

Isn't where?  It is on the network now, where is it going to be?

> **adwatkin19 said:**
> 
basically i need to use the name, but it just doesnt seem to be having any at all. 
Ok, so you don't have a name.  

> **adwatkin19 said:**
> 
the printer is named: \\server1\reception$  ...obviously server1 is where the printer is.
You do have a name!

> **adwatkin19 said:**
> can anyone help me with this
Help you with what?

---

### Post by wink on 2007-06-28
Have you checked (using Control Panel > Printers and Faxes on a Windows machine) that you have the correct share name for this printer?

---

### Post by adwatkin19 on 2007-06-29
i do have the name, but it doesnt connect to the printer and refuses to print to it, the printed item just doesnt go to the printer. 

The share name has come directly from the network manager, and is correct. 

I cant use the IP because the printer is set to DHCP so the IP changes everyday when the print is reconnected and it would mean me having to find the ip again every day. i need to be able to connect using the printer name and not the ip address. 

A status page is the sheet of paper that the printer can print out for you that shows all the settings as they are currently configured to. This includes things like an IP address etc. 

hope this helps


adwatkin19

---

### Post by HotShotDJ on 2007-06-29
> **adwatkin19 said:**
> I cant use the IP because the printer is set to DHCP so the IP changes everyday when the print is reconnected and it would mean me having to find the ip again every day. i need to be able to connect using the printer name and not the ip address.ARGH... I feel your pain.  I had the same issue on my network.  Fortunately, it is MY network so I solved it by forcing the printer to use a static IP (configured the printer for a specific IP address outside the range used by DHCP server -- different routers will handle this differently).  Of course, this is no solution for you if your not authorized to make changes like that to the network.

---

### Post by Pragmatist on 2007-06-29
[http://www.suselinuxsupport.de/wikka.php?wakka=HowToPrintLinuxToWindows](http://www.suselinuxsupport.de/wikka.php?wakka=HowToPrintLinuxToWindows)

I found that after about 5 minutes of googling.  If that doesn't work for you, I would suggest doing some more searching.

---

