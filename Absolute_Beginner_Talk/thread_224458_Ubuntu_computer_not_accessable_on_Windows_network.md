---
title: "Ubuntu computer not accessable on Windows network"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by drworm01 on 2006-07-28
I just installed Ubuntu on an extra computer in my house and want to connect it to my network. I have three computers all told-2 with XP, 1 with Ubuntu-all connected to the internet through an ethernet router. This is not a wireless network.
Ubuntu can access the shared files on the Windows computers but the Windows computers don't show Ubuntu as part of the network. They recognize it as being another computer in the "Workgroup," but when I double-click on the Ubuntu computer's icon in the Workgroup window, I get a prompt for a username and password. The username/password I use to log into Ubunutu (the only un/pw combo on that computer) doesn't work.
I've installed Samba via Synaptic though I don't know if I've got it operating correctly or, really, at all.
I'd like to use the Ubunuto computer as a central music server for the house so I need to be able to read files from it remotely. What am I doing wrong and what do I still need to do?
Thank you for any help.

---

### Post by dtfinch on 2006-07-28
If using just the administration tool that comes with Ubuntu, I don't see how to add users or set permissions. I haven't really tried to use the tool much, but it looks like a victim of oversimplification.

On our servers at work I use "smbpasswd -a username" as root to add a user to samba's user list and set their password. Then I add their username to the "valid users=" line under the share in the samba config (/etc/samba/smb.conf). I generally use a web based tool called SWAT for all samba administration tasks except for managing users. It's very comprehensive and self documenting.

---

### Post by jonandrews on 2006-07-31
Hi. I am in exactly the same position as you! Below are my notes from my battle so far:

I started with a fresh Ubuntu install, connected to a working Windows network containing a ADSL Modem / router set to supply IP addresses (permanent lease):

Ubuntu can immediately see & access all the connected Windows PC's  via:
Places > Network Servers > Windows network > mshome > etc…..

From Ubuntu, files can be transferred both in & out of the pre-existing shared Windows folders. No changes to Windows or the firewalls were needed. 

