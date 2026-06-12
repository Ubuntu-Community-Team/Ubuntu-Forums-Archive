---
title: "Printing on windows machine"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by NikoC on 2007-03-07
Oow boy, getting printers installed on an XP machine has been giving me quite some trouble! I've  read and tried out numerous solutions posted on this forum (reconfiguring samba, unix printing system, installing via cups,dis/enabling bidirectional printing), yet I've failed installing an HP Laserjet 2200 and HP Deskjet 980 printer that are connected to a windows xp pro machine. I decided to try the rc3 livecd from pclinuxOS and guess what, printers installed flawlessly... however I'm so hooked up to ubuntu I just don't want to switch to PCLOS and I want to get the printers up on my Feisty box! So this is the error problem I keep getting:

Via printer properties:
"Ready: /usr/lib/cups/backend/smb failed"
Via cups ([http://localhost:631/printers/](http://localhost:631/printers/))
"Unable to connect to CIFS host, will retry in 60 seconds..."

At home I'm using an HP Laserjet 1100 shared on a windows xp machine and this is working just fine on my ubuntu lappy... so where am I going wrong?

---

### Post by Abhi Kalyan on 2007-03-07
Hi!
Could you please repost with the following details
1. The OS from whihc you are trying to connect to the Printer
2. The type of established network connection
3. wheather you are able to ping to the Printer host machine
4. Name of the printer on the printer host machine
5. Is the printer shared on the printer host machine
6. The Procedure that you had used to connect to the printer on the printer host machine

7. Any other problems that you might be facing currently

Hoping to solve this issu, or atleast to point you in the direction towards your goal.

All the best

---

### Post by NikoC on 2007-03-07
1. Os: Ubuntu Feisty (herd 3 installed, but updated on a daily basis, i.e. this morning)
2. University network with cabled access via a D-link switch and automatic configuration (DHCP)
3. Ping statistics: 4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.256/0.277/0.298/0.022 ms
ps. I can ping on the IP of the printer host as well on the Hostname
4. 'laserjet'
    'deskjet980'
    so no spaces in their names ;-)
5. Printer is shared on the host and users have been configured
6. [http://ubuntuforums.org/showthread.php?t=32190](http://ubuntuforums.org/showthread.php?t=32190) --> general modus operandi for installing windows shared printers
   --> also tried en/disable unix printing, adding printer via cups, ... (see first post)
   --> the 'general modus operandi' works on PCLOS so this should do the trick on Ubuntu, yet no success
7. File sharing on the XP machine works: I have access to my personal folder on this machine and file transfer is flawlessly (every lab-associate has its own folder on the xp pro machine)
The printer says 'ready' in Fesity but that's due to the fact that samba is working for this machine. The strange thing is when I enter the IP of the host it does not detect the printer while at home for my Laserjet 1100 it does and the same goes for PCLOS at home and at work (so PCLOS 'sees' the printers at home and at work, while Feisty only 'sees' the on at home)

---

### Post by Abhi Kalyan on 2007-03-07
1. DHCP gives out IP's, are these IP's Dynamic or are they reserved?
2. The system on which the printer is connected, does it have a static IP?
------------------------------------------------
1. If the printer Host is "A", and the sharer system is "B"
2. "A" running on XP Pro and "B" is running Feisty[If i have understood correct]
3. in "Add a printer" choose "Network Printer" "Windows Printer (SMB)".
4. Do not fill in the user name or the password now, how many ever times the systme asks you.
5. in "Hosts" give the name of the host - [Please make sure that the print server has a static IP, If not please post back]
6. in "Printer" type in any of the printers names, each cycle adds only one printer so type in only one name now Ex: laserjet.
7. "forward" choose the manufacturer and the driver.
8. "Forward" Apply. The printer should be added now.
9. **Open the printer properties and in "Connections" fill in the username and the password.**. Test if you can print.
Hope this helps.
If i have assumed any thing wrong here please post back

---

### Post by Abhi Kalyan on 2007-03-07
smbfs, winbind need to be installed using apt-get, before we can do anything.

---

### Post by NikoC on 2007-03-07
Installed the 2 suggested packages. Then followed the steps of your previous post, yet not success so far. To answer your questions:

1. All registered computers, including mine, have static IP's
2. So does the machine the printer is connected to
------

All the other assumptions were correct and the suggested method to install smb printers should work indeed (as it did in PCLOS), but seems to be failing in Ubuntu. Nevertheless already major thanks for the offered help!

edit: the only thing that I see that is different from the PCLOS options is that I can't set a workgroup name in Feisty, I don't really know if that would matter.
edit2: when the printer installation is scanning the network for hosts, it does not display the xp machine to which the printer is connected, yet I can manually connect via smb://Stress1 (this is the host's name)

---

### Post by NikoC on 2007-03-08
*bump*

---

### Post by NikoC on 2007-03-14
Okay finally got it working... 
It seems that samba does not do well with passwords containing spaces, so I created a new account (just for printing) on the windows machine without any 'special' characters in it (no, altering the password on the xp box was not an option ;) ). Now it prints flawlessly!

Never give up! :guitar:

---

### Post by 1oki on 2007-05-01
Hmmm I have this problem too... worked fine before I upgraded to Fiesty, now its being a pain. Im using a Samsung SCX-4100 printer and had to mod the linux drivers a tad... but it was working flawless before... Now I am getting this error:


Printing: Unable to connect to CIFS host, will retry in 60 seconds...

or I get 

Ready: /usr/lib/cups/backend/smb failed

or

Ready: No %%BoundingBox: comment in header!

But now that I think of it, I believe the printer setup should have been left at the HP instead of SMB... I will give that a shot when I can look at what the IP was for the machine in a little... 
Yes, I know its a samsung, but it uses the same port as an HP.

hell, Im gonna try a reboot. /me crosses fingers and hopes the old windows reboot works for Ubuntu!

---

### Post by 1oki on 2007-05-01
heh, never mind... before Ubuntu was able to find the printer using the windows network name of the computer... I put the IPaddress in where the winbox name was... works now :)

---

