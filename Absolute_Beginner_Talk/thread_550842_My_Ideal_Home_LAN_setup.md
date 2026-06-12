---
title: "My Ideal Home LAN setup??"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-09-14
*Something I've been seriously playing with but am having a hard time setting up.*

Once upon a time, in the recent past, my home wired LAN was working adequately when all 4-6 boxes were using various shades of Windows (w2k-XP).  I could share printers and files pretty much seamlessly. My big issue was with the whole "BIG BROTHER is watching aspect" of Windows not to mention the never ending security problems. (Okay, quite a few other things too) As well, I hated having my hands tied by software publishers who insisted I install their products in c:\program files regardless of where I wanted it to go.

With Linux, I was hoping to setup a LAN that incorporated both Linux (Ubuntu) boxes and Windows (a must have for BF2 and some office applications). Since everyone in the family uses the computers (pleasure, work, and homework) I wanted to set up a file server on one of the older boxes. Nothing fancy, just a common location so anyone could be using any computer and have access to music, homework, email, etc. 

The following is what I currently have BUT as a network, it's not working the way I had hoped for. (I was using a mixed system of XP/6.06 boxes and while it largely worked I was never able to tweak it the way the way I wanted it to.)  I have a D-Link EBR 2310 Wire Router connected to a cable modem. The Router serves IP addresses to all but two Ubuntu boxes...these are static:
[LIST=1]
[*]**Notebook 1:** Fixed kitchen location, used a lot for general surfing, email, chat. Has Feisty 7.04 installed.  Older box, 1.0Ghz / 10 GB HDD / 512mb RAM).
[*]**Notebook 2: **I take this on the road with me. I'm having to replace the HDD so I'll likely try to set it up for dual boot (XP/Feisty). It's old but it works fine for writing up reports and stuff. (750mhz / 40GB / 256Mb RAM)
[*]**Current Gaming Box:** XP pro/Sempron 2600+ / 1Gb RAM / 256mb VRAM / 2x80Gb HDD. Teenage sons are really into BF2 (so am :) ). I also use this box for Dreamweaver/Fireworks/Acrobat usage.
[*]**Home Office:** I use this for email, report writing, research/surfing. Duron 750 / 384mb Ram / 64mb VRAM / 40Gb HDD / Feisty 7.04.
[*]**Current Server:** Made up out of spare parts. I once had it working fine with 6.06 server but having probs setting up SAMBA and stuff. I may retire this one or use it to muck about with. Feisty 7.04 server. Duron 650mhz, 80gb HDD, 64MB RAM.
[*]**Soon to be built gaming box** Will be using XP pro. This will likely have access to the web only for online gaming, MSN cha, Youtube, etc.  The only problem might be in saving shared music/video that can be access from anywhere on the LAN. (My sons want this box with just enough services going to maximize its gaming ability.)  I'm not sure if I can open up this box for gaming yet have it safely connected to the network. It will be using current technology.
[*]**Guest computers: **Visiting family and friends often need to connect laptops to internet.  Access to LAN isn't required other than for printing.
[/LIST]

**LAN Requirements:**
[LIST]
[*]I'd really like to be able to administer the LAN and individual PCs from one PC using a GUI tool for the most part. (I understand that I will have to do some work with the CLI.) Is Webmin a good tool?
[*]Users can access their files from any PC.
[*]POP Email should be accessable from any PC (We use Thunderbird.)
[*]Remote Access (VPN?): I really would like to be able to access the network remotely.  So would my kids who want access to tunes and stuff. I can use client software in some locations, in others I will have to use a web browser since I can't install software on a borrowed computer.  
[*]Printers: Should I setup a print server? I have a HP All in One, scanner, HP DJ 882C, Kodak EasyShare printer dock series 3 (the camera that uses the dock, EasyShare C743, is a piece of crap.  The printer is absolutely brilliant though. I highly recommend this 4x6 portable printer...it isn't an inkjet type.Note: I've only used it with XP)
[/LIST]

*I'm not a total noob but it does take a lot of time to learn and do everything with the CLI. And remembering what I did a month later...wow, what a task. *

With consideration of the above, I'm asking for three things:
[LIST=1]
[*]How you would setup the ideal LAN for my environment.
[*]The settings required for getting the LAN going. Can you give me examples of your /etc/#.conf files?
[*]How do I secure the system? (Firewall/standalone vs. shared antivirus/spyware?)
[/LIST]

I realize that I am asking for a lot, nonetheless, I really could use your help.

Thanks,
Ian.

---

### Post by raijinsetsu on 2007-09-14
If you want Windows compatibility, you'll have to use Samba for file-sharing and printer-sharing. Personally, I'd use their SWAT application to configure it. SWAT is a web-based configuration utility.

For remote configuration (from within the home)... I'd use SSH and X window redirection (this is one by default).

As for remote access, it all depends on what your ISP allows. Mine will not let me accept incoming HTTP, FTP, or SSH connections (even when using non-standard ports). If you can, you should set up a webserver on one machine and make virtual hosts under it to access the shares on the different computers.

It sounds like a really convoluted setup...

My suggestion:
Have 1 computer (Server) store all files and connect to all printers, as well as storing all password lists. Have it set up with Samba shares for your visiting Windows users, and NFS for your local linux boxes.
Have a webserver setup that has read-only permissions to access the "media" or shared files on the server. This is how my home network is setup, and I find it works very nicely.

