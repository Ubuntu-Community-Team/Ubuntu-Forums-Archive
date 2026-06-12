---
title: "Configure ubuntu as printer server for windows clients"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-10
Hi,

I have an Ubuntu Server running as a backup server (using BackupPC) and also as a proxy server and internet content filter using DansGuardian. These work great, and since the server is running 24x7 I may as well plug my USB hp deskjet 990cxi printer into it and serve that to my windows machines.

What do I need to do in order to serve the printer to windows, Mac and Linux clients on the LAN?

Thanks for any help!

---

### Post by steve.horsley on 2007-09-10
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_a_Windows_machine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_a_Windows_machine)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine)

Not sure about from a mac.

---

### Post by keymoo on 2007-09-10
Thanks - I installed samba and cups. However I am using Ubuntu Server (no GUI) so when it says to add a printer by doing:
[LIST]
[*]Go to System -> Administration -> Printing.
[*]Choose "Add printer".
[*]"Add printer wizard" should start and tell you what to do.[/LIST]Is there an equivalent at the command line?

Thanks again.

---

### Post by steve.horsley on 2007-09-10
Probably, but I don't know what.

If no-one else can help, you could take a look at my /etc/cups/printers.conf - a manual edit might get things going:
> 
# Printer configuration file for CUPS v1.2.8
# Written by cupsd on 2007-08-21 14:44
<Printer DeskJet-1280>
Info DeskJet-1280
DeviceURI ipp://192.168.8.101/printers/DeskJet-1280
State Idle
StateTime 1186961387
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer LaserJet-4100>
Info LaserJet-4100
DeviceURI socket://172.30.2.234:9100
State Idle
StateTime 1187703859
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>


P.S.
I forgot to mention - the DeskJet is being shared by another Ubuntu, and the LaserJet is connected by Ethernet on the LAN using normal HP-jet-direct protocol or whatever it's called. I don't have access to the other Ubuntu to see what a local printer configuration looks like at the moment.

---

### Post by keymoo on 2007-09-11
Thanks steve. I don't have a /etc/cups/printers.conf

:confused:

---

### Post by reldruH on 2007-09-15
This is exactly the same issue I'm having. I have a server going 24/7 and want to hook a printer up to it so it's always available to anybody on the network but I don't know how to set it up without a GUI. Did you find a solution to this? Or have any ideas on how to get started?

---

### Post by AndyCooll on 2007-09-15
I had fun with this and got my answers from the following two threads:
[HOWTO: Setup A Headless Ubunutu CUPS Print-Server]("http://ubuntuforums.org/showthread.php?t=310450")
[Howto: configure cups on Ubuntu Server from command line]("http://ubuntuforums.org/showthread.php?t=240282")

I have the same printer as you. The second link tells you how to install CUPS and then how to give yourself administrative privileges in order that you can configure everything via a web browser.

:cool:

---

### Post by keymoo on 2007-09-17
Thanks for those links Andy. I can now print to my ubuntu server. Yay! I can print from Linux desktops and XP machines - I just need to try and set up my vista machine and my OS X Tiger desktops.

---

### Post by keymoo on 2007-09-17
Vista's working fine now, the remaining elusive machines are the OS X ones. I can't seem to get those working just yet. If anyone here has successfully printed from OS X 10.4.10 to an Ubuntu cups print server, please let me know!

---