(I originally thought that Sygate firewall worked immediately, and Zone Alarm didn't - but now they both allow traffic ok.  Mmm….)

However, WinPC's cannot see the Ubu PC at all.
	
I spent a day trying to resolve this - and failed. The key seems to be in the use of Samba , but I found the documentation  too difficult to follow at this stage, due to my lack of Linux experience.  I made some apparent progress, but of course I may have made errors that would screw thing up later.

I got the Ubuntu PC visible (but not accessible) to WinPCs as follows:

System > Admin > Shared Folders.  Got message that Sharing Services are not Installed.

It then asked if I wanted to Install Samba to achieve sharing with Windows.

Said yes - It downloaded & installed packages (Samba?)

Then went System > Admin > Shared Folders  again, and selected 'Allow Browsing Folders'

The Ubuntu PC then became visible in MSHome on the WinPCS

Also, when rt-clicking on folder in Ubu, a 'Sharing' option became available.

However - when trying to access the Ubu machine from WinPCs, a 'User & Password' screen appears, and I cannot get past it with the Ubuntu user codes I established when setting up the UbuPC. It transpires that there are more config setting required in Ubu, but I failed to make any progress with them.  Bundled with Samba is a GUI called SWAT, which I think would be very helpful, but I couldn't figure out how to access it !

I will keep on at it as time permits, and post updates.

---

### Post by jonandrews on 2006-07-31
In the main section of the forum, I have just found this guide
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

It looks like it should help

---

### Post by jonandrews on 2006-07-31
I have done it! I can now see & access the Ubuntu PC from all the Windows XP  PC's on my network. Files transfer both ways between the shared folders of the 2 systems.

I used the guide I mentioned in my previous post (Thank you very much, stormbringer!) and just slogged through it.

I will mention a couple of things.(remember, I'm a newbee to Linux!)

In Terminal, when it asked for a password, I thought it was not accepting my keystrokes, and this stopped me dead. I later found that sudo does not acknowledge the password keypresses at all, but it does action them. After that, I was fine with Terminal.

Finally, stormbringer includes a section on changes that have to be made to your Windows PC's. I made no changes at all, left the WINS settings at the default, and am able to do everything I want, which is basically just file transfers.

I hope this is helpful. Just ask if you would like any more detail.

---

### Post by stig on 2006-08-03
> **jonandrews said:**
> I have done it! I can now see & access the Ubuntu PC from all the Windows XP  PC's on my network. Files transfer both ways between the shared folders of the 2 systems.

Hi,
Are you using DHCP or static IP? The Stormbringer guide seems to be for static only.

---

### Post by jonandrews on 2006-08-04
In my network the individual PC's are all set to obtain their IP address automatically. The addresses are provided by my Belkin ADSL modem / router. I know that stombringers guide talks about the need for static ip's, but I also knew from previous experience that when IP's are issued by the various routers I have owned, there is the additional concept within (all? the) routers of a 'lease period' for an ip address. On checking my router control panel, I found long ago that the 'lease period' could be adjusted from (say) 1 hour to 'permanent'. As I recall, the default in the Belkin as 'Permanent'. So, I reasoned that if everytime a one of my PC's was turned on, it was always issued with the same IP, then this ammounted to a static ip 'by other means'. It certainly worked fine with stormbringer's setup. I've set up 2 other PC's since my original post with his method, and everything is fully visible & working fine. 
Hope this is helpful.

---

### Post by stig on 2006-08-07
> **jonandrews said:**
> In my network the individual PC's are all set to obtain their IP address automatically. The addresses are provided by my Belkin ADSL modem / router. I know that stombringers guide talks about the need for static ip's, but I also knew from previous experience that when IP's are issued by the various routers I have owned, there is the additional concept within (all? the) routers of a 'lease period' for an ip address. On checking my router control panel, I found long ago that the 'lease period' could be adjusted from (say) 1 hour to 'permanent'. As I recall, the default in the Belkin as 'Permanent'. So, I reasoned that if everytime a one of my PC's was turned on, it was always issued with the same IP, then this ammounted to a static ip 'by other means'. It certainly worked fine with stormbringer's setup. I've set up 2 other PC's since my original post with his method, and everything is fully visible & working fine. 
Hope this is helpful.

Yes, thanks for the reply, your message does help by confirming my own conclusions.

I'm using a Speedtouch 510 router but it was supplied by my ISP as part of the broadband package and I can't alter the configuration - they have a password and want users to do everything through them, it seems. The router must be on the same as yours was originally, giving out different IP addresses.

Oh well, I emailed the ISP's tech support for help, waited about 30 hours and got a reply saying that I hadn't given them my hostname. In fact, the hostname was in the first line of my message - so if they can't understand that, I wonder what good their help might be.

I'm glad to hear your network is running OK. At least my ubuntu-to-ubuntu and ubuntu-to-windows sharing is OK - it's just the win-to-ubuntu that fails. But then I hope to give up windows soon.

---

### Post by jonandrews on 2006-08-07
Hi. I had a Speedtouch 510 a while back, & from memory, although it was possible to vary the lease times (if you can get to it's control panel!), I don't think it had a 'permanent' option anyway. As a matter of interest, which ISP are you with ?

---

### Post by stig on 2006-08-08
> **jonandrews said:**
> Hi. I had a Speedtouch 510 a while back, & from memory, although it was possible to vary the lease times (if you can get to it's control panel!), I don't think it had a 'permanent' option anyway. As a matter of interest, which ISP are you with ?

Demon Internet, on a "Business Broadband" package.

I have had a very brief reply from their technical support saying: "You only have 1 static IP address [here they give the router's address]. May we request you to assign the IP address's manually in the Local area connection and try."

I haven't tried this because I assumed that it would not over-ride the router's DHCP configuration. But then I don't know much about it, so perhaps I should give them the benfit of the doubt and try it.

For the record, I've been with Demon for a long time. They were excellent back in the days before Scottish Power/Thus took the company over. Since then, the the internet service provision has been good, and so has the tech support (usually!), but customer service is abysmal. They are well-known for claiming that you owe them money (when you don't) and getting debt collectors to harass you! (They had the collectors chase us for seven pounds which they claimed we owed them).

---

### Post by jonandrews on 2007-11-21
I've finally put my simple guide to integrating Ubuntu PC's into a wired Windows home network 

onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