---

### Post by Ian-on-the-Trent on 2007-09-14
Thanks for getting back to me raijinsetsu.

I suppose if I'm storing files in one central location then the individual machines really don't need access to each other...just the server. 

What I did not mention is that I store my business files on my office computer (not the central "server") and had set it up so an XP box could access it (for files I use with Windows apps).  I figured this was a more secure way to protect my biz files, I turn off this computer when it's not in use so it isn't exposed 24/7. * If I want to access these files remotely should I use a central server and spend my energy securing that?*

> Have a webserver setup that has read-only permissions to access the "media" or shared files on the server. This is how my home network is setup, and I find it works very nicely.

How would users be able to add "media" files if it was set up as read-only. Incidently, is "media" the standard location used by Ubuntu/Linux for multimedia files?

---

### Post by adl80l on 2007-09-14
> 6.Soon to be built gaming box Will be using XP pro. This will likely have access to the web only for online gaming, MSN cha, Youtube, etc. **The only problem might be in saving shared music/video that can be access from anywhere on the LAN**. (My sons want this box with just enough services going to maximize its gaming ability.) I'm not sure if I can open up this box for gaming yet have it safely connected to the network. It will be using current technology. 

Check out [www.orb.com](www.orb.com).  It might be an easy solution for that.

---

### Post by raijinsetsu on 2007-09-14
So... You want an enterprise class network inside your house?

First, if you want access to everyone's shared files from every computer, you either have to collect all the files all in one place(client/server configuration), or connect every computer to every other computer(mesh configuration). The latter is very messy and difficult to maintain, unless you happen to have access to Enterprise software. My suggestion: make the following file structure:
"/usr/local/shared_files"
"/usr/local/shared_files/SammysComp"
"/usr/local/shared_files/BobbysComp"
"/usr/local/shared_files/WorkComp"
etc.
and then make Samba shares for each of them, with proper permissions.

Second, if you are mixing Linux and Windows clients on the same network, you really need to use Samba for file and print sharing. A good GUI configuration tool is SWAT. NFS is preferred(at least by me) for linux file sharing. CUPs, I believe, automatically allows printer sharing if configured properly.

Third, remote-administration. I almost think you'd be well off to set up remote desktop on each of the clients. This is probably the easiest way to do graphical configurations on all the computers from one place.

Fourth, as for the Thunderbird setup: I don't know what you mean. Do you want to access your e-mail from every computer? Or do you want to access everyone's email from one computer?

---

### Post by Ian-on-the-Trent on 2007-09-14
> Fourth, as for the Thunderbird setup: I don't know what you mean. Do you want to access your e-mail from every computer? Or do you want to access everyone's email from one computer?

The email software my family uses is Thunderbird.  RIght now, the family email is accessed through the kitchen laptop while my biz related email is accessed using my office computer.  I was wondering if I could set up Thunderbird so all email is stored on one computer. Then, depending on how the user logs in, can access their email from what ever computer they are using.

Enterprise class network? Am I asking for a lot of my home LAN?

I want each persons files to remain their own.  I realize that I could access them as a root, however, in our family we respect each others space.

---

### Post by raijinsetsu on 2007-09-14
For the e-mail, you'd probably have to setup an e-mail relay. What this would do: a program on a server would fetch the e-mail for everyone in the house. Then, you could setup web-mail so that each person could access their e-mail from any computer.

It's not that you're really asking a lot from your LAN, but you may be asking a lot of yourself. Maintaining and configuring the complex setup you want is very difficult.

-=Overview=-
1) Every computer on your network will have a "Shared Folder" (accessible only by the owner, and administrator??), which is available through Samba on every other computer (except "guests"). This is fairly simple. If you do not wish to allow access to non-linux computers, use NFS instead.
2) E-mail is accessed by relay. A central computer fetches everyones e-mail, stores it locally, and allows access either via web-mail, or POP3. I've never done this, but there are lots of Howtos on this elsewhere. Web-mail would probably be ideal because you would not be storing scattered copies of everyones e-mail on each computer they used. Again, I've never done this, but there are lots of howtos.
-OR-
I believe you can configure Thunderbird to NOT delete the mail off of the e-mail server. Therefore, when someone accesses the e-mail from another computer (using thunderbird) they can access all the e-mail still on the server. The downside to this is: e-mail is now duplicated across many locations.
-OR-
If you're using Linux, you can have a users HOME directory on their computer exported via NFS. Then, on every other computer on the network, you can mount this directory for that user. The problem here is: UID,GID, and password concurrency across multiple computers: you'll need to use a mechanism like LDAP or some such.
3) Remote configuration can probably be most easily done through the use of remote desktops. VNC works on both Linux and Windows, so it is probably the most viable choice.
4) Remote access via the internet is not really suggested. But, if you really want it, you could use a regular HTTP server that has links to each of the shared folders.

---

### Post by armandh on 2007-09-14
I solved the issues with a NAS that also acts as a server
[http://70.237.130.123/FLASH_2_1_1/Apicturenlink.htm](http://70.237.130.123/FLASH_2_1_1/Apicturenlink.htm)

---

