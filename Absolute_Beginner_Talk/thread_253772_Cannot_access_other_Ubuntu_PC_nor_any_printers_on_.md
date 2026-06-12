---
title: "Cannot access other Ubuntu PC nor any printers on network"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by iorbell on 2006-09-08
Hi,

I have Dapper (AMD64) installed successfully on two PC's that sit physically next to each other and are attached to the same router (for internet access) via a wired access.

Both PC's work fine, the install of Ubuntu was generally without issues, I can access the Internet from both PC's with no problems, and I can do audio encoding (my other biggest use of the PC's apart from Internet access) very successfully. Overall, I am very pleased with Ubuntu and intend to move entirely from Windows to Ubuntu once I can get the following items sorted....

However, I have two problems, and I can only imagine I am missing something really, really simple. I cannot access (or see) either the other PC nor any of the two network printers (HP and Samsung) from either PC. I have used the Network File Browser (just shows WIndows network which is empty when I drill down into it).

I ***can*** ping to each machine from the other.

IP addresses are as follows

PC1 - 192.168.2.9
PC2 - 192.168.2.5
Samsung printer - 192.168.0.10
HP Printer (cannot remember for the moment)

I assumed I would at least be able to see the other PC fairly easily.

Any ideas or suggestions?   Thanks in advance.   Ian

---

### Post by croc1 on 2006-09-09
Do all the machines have the same Domainname (workgroup name)

---

### Post by iorbell on 2006-09-09
When looking at System/Admin/Networking and the 'General' tab neither of them show a domain name (which I guess is a problem).

I entered a value in that field for both PC, saved it, then rebooted, but when they both rebooted, neither had a domain name in that same tab - what was I doing wrong?

Ian

---

### Post by seshomaru samma on 2006-09-10
what do you get at places>network servers?

---

### Post by iorbell on 2006-09-10
Just an icon for 'Windows Servers' with nothing showing underneath it.

---

### Post by bodhi.zazen on 2006-09-10
first the printer: I advise cups.

Open a browser and type
```
localhost:631
``` in the address bar. This will bring up a browser page for the cups server. I can not advise further without more information. Is this a network printer? IP address? type/model of printer?

As far as connectivity, how are you trying to connect? samba, ssh, vpn? Each of these options will work but it sounds like you need help with configuration.

Since you are going Linux -> Linux I suggest ssh. ssh will forward X. vpn works as well but is slower. For file transfer nfs (nfs will allow you to mount remote directories).

---

### Post by iorbell on 2006-09-10
Many thanks for your help.

On the printer side the printer is a Samsung ML-2010 laser printer (I already have the Sunsung Unified Driver installed on my PS under Ubuntu).

Its location is 192.168.0.10 (at least thats 

On the CUPS screen (localhost 631 etc), it shows no printers - not sure if that just means I need to set one up or whether it means I should see one but do not (and therefore have a problem). I started to go through the 'Add Printer' dialog, but stopped at the 'Device for [printername] choice - not certain if I should use IPP or what, and if IPP, what the device URI should be.

The printer is on a different subnet to the PC (192.168.2.9 v 192.168.0.10) - is that a big problem?

I think the reason for that BTW is that I have two wireless routers in my set up (needed more that 4 wired connections, so the two routers are set up in serial). However, all the wireless connections in Windows worked fine with no change to the router set exactly as now.

Both Ubuntu PC's are connected (wired) into the same router - the Samsung printer is connected (wired) into the other router. To connect between the two PC's I had been trying to use SSH - using the 'Connect to remote server' option...although I had also tried ftp, public ftp etc etc. - None received any response from the remote server - even though I mcan ping to it successfully.

I hope this answers the questions you raised.   Thanks again for your help.

Ian

---

### Post by bodhi.zazen on 2006-09-10
> **iorbell said:**
> Samsung ML-2010 laser printer Its location is 192.168.0.10

I use ipp
```
ipp://192.168.0.10:631/ipp
```is what you want.

Subnet should not matter.

So....
[list=number]
[*]Click "Add printer"
[*]Location="Local Printer" Description="Samsung ML-2010"
[*]Device="IPP (Internet Printing Protocol)
[*]Device URI="ipp://192.168.0.10:631/ipp"
[*]Select your printer if listed or "Provide PPD file" -> Browse to your Samsung driver (PPD)
[/list]

Local printer because you are using cups locally, not via logging into a different box. Clear as mud, no?

Now print a test page.

If it works, set as default.

---

### Post by iorbell on 2006-09-11
Many thanks...I will try this tomorrow...I tried this evening but CUPS kept asking me for a username and password, and not accepting any of my known User/pw combinations. I did a search on the web and found this is not unknown and was trying some of the ways I found to get around that (e.g. editing the cupds.conf file to change authtype to Shadowhash)...then I could not restart the CUPS process, so I thought I would reboot...thats where I got to tonight.

However, I think we are near, and I appreciate your help. I'll let you know the outcome tomorrow.

Ian

---

### Post by bodhi.zazen on 2006-09-11
> **iorbell said:**
> Many thanks...I will try this tomorrow...I tried this evening but CUPS kept asking me for a username and password, and not accepting any of my known User/pw combinations. I did a search on the web and found this is not unknown and was trying some of the ways I found to get around that (e.g. editing the cupds.conf file to change authtype to Shadowhash)...then I could not restart the CUPS process, so I thought I would reboot...thats where I got to tonight.

However, I think we are near, and I appreciate your help. I'll let you know the outcome tomorrow.

Ian

Did you try this:
[CUPS on Ubuntu](http://dramor.blogspot.com/2004/12/todays-stupid-trick-on-ubuntu.html)

> In summary, the answer is:

adduser cupsys shadow
/etc/init.d/cupsys restart

They also say to use :
> GNOME CUPS manager (Computer > System configuration > Printing)
This has never worked for me... Thus I advised CUPS. Sorry if it was so inconvenient.

I think I enabled cups on my box by enabling su (setting to root password).

---

### Post by iorbell on 2006-09-11
Thanks...printer is set up and displays on the CUPS admin pages.

I tried printing a test page but the response within CUPS is

"Network host '192.168.0.10' is busy; will retry in 30 seconds..."

...and its actually not busy printing anything at all.

Any idea what might be causing that?

The CUPS error message log shows

"E [10/Sep/2006:21:58:03 -0700] Unable to bind socket for address 127.0.0.1:631 - Permission denied.
E [10/Sep/2006:21:58:03 -0700] cupsdStartBrowsing: Unable to bind broadcast socket - Permission denied.
E [11/Sep/2006:02:59:42 -0700] Unknown Location directive AuthType on line 47."

To avoid that last error line I reverted to the default configuration file, and restarted CUPS.

BTW - in the setting up of the printer it never asked me to choose 'local' anywhere.

Ian

---

### Post by bodhi.zazen on 2006-09-11
I will need to look into this a little later. I do not know if this is the problem or not...

When you first his "add printer" the very next (first) screen has a pull down menu. You need to select "local printer" and not network printer. This refers to where you are connecting to cups not the location of the printer.

I think this is the source of your error although I am not certain.

---

### Post by bodhi.zazen on 2006-09-11
For remote access, I assume you are interested in ssh.

Install ssh and openssh-server. Add yourself to ssh group on both boxes.

You should be able to connect, this is a CLI connection although you can ssh -X to forward X.

Alternate look at vpn. You need to allow a connection in the vpn pull down menu on the "server" or box you want to connect to.

---

### Post by iorbell on 2006-09-12
I added ssh and openssh-server to both machines.

Should there already be an ssh group set up? (I can see an ssh-agent process running already on both boxes). I did not want to set up a group needlessly.

Should I just use addgroup and adduser to create the ssh group and to add my user to it?

BTW - on the CUPS thing I set up a printer from scratch again, and no prompt for network or local shows up at all in the process. I used the System/Printing option and chose 'Local' there, but then it did not let me enter any ip address anywhere. I also chose Network instead of local - but same sort of result...job never prints and CUPS error log shows the following

I [11/Sep/2006:21:44:08 -0700] New printer "Samsungnetwork" added by "root".
I [11/Sep/2006:21:44:22 -0700] Started "/usr/lib/cups/daemon/cups-driverd" (pid=13642)
I [11/Sep/2006:21:44:24 -0700] Started "/usr/lib/cups/daemon/cups-deviced" (pid=13644)
I [11/Sep/2006:21:44:29 -0700] Adding start banner page "none" to job 11.
I [11/Sep/2006:21:44:29 -0700] Adding end banner page "none" to job 11.
I [11/Sep/2006:21:44:29 -0700] Job 11 queued on "Samsungnetwork" by "ian".
I [11/Sep/2006:21:44:29 -0700] Started filter /usr/lib/cups/filter/pstops (PID 13671) for job 11.
I [11/Sep/2006:21:44:29 -0700] Started filter /usr/lib/cups/filter/rastertosamsungspl (PID 13672) for job 11.
I [11/Sep/2006:21:44:29 -0700] Started backend /usr/lib/cups/backend/ipp (PID 13674) for job 11.
E [11/Sep/2006:21:44:29 -0700] [Job 11] No %%BoundingBox: comment in header!
I [11/Sep/2006:21:46:04 -0700] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=13772)
I [11/Sep/2006:21:46:18 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=13788)
I [11/Sep/2006:21:46:18 -0700] CUPS-Get-Default client-error-not-found: No default printer
I [11/Sep/2006:21:46:33 -0700] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=13806)
I [11/Sep/2006:21:46:34 -0700] Started "/usr/lib/cups/daemon/cups-deviced" (pid=13807)


Ian

---

### Post by bodhi.zazen on 2006-09-12
You should have a ssh group already.

I am afraid I am failing with the cups. The pritn out, was that from the print a test page in cups or an application? It appears you have not set the printer as default (you can do this in the cups menu).

Here is the second cups page I get:
		
Add New Printer
Name: 	
(May contain any printable characters except "/", "#", and space)
Location: 	**put "Local Printer" here**
(Human-readable location such as "Lab 1")
Description: 	
(Human-readable description such as "HP LaserJet with Duplexer")"

At any rate, is this printer a usb or network printer? I have been assuming it was a network printer.

Perhaps this helps:
[Site 1](http://www.linuxquestions.org/questions/showthread.php?t=417541)
[Linux Usb Devices](http://www.qbik.ch/usb/devices/showdev.php?id=3758)

---

### Post by iorbell on 2006-09-12
Well, I have had one success - I can now login to the pc's from each other - in the end I realised the deafult firewall setting (from firestarter) was blocking ssh. I could not believe I had not thought of the firewall :)

I'll try putting local printer in the location item, and make it the default.

The Samsung is a USB printer, but its on a network print server (a little D-Link DP-G310) so I am treating it as a network accessible printer.

Thanks again for all your help...I am very close to getting rid of Windows entirely on my system (thats a kind of goal of mine)...your patience and support has been very good to have!

Ian

---

### Post by bodhi.zazen on 2006-09-12
8-) If ssh is not to your tastes you can try vnc.

Good luck with your priter [-o<

---

### Post by Smuve on 2006-09-12
iorbell

I'm not sure if this helps, but I just got my Canon Pixma ip4200 working on my dlink dpr-1260 print server.

After I figured out what information I needed, it was actually quite easy.

Before you proceed, log into your print server and in the status page, find your:

Print Server:  mine was  dlinkps-454e04
LPR Queue Name:  mine was iP4200 (notice the capital "P")

Go to System > Admin > Printing > New Printer

Choose Network Printer > Unix Pritner (LPD)

IP Address = Print Server IP Address = 192.168.0.10
Queue = Print Server/LPR Queue Name = dlinkps-454e04/iP4200

Then choose your correct driver.  

It worked for me, I hope it helps.

---

