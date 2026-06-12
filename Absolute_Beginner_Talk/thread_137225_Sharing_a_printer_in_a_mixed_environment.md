---
title: "Sharing a printer in a mixed environment"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by secular on 2006-02-27
I've been able to use ubuntuguide.org and this forum to set up sharing a printer connected to an Ubuntu machine with other Ubuntu and WinXP computers.

Right now, they are working fine, but I see a potential problem for me. 

The different directions I found and the ones I followed all tell me to put the printer-sharing Ubuntu machine's IP address in a conf file and that same IP address in another conf file on each Ubuntu machine accessing that printer over the network. 

I'm inside a lan at a school, and I know that the next time I turn off and re-start my printer-sharing Ubuntu machine--or, more likely, bad weather knocks out the network--the IP address might change. 

Will I have to set up the printer sharing all over again the next time one of these events occur? If so, is there a way to do this without using IP addresses? 

Many thanks to anyone who can lend a hand here.

---

### Post by secular on 2006-02-28
Well, it's happened. The electricity went off for a couple of hours last evening, and the IP address on the printer-sharing Ubuntu machine has changed.

In the client.conf file on the other Ubuntu machines, I now have to change the IP address, and that will take a while each time.

Can I specify a hostname or something like that in the client.conf file? I've tried the hostname by itself, but that doesn't work.

It would save me a lot of time and frustration if anyone could point to a good solution here.

Thanks.

---

### Post by secular on 2006-02-28
I think I've found a good solution based mainly on information I got from [http://gerona.gov.ph/davidjr/?p=57]("http://gerona.gov.ph/davidjr/?p=57")

I changed a few things, and I think I have a good method for others in my shoes to follow. I'll try to post exactly what I did tomorrow.

---

### Post by secular on 2006-03-01
Here's how to set up printer sharing in an Ubuntu 5.10, WinXP Pro, and Win98SE environment inside a LAN -- one that has a DHCP server which can 
occasionally change IP addresses. I figured out some of this by myself but stole most of it from [http://gerona.gov.ph/davidjr/?p=57]("http://gerona.gov.ph/davidjr/?p=57") and multiple posts on this forum.

On the Ubuntu computer acting as a Samba file server and print server (hereafter referred to as **SambaGal**), do the following:
Open the terminal & type ```
sudo gedit /etc/cups/cupsd.conf 
``` & supply the root password. This will open a text editor. Make sure to save a copy for a backup. Then delete all the text in the cupsd.conf file and add the text below, modified a bit for your LAN:

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
**Allow From 192.168.1.***
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
**Allow From 192.168.1.***
</Location>

Here are some notes for the above cupsd.conf file:
--Do not change **Allow from 127.0.0.1** -- I think this is **SambaGal** talking to herself, and that's a good thing.
--Change the two instances of **Allow From 192.168.1.*** (made-up IP address). Inside my part of the LAN, all computers have the first 3 sets of 
numbers in common. That's the reason for the asterisk in place of the 4th set of numbers; it's a wild card to include every one inside my part of the LAN. I also put the asterisk there because the fourth set of numbers in **SambaGal**'s IP address changes sometimes--when I restart her, when the network goes nuts, when the electricity goes out, etc.
--To get the IP address for **SambaGal**, type ```
ifconfig 
``` into the terminal. Once you get it type the first 3 sets of numbers as-is and type an asterisk in place of the numbers in the the fourth set. I hope a network person in the forum will correct this if it's mistaken.

Save the cupsd.conf file and exit the text editor.

Next on **SambaGal**, open the cupsd-browing.conf file by typing into the terminal ```
sudo gedit /etc/cups/cupsd-browsing.conf
``` . This will open a text editor. Change the **No **to a **Yes**. Save that file and exit the text editor.

Restart CUPS by typing into the terminal ```
sudo /etc/init.d/cupsys restart
``` . 

**SambaGal **is now set up.

------------------------------------------------------------------------

**On all of the other Ubuntu 5.10 computers**, leave all files as they are (unless you've made previous changes) and do the following:
--Click on **System **-> **Administration **-> **Printing**
--In the Printers dialog window, click on **Global Settings** and check **Detect Lan Printers**
--Click **OK** when given a warning about security and opening a port
--Click on **Printer **-> **Add Printer** to open the printer wizard
--In the Add a Printer dialogue window, click on **Network Printer** and make sure it says **CUPS Printer (IPP) **in the drop-down field
--In the URI field, type ```
http://SambaGal:631
``` (change **SambaGal **to your server's name)
--Click the **Forward **button
--Select the proper printer and driver or download the driver for it and follow the prompts in the printer wizard
--Wait a moment to see two new printers show in the Printers window. One is checked as default, and that is the one that works. I don't know why the other one is there, but it seems that it needs to be; it has the same printer name as the default printer with -1 added to its name

-------------------------------------------------------------------------------

For the WinXP and Win98SE computers, just install a network printer at the following address: ```
\\SambaGal\printername 
```(again, change **SambaGal** to your server's name)

It should all work now. Good luck to anyone who tries this.

---

