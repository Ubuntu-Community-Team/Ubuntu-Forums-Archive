---
title: "Printer problem"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by heltinde on 2005-05-28
First of all - I have been looking arround in this forum and Google, but I (obviously) didn't find a solution to my problem. My eyes are sour of intensive reading, so bear with me, if I am posting a thread that has already been posted before.

I installed Ubuntu 4 days ago. No problem and I had fun untill I wanted to install my printer. No matter what I do, it won't work.

My printer is a HP Deskjet 970cxi, and is attached to my network. I know the print servers IP-address.
I've tried the Add Printer thing, CUPS and smb. I really need new ideas to solve this.

If you can help me, please be simple in your explanation since I'm a new born baby in the Linux world.

---

### Post by clb137 on 2005-05-28
[QUOTE=heltinde]First of all - I have been looking arround in this forum and Google, but I (obviously) didn't find a solution to my problem. My eyes are sour of intensive reading, so bear with me, if I am posting a thread that has already been posted before.

I installed Ubuntu 4 days ago. No problem and I had fun untill I wanted to install my printer. No matter what I do, it won't work.

My printer is a HP Deskjet 970cxi, and is attached to my network. I know the print servers IP-address.
I've tried the Add Printer thing, CUPS and smb. I really need new ideas to solve this.

If you can help me, please be simple in your explanation since I'm a new born baby in the Linux world.[/QUOTE]


Hi,

You said ur printer is on a network,  is the printer on a windows box??

If it is you need to edit your /etc/cups/printers.conf

find this line

DeviceURL smb://yourworkgroup/hostname/printername

change it to 

DeviceURL smb://Guest@yourworkgroup/hostname/printername

then resart smb or reboot ur system.

you must use printing by smb when you set up your printer,  then the workgroup will be womething like 'mshome',    'hostname' is the name of the machine with the printer attached,  printername is the name of your printer on you winbox??

good luck if you need any more info please contact me

clinton

---

### Post by heltinde on 2005-05-28
Hi Clinton

Thanks for your response. My printer (with network device), my Linux machine and my Windows machine are all connected to a switch - and the switch is connected to a router. 

Then I don't need to use the Windows workgroup, do I? I figured I should consider the Linux 'box' totally independant of Win. Am I right?

By the way, my Internet connection works fine.

Can it be something with those permissions?

---

### Post by clb137 on 2005-05-28
hi there,

Whatoperating system is the printer connected to or is it a LAN printer,  if it is connected to a WinBox then have you amended the printer.conf file as I said?

clinton

---

### Post by heltinde on 2005-05-28
Hi

It's a LAN printer.

---

### Post by clb137 on 2005-05-28
[QUOTE=heltinde]Hi
Static IP or DHCP?

---

### Post by heltinde on 2005-05-28
All the components have their own IP-addresses, so the LAN must be static.

---

### Post by clb137 on 2005-05-28
[QUOTE=heltinde]All the components have their own IP-addresses, so the LAN must be static.[/QUOTE]


Can u print to ur printer from ur win box?

---

### Post by heltinde on 2005-05-28
Yes I can print from my winbox. No problem.

---

### Post by clb137 on 2005-05-28
ok can u run through from start to finish on how u have set ur printer up in linux,  and the error message that you get,

if can post ur errors that would be better

thanks

clinton

---

### Post by heltinde on 2005-05-28
OK, here's what I do:

Add Printer
Network Printer (CUPS)
Address: [http://192.168.168.254/lpt1:631](http://192.168.168.254/lpt1:631)
Choose HP - 970c whith the recommended hpijs driver.

Then I try to do a test page. Nothing happens - I can see the print icon.

If I open the CUPS web interface, it tells me "Printer busy, will try again in 10 seconds..."

---

### Post by heltinde on 2005-05-29
I've been doing some more reading, but I really don't know how to access CUPS via web interface because it wants username and passw. I've seen, that others have the same problem, but I couldn't find a solution. Why on earth is there a secret username/passw, I don't get it. Of course it's a good thing people can't break in to the system, but I want to have that control, and I don't know how to get it, argh!

The restart of cups: I have figured out how to enter terminal, but when I try to do the restart of cupsys I get the message 'command unknown'. Then I reboot the mashine, but I would rather know how to do the restart of cups instead - I guess it would be faster.

I feel I need the above tools in order to get closer to figure out my printer problem. Please help me - there's so many things to learn.

---

### Post by clb137 on 2005-05-29
[QUOTE=heltinde]I've been doing some more reading, but I really don't know how to access CUPS via web interface because it wants username and passw. I've seen, that others have the same problem, but I couldn't find a solution. Why on earth is there a secret username/passw, I don't get it. Of course it's a good thing people can't break in to the system, but I want to have that control, and I don't know how to get it, argh!

The restart of cups: I have figured out how to enter terminal, but when I try to do the restart of cupsys I get the message 'command unknown'. Then I reboot the mashine, but I would rather know how to do the restart of cups instead - I guess it would be faster.

I feel I need the above tools in order to get closer to figure out my printer problem. Please help me - there's so many things to learn.[/QUOTE]

You need to set upa root password (see the guide 'http://www.ubuntuguide.org/#setchangeenablerootpassword) then use 'root' and your root password to gain access to webmin, iam assuming that yoiur are using webmin


good luck 

clinton

---

### Post by heltinde on 2005-05-29
Hi Clinton

It gets worse. Now I can't open the printer setup tool: Error - CUPS server cannot be contacted (translated from danish).
I guess it's because I managed to open the cupsd file and must have **** something up.

And I can't browse to 127.0.0.1:631, well I can, but when I click something I now get the message: Connection annulled (another translation from danish).

I have figured out making a root password, and I can even log in to gdm - perhaps I'm not a total failure.

Can I remove cups and install it again? I think it must be to hard for you trying to guess what I have done wrong....

---

### Post by clb137 on 2005-05-29
[QUOTE=heltinde]Hi Clinton

It gets worse. Now I can't open the printer setup tool: Error - CUPS server cannot be contacted (translated from danish).
I guess it's because I managed to open the cupsd file and must have **** something up.

And I can't browse to 127.0.0.1:631, well I can, but when I click something I now get the message: Connection annulled (another translation from danish).

I have figured out making a root password, and I can even log in to gdm - perhaps I'm not a total failure.

Can I remove cups and install it again? I think it must be to hard for you trying to guess what I have done wrong....[/QUOTE]


Hi heltinde,

Please do not give up, its all part of the fun an of course learning too.

Yes you can unimstall cups, i think you would be better off using 'synaptic' to uninstall.  

Do you use 'gnome' as you windows manager? If so start up synaptic and the hit the search button put in 'cups' then you can mark the files for removal, re start ur machine then ope a terminal and type 'sudo apt-get install cupsys'

and lets start from the begining, try things out and it is the best way to learn it took me a long while to get printing so I know what it is like

talk to you soon

good luck

clinton

---

### Post by heltinde on 2005-05-29
Damn sh..
Remove and install didn't solve the access problem! Now I'm killing the installtion. I wasn't to happy about my partitions anyway.

Do you think my install-cd is bad (I never figured out that thing about MD5)?

I won't give up! I know problems make me learn a lot, but I'm really angry with that printer issue. I know I/we will solve it at some point, but I rather prefer yesterday instead of tomorrow.

I'll be back in a couple of hours.

By the way, my real name is Lise, and I'm hoping I some day will be able to write Linux-Lise at my business card ;-)

---

### Post by heltinde on 2005-05-29
Well, now I think I've earned the right - at least temporarly - to call my self Linux-Lise. I solved the printer problem! I'm now the owner of a beautiful Ubuntu test page :grin: 

Here's what I did:
RTFM (read-that-****-manual). I found the manual to my external printserver, and I actually read it!
It said: The printserver should be treated as a BSD networked print server host. The queue name is lpt1, and the host name is the IP address you have assigned to the print server.

Life is far more simple, than we think. Clinton, thank you very much for your patience. It was so nice having somebody to discuss the problems with. I've really learnt a LOT!

Lise \\:D/

---

### Post by clb137 on 2005-05-30
[QUOTE=heltinde]Well, now I think I've earned the right - at least temporarly - to call my self Linux-Lise. I solved the printer problem! I'm now the owner of a beautiful Ubuntu test page :grin: 

Here's what I did:
RTFM (read-that-****-manual). I found the manual to my external printserver, and I actually read it!
It said: The printserver should be treated as a BSD networked print server host. The queue name is lpt1, and the host name is the IP address you have assigned to the print server.

Life is far more simple, than we think. Clinton, thank you very much for your patience. It was so nice having somebody to discuss the problems with. I've really learnt a LOT!

Lise \\:D/[/QUOTE


Hi Lise,

Gald to hear all is well on the linux front.  Good job and it is laways a good feeling when things work out

clinton

---

