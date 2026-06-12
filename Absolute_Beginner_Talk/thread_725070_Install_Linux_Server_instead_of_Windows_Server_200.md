---
title: "Install Linux Server instead of Windows Server 2003 -- good idea???"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-03-15
Our Church currently uses a Windows XP Professional PC as their Server.  They have less than 10 workstations and most are running XP Home.  The Church wants to upgrade their Server and two consultants have similarly proposed going with Windows Server 2003 Small Business Edition.

At the moment, the Church only uses the server as a File Store.  
They have a DSL connection that they utilize for getting onto the Internet.
Their email addresses are maintained by their ISP.
They share printers.


So, what are your ideas for a possible solution?
How about enhancements to their configuration?

Going forward, would XP Home be an issue?  How about those who in the future might want to remote into their workstations?

Would an Ubuntu Server provide Windows like VPN connections?  I currently utilize NXServer to remote into my home Ubuntu but that necessitates installing the NX Client.

Does Linux offer a "domain" like configuration similar to what Microsoft has with their Servers?

Thanks much.  I hope this generates a lot of useful ideas not only for me but for others too.

Carl

---

### Post by kujaabi on 2008-03-15
Our private school is thinking about going linux as well. The tech guy is very open but justifiably concerned about the difficulties. I will be interested to see responses to this posting as well.

---

### Post by davahmet on 2008-03-15
Often a consultant will recommend only what they know, so if the consultant knows only Windows, it becomes the answer for everything.

A better answer would be to match the solution to the need.  Linux does a wonderful job as a general purpose file server.  Really the only time I would recommend Windows 2003 is if you needed to run IIS or a Windows-dependent application that needed .Net.  Considering the cost differences in licensing costs, security and stability, Linux is usually the more obvious choice.

---

### Post by ByteJuggler on 2008-03-15
> **cwmoser said:**
> 
Would an Ubuntu Server provide Windows like VPN connections?  I currently utilize NXServer to remote into my home Ubuntu but that necessitates installing the NX Client.

Does Linux offer a "domain" like configuration similar to what Microsoft has with their Servers?


There's a package called "SAMBA" for Linux, which allow Linux to be a domain controller for a Windows network, as well as act as fileserver, print server etc.  

Re VPN: Linux supports several VPN servers, including PPTPD which Windows clients can connect with the built in Windows VPN client.  It can be a tad fiddly to set up the VPN server, but it's a lot easier these days that it used to be, and I/we can help with that.  Of course, once it's set up you don't tend to have to mess with it again.

As for remoting/NX:  IIRC you need Windows XP Professional to be able to remote desktop to a machine, so in that respect you'll have a problem, if you want to use remote desktop.  You can however use VNC or some other alternatives, to get onto the Windows PC's, but that will neccesitate the installation of VNC everywhere.  VNC also isn't always as fast as the RDP protocol particualrly over slow links, but it may suffice depending on your requirements.

Hope these comments help.

---

### Post by cwmoser on 2008-03-15
What would be PROS and CONS if I utilized Ubuntu workstation OS as the Server versus Ubuntu Server?

Carl

---

### Post by handydan918 on 2008-03-15
> **cwmoser said:**
> What would be PROS and CONS if I utilized Ubuntu workstation OS as the Server versus Ubuntu Server?

Carl

I would say the main "con" is not having someone around to dig you out when you get in over your head. If you can find a local Linux geek who knows this stuff well, I would consider  proposing a support contract between him and the church. 
The very fact that you are asking the questions that you are asking would seem to indicate you aren't quite ready to take on that task yourself.

---

### Post by Cyanic420 on 2008-03-15
If you are up to the challenge you can pretty much use Linux instead of Windows for the things you are considering. However be prepared for the additional learning curve you will encounter. 

rdesktop is a Linux client that duplicates terminal service client. 

You should be able to use a combination of LDAP, Kerberos and/or SAMBA to replace the Windows directory. XP home will not give you directory services, ie you will not be able to use domain logins.

---

### Post by Nythain on 2008-03-15
if you or someone in the church knows your way around ubuntu linux even a little bit, i would say go ubuntu over microsoft server... do you know how much money will be saved in that act alone.

setting up a simple file storage/server in ubuntu isnt to hard, its a matter of search for samba on google or these here forums... then setting a few things up.

advantages of a GUI *buntu over Ubuntu Server
easy to use apps for configuration of almost everything, and a familiar "windows" feel, and i use that term lightly in the fact that it has a GUI

disadvantages of GUI over Server
wasted resources spent on the gui itself instead of well, "serving" stuff :) thats about it... wich isnt even really a problem if the machine in question has a decent processor and amount of ram...

Now if you are familiar enough with ubuntu/linux, and arent afraid of teh command line, Server is the way to go... I personally had a Desktop install on my home server for the longest time untill i got familiar enough with the command line... then reformatted and installed Server instead...

no matter how you go though, as long as you or someone you know is proficient enough with linux, i would suggest it over windows... if you arent, then windows server 2003 is probably the better bet... everyone knows windows :)

---

### Post by cwmoser on 2008-03-15
> **Nythain said:**
> if you or someone in the church knows your way around ubuntu linux even a little bit, i would say go ubuntu over microsoft server... do you know how much money will be saved in that act alone.


Not sure how much Windows SBC 2003 costs.   How much is a 10 user license?

I know Ubuntu desktop pretty well and am familar with the command prompt.  I am though not familar with setting up "server functions".  I have installed Samba on my Ubuntu desktop along with NXServer.  Have not done anything with a mail server, apache web server, nor VPN server.

Carl

---

### Post by cwmoser on 2008-03-15
I found this on eBay that looks interesting -- anyone have any experience with it?

[http://cgi.ebay.com/REPLACE-MICROSOFT-SMALL-BUSINESS-SERVER-2003-2000-LINUX_W0QQitemZ350034741681QQihZ022QQcategoryZ41881QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/REPLACE-MICROSOFT-SMALL-BUSINESS-SERVER-2003-2000-LINUX_W0QQitemZ350034741681QQihZ022QQcategoryZ41881QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

Looks like this offer is a Linux OS with some easy to use configuration interfaces.

Do you think this might ease the setup of a Linux Server?

I'd hate to just submit to Microsoft and pay a lot of money if we didn't have to.  
Then again, I don't want a lot of stress and potential hit on my reputation for going with Linux.

Carl

---

### Post by kwacka on 2008-03-15
As the bulk of internet servers use linux there is clearly no great problem with your proposal of using Ubuntu as a server with XP Home clients.

Remote access is no problem, you mention NXServer - Nomachine also provide a free linux client. I just use xvncviewer  which I find perfectly adequate for my needs (storage, network connection in attic, e.g. can access & stream media using a 2002 Sharp Zaurus handheld).

The ebay link has a screenshot of the SME server - save yourself 9 dollars (plus postage) by downloading direct from the SME Server site - see documentation (a lot more than the ebay manual) at: [http://wiki.contribs.org/SME_Server:Documentation](http://wiki.contribs.org/SME_Server:Documentation)
and see if this fits your needs.

You will only need a Windows server if you intend to run .asp or .NET applications over the network,

(The link doesn't look right but does work - don't you just love graphic emoticons?  :( )

---

### Post by louieb on 2008-03-15
> **cwmoser said:**
> I found this on eBay that looks interesting -- 
[http://cgi.ebay.com/REPLACE-MICROSOFT-SMALL-BUSINESS-SERVER-2003-2000-LINUX_W0QQitemZ350034741681QQihZ022QQcategoryZ41881QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/REPLACE-MICROSOFT-SMALL-BUSINESS-SERVER-2003-2000-LINUX_W0QQitemZ350034741681QQihZ022QQcategoryZ41881QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

 
I went to [DistroWatch.com:]("http://distrowatch.com/")
BlackBelt Server Linux is not listed. 
Looking at the screen shots looks like it might be SME Server Linux. 
SME Server is based on CentOS which in turn is a re-branded version RED Hat (RHEL) Linux.
Heres the home page [http://www.smeserver.org/index.php](http://www.smeserver.org/index.php)
and the forum [http://forums.contribs.org/](http://forums.contribs.org/)

I've played with CentOS some (just installed it 2 days ago). Even thought it runs Gnome and I've used Ubuntu for 2 years. Its still been a bit of a learning curve. (RPM not deb packages) (yum not apt).  
:guitar:I think I'm going to stay with Ubuntu - bring on Hardy.

---

### Post by vexorian on 2008-03-15
In the case of servers, Linux and not "windows server" is the tested, common product.

---

### Post by General_Ts0 on 2008-03-15
Don't forget to think about this from an end-user standpoint.  Your taking the "pro-Linux" approach and your inner geek is trying to convince you to go this route.  What you risk losing sight of is those poor end-users that are stuck with this.  Philosophically, you've got lots of good reasons to go Linux, but you have to remember that you're never going to inventory the nuance needs of the end-users. Regardless of the technical implementation ends up being, you need to slowly phase this in.  At the point which this becomes more transparent, that's when you know you've done the right thing.  

I'm never a fan of "light switch" change overs [in this sort of context] and I don't think you're end-users would be neither.  They'll think you in the end for making it easy on them.

If you're lucky enough to have even semi savvy users and are still hell-bent on pushing Linux, go with a test environment and give it a 30 day trial run.

---

### Post by Wharf Rat on 2008-03-15
> **cwmoser said:**
> Our Church currently uses a Windows XP Professional PC as their Server.  They have less than 10 workstations and most are running XP Home.  The Church wants to upgrade their Server and two consultants have similarly proposed going with Windows Server 2003 Small Business Edition.
.....

So, what are your ideas for a possible solution?
How about enhancements to their configuration?

Going forward, would XP Home be an issue?  How about those who in the future might want to remote into their workstations?

Does Linux offer a "domain" like configuration similar to what Microsoft has with their Servers?

Thanks much.  I hope this generates a lot of useful ideas not only for me but for others too.

Carl



Carl,
It sounds like you have a budget and can afford a commercial product.  If so,  I highly recommend Nitix (just bought out by IBM).   Does all you ask plus:
VPN,  Shared mail, Shared contacts and Calendar.  Web, full security and BACKUPS.Restores work like they should - simple and solid.  Oh, and it acts like a NT Domain controller if needed. And, it you can  mimic an Exchange server to talk to Outlook. 

Anyone can maintain the system.

VPN Connections.
Yes.  Both for Windows, Mac and Linux clients.

Windows XP Home will work but can be a challenge for mapped drives in Samba.  
You might find users need to re-map a drive when they reboot the XP Home machine. XP Pro works better.
[www.nitix.com](www.nitix.com)
I have had one in service since Feb 2004. 24/7

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-16
ubuntu can do everything you said you need it too

---

### Post by cwmoser on 2008-03-16
I did some test exploration using my current Ubuntu desktop.  

I have Samba working and it works with my test Windows 2000 professional PC and my other Linux boxes.  I'll have to get an XP Home PC to test Samba.

I installed pptpd and set up my Ubuntu as a VPN Server.  Was able to VPN remotely and mount a network drive on the Server, and I could ping the Server.  BUT, I could not ping the other computers on my home network or any of my routers.  So, is the "Linux" VPN different from that we see with Server 2003 in that once the VPN is established you can access all the devices on the remote network?

Carl

---

### Post by handydan918 on 2008-03-16
It might not be a bad idea to grab an old tower and see if you can set it up to do what you want to do. If you can get it to porvide the functionality you're after, then you can duplicate it on the actual server box at the church.

---

### Post by ByteJuggler on 2008-03-17
> **cwmoser said:**
> I did some test exploration using my current Ubuntu desktop.  

I have Samba working and it works with my test Windows 2000 professional PC and my other Linux boxes.  I'll have to get an XP Home PC to test Samba.

I installed pptpd and set up my Ubuntu as a VPN Server.  Was able to VPN remotely and mount a network drive on the Server, and I could ping the Server.  BUT, I could not ping the other computers on my home network or any of my routers.  So, is the "Linux" VPN different from that we see with Server 2003 in that once the VPN is established you can access all the devices on the remote network?

Carl

You definitely can connect to other hosts on the VPN'ed network/ping them (or, it's possible to set it up so that it is.)  It's probably a configuration option somewhere, I don't offhand know exactly what but suffice it to say on Windows when you set up the connection, there's a "use default gateway" option somewhere which may be relevant.  It could also be something with the exact VPN server config you're using.   Have you installed any firewall software? (Firestarter etc.)

Aside: Some VPN clients (Cisco f.ex) prevent (by default)** local lan** access (e.g. vpn client lan) while the vpn is established.  If your client is linux, this however can be disabled by suitable changes to the routing table.

---

### Post by dwanders on 2008-03-17
Considering that you currently are no using any server (XP Pro PC), it would defiantly be worth your while to try using Linux for all your needs. You are not currently using a Domain, (so the XP home computer(s) are not logging into anything),nn AD's laying around. From your original posts you sound experienced enough to learn what you need to get it going or I bet these fourms could help you get it done.    

Don't get taken in by the FUD - even if you try Linux on new hardware and it does not work out for your needs (which I am betting it will) you could still go the MS route later if it just does not fit the bill. 

I only wish I did not have 250 computer's, 2 NT Domains and 1 AD - we are so buried in to MS products that convincing folks we could use something else would only be 50% of the battle - the rest would be actually getting all that useless stuff out of the network.

---

### Post by igknighted on 2008-03-17
Windows SBS comes with 5 CALs for a bit over $1000.  I think another 5 CALs will run you between 400 and 800, I can't seem to find the price anywhere.  So expect windows SBS to cost you at least $2000.  Versus free.

Now consider what time and money training will cost.  If you have people knowledgeable with windows server, then your costs will be low here.  If you are learning either way, windows and linux will likely be similar.

Also consider whether or  not you need windows SBS.  It does FAR more than you have outlined (for example, you get email and calendering through exchange server with SBS).  You could probably save money just going with windows server 2003/2008 and just using the file server & domain control features.

Finally, if you go with linux, do yourself a huge favor and use SME server.  The installer has a wizard that will walk you through the configuration, rather than spend hours messing with config files trying to get going.

I am going through a similar transition at work.  We have a Netware server that we are replacing, and are weighing the pros and cons of using linux and windows.  Due to the fact that a windows box is our current PDC (and by extension we have the CALs already), I think windows will win out.  And our IT staff knows it as well.  So don't go with linux just because it is appealing.  Carefully consider the options and make sure the solution is the best for all involved.

---

### Post by joechiang on 2008-03-18
i've build ldap from scratch, it is not hard, just google google google

best way though, is to load up vmware workstation on your computer 
(2gb ram recommended)
1. os  install ubuntu 6.06
and 
2. os install ubuntu 7.10

practices and test the ldap/samba installation on it.. 
best way to get you started

btw OP, it's kind of weird question to ask on ubuntu forum, coz linux can do everything almost and it's free :D

u might wanna post the same question at microsoft forums i am curious what the outcome would be..

---

### Post by cwmoser on 2008-03-18
Here is what I am going to model for this project:

  = use webmin ([http://localhost:10000](http://localhost:10000)) for the Servers administration interface
  = use Samba web interface ([http://localhost:901](http://localhost:901) for Samba
  = use the "Domain" feature in Samba to provide an Active Directory like logon
  = use pptpd VPN access
  = use NOMachine for admin login.

 
Still evaluating to provide an "enhanced" experience:
  = postfix for email
  = apache for a Church website
 

Still need advice on:
  - backup???
  - Antivirus???
  - Spam filter???


What Server hardware to purchase?  
I worked with a fellow consultant last night installing a Dell 2900 SBS Server -- that is a definite *overkill*.

Any ideas and advice is appreciated.

Thanks

Carl

---

### Post by hyper_ch on 2008-03-18
I just ask:

What does the server need to do?

---

### Post by njparton on 2008-03-18
> **cwmoser said:**
> What would be PROS and CONS if I utilized Ubuntu workstation OS as the Server versus Ubuntu Server?

Carl

I use the desktop edition for my home file server or "NAS" without any problems.

Now that I'm more confortable with the command line I'll probably go for the server edition when I next upgrade or re-install, but there aren't really any drawbacks to using the desktop edition.

---

### Post by dwanders on 2008-03-18
I think your over killin with that AD/Domain stuff - none of your XP Home computers will benefit from it and it will just overly complicate things. And the over complication will more than likely make you think Linux will not suite your needs. Keep things as simple as you can. 

I also think the pricing given a littler earlier was skewed:

Windows 2003 SMB Server with 5 cals = ~$700 - 800
Device CALS run about $40 - $50 each and I think you need to buy in packs of 5 (so if your going to go this route calculate out everything you need (and might need soon) and get it at once.  

I do think he was correct in that with SMB you will be paying for a bunch of stuff you do not intend to use or need. 

The Linux server should not need AV, but if you using Samba a lot and storing windows files on it, you should run clam av or something similar from time to time. 

Backup - standard Tar will do

Spam filter - I thought your ISP was hosting your Email - let them perform the bulk of that stuff - it will push the load & complexity of setting up off your server (anything the ISP can and will do - let them - especially if your already paying them for it).  If you just interested and want to learn how to do it your self 90% of the canned spam hardware solutions use some form of Spam Assassin or other Linux born spam package. 

Email - again, I thought you said the ISP was hosting this

While it will probably cause information overload - the other fella was also correct in that you should have this same post in a Windows centric area. Don't get me wrong, I truly believe with very little effort you could cover all you needs with one Linux server that you will set up and forget for the next 5 - 8 years (with intermittent log cleaning). 

Hope it all works out for you.

---

### Post by handydan918 on 2008-03-18
>  Don't get me wrong, I truly believe with very little effort you could cover all you needs with one Linux server that you will set up and forget for the next 5 - 8 years (with intermittent log cleaning).

Aforementioned logcleaning can and should be automated via cron on a server, especially if /var is not given it's own partition. 
As to 5-8 years, if you want that kind of life out of a system, Debian stable might be better. Their development model allows for rolling upgrades, unlike Ubuntu. That means zero downtime except for the rare kernel upgrade.

---

### Post by cwmoser on 2008-03-18
Has there ever been a project to create a "Best Practice" example for setting up an alternative to Server 2003?  Maybe a blog?  If not, maybe we can round up some interested parties to organize and develop detailed documention to do this.

Carl

---

### Post by halitech on 2008-03-18
as far as the backup, what about Remastersys? Will allow you to just back up data or a complete backup you can use to restore your system.

---

### Post by dwanders on 2008-03-18
I have never seen a "Best Practices" guide - I think these are mainly unavailable  because you would need one for each distro that does something differently than the other. There is a Linux Administrators Guide that is very good at the underbelly of these differing distros, but even it gets overly large because it tries to show how do such and such in RedHat, Ubuntu, Suse etc... 

I think the best thing you can do is analyze your situation (throughly). Determine what is going to be your Outside services (e.g. hosted by your ISP), and try push off (or utilize) this as much as possible - use every thing your are probably already paying for - (so you don't need to get into anything short of a FW & connection). Next determine all your required inside services - things you want to (and can) provide as services to your users dependent on the Host OS of your users (e.g. XP Home has many limitations to use server services - you would probably experience less limitations when it comes to Linux if you use only TCP/IP based stuff). 

Then once you have all your outside services & internal services figured out - you should easily be able to determine what system will suite your needs best. From there, once you have determined you base OS - you can probably find some pretty good guides (or kinda best practices for your chosen distro)  to accomplish everything you want to do. Based how killer Ubuntu has been and the support system it has in place - I would be surprised if the Long Term supported distro would not suite your needs. It is not bleeding edge - but I don't know any administrator that wants that for their base systems anyway.    

In the end things can get complicated if you let them - keep everything on a short leash and keep it simple.

---

### Post by dwanders on 2008-03-18
This looks very promising to help guide you on your decision (cant beat O'reilly for very good tech books & Ubuntu comes from that Debian Pool) have not read it all but I intend to:

[http://www.oreilly.com/catalog/debian/chapter/book/ch10_01.html](http://www.oreilly.com/catalog/debian/chapter/book/ch10_01.html)

---

### Post by dwanders on 2008-03-18
While much of that info is still relevant - I would say it is pretty outdated. It looks like it only covers up to NT based computers. Sorry - should have read it all first! ;P

---

### Post by cwmoser on 2008-03-18
I appreciate all the suggestions you folks have given.  I think I will concentrate on this primarily as a server to do file and printer sharing.  To summerize, this is the software I think I will concentrate on:

-  Ubuntu Server
- Webmin administrative interface
- pptpd for VPN access
- NXServer for remote admin access
- Samba for File and printer sharing - maybe even as a domain controller
- UPS - apcupsd software
- Backup/Restore - backuppc software using external USB hard drives 
- Cups admin for printer maintenance
- Apache2 for a basic website

With these I can have a web interface for most admin functions.

No functionality for email, virus, or spam.

What do you guys think?  Got suggestions?

Carl

---

### Post by dwanders on 2008-03-18
I think/bet that will work out nicely. I might stick to LTS for the Ubuntu (not the flashiest - but probably more stable). With all the money you save from not using Windows - I found a very slick USB unit called DRobo that looks very promising (as a data store for your backups) do a Google if your interested.

As for each - my personal experience :
Ubuntu Server <- Use every day - forget about it often - I have some print station Kiosk based on Ubuntu that have been running unattended for well over a year - when I go back out to them I have to try and remember how I set them up - so document things well as you go along. I have a single server I have been using as our Intranet Web Server (Apache)  for well over three years with little more than a reboot from upgrades) I also have a Redhat ES3 I have been running for over 5 years now with Domino Email on it - as for the OS I have had to do squat with it short of cleaning the server up from time to time for disk space. I also use Ubuntu Desktop daily for my workstation at work, I set up my Kids with each their own Ubuntu Desktops, and my Home computer & Laptop are Ubuntu its all I run - my Wife is still using Windows, refuses to change. 

Webmin administrative interface <- never really used/needed kind of a Telnet/SSH kind guy
pptpd for VPN access <- never really used/needed (want to try SSH but have not got around to it - chasing to many Window's servers to have the time) 

NXServer for remote admin access <- never really used/needed (been wanting too try it though)

Samba for File and printer sharing - <- Use every day - foget about it often we have 1 Redhat ES4 that has been running SMB to exchange files with a windows server for well over three years now, and since setting it up, I have never messed with it. Keeps chug-in along. The other RedHat server with my email on it, has been exchanging backups with a Windows 2000 Workstation (yes workstation to avoid licensing nightmares) computer as long as its been alive so the Windows computer could back it up (kinda backward I know, but I cannot get out from under the FUD with my supervisors - they are very afraid of what they don't understand and Windows is all they understand). 

UPS - apcupsd software <- never really used/needed (probably should)

Backup/Restore - backuppc <- experimented with this very sweet, cant convince my supervisors to leave crappy NT Backup (my nightmarish structure already in place)
 
Cups admin for printer maintenance <- Use every day - forget about it often CUPS that is, never really used the Web admin for much. 

Apache2 for a basic website <- Use every day - forget about it often - it is my Intranet, use it for hosting many internal things, would like to use it more. trying to get my supervisors to abandon MS Access 2.0 runtime for a PHP/MySQL setup but it is slow going.

NOTE: This stuff has been around for a long time, and is only improving every day - however - since I work for a Corporation, all the big Linux servers we have (the RedHat ES servers) are under maintenance contracts. The hardware and OS systems are under support. So for my Redhat server(s) we call HP if we have any OS problems and their Unix gurus help us out. To my recollection, we have called them once during its initial setup because we had problems getting the RAID drivers on the HP Proliant server to work correctly with the SCSI controlled DAT drive - we have not talked to them since about the OS related problems but never underestimate that comfort of knowing we could call them if we need to is always there. I just don't want you to think I am hanging out there with no support praising this stuff with just my skill level! And I would use Ubuntu for all these servers (even tested it just for proof of concept) but the applications I need (Domino for Email and my MRP system) are currently only supported on RedHat [I expect that change as Ubuntu grows!]  

Whew pretty long winded! But I feel I must do all I can to get people out of this FUD and into using something really useful (I have an equivilence Linux to Thomas the train OK yes I went overboard, must be time to go home!) -  I truly hope every thing works out for you and your Linux experience is a rewarding one.

---

### Post by cwmoser on 2008-03-22
I got my Ubuntu Server working along with ssh, Apache, Samba, Webadmin, and Samba SWAT.  I got Postfix working partially and it will send out email.  I don't have a email presence on the Internet to fully test Postfix -- any ideas?

I've got these clients working:  Ubuntu, Windows 2000, and Windows XP.  Ubuntu Server seems to work very fast.  Found out that XP needs a registry tweak.  Have not got the connection to the Domain working -- still the clients need to have local accounts with same username and password as on the server.

Started looking into BackupPC for backup.  Confused.  I need a quick start tutorial.

Going to look into moving my printer to the Ubuntu server for shared printer testing.

Comments and suggestions on this project are encouraged.

Carl

---

### Post by saminthemiddle on 2008-03-22
Don't forget that RHEL, SLES, and Ubuntu all make a business supporting their products commercially. I just looked it up and 9x5 support for a server is $750 for a year. 24x7 is $2750, but I doubt a church needs 24x7 crisis support.

Anyway, just saying that free plus $750/yr is a lot cheaper than the windows alternative.

---

### Post by cwmoser on 2008-04-05
Ok, this is the status of the project to develop a Linux server for our Church.

The test server has this functionality:

- File and printer sharing (Samba, Cups)

- Domain (Samba)
  Got this working so that workstation users have to enter logon credentials.  
  Does not seem as nice as Windows, but it works.

- Remote access:  VPN (pptpd), VNC, and ssh (sshd)
  Windows workstation PC's can be remotely administrated using Remote Desktop or VNC.
  Any Linux workstations I can talk them into can have NXServer, or FreeNX.

- Full email capability:  (PostFix)  This is nice!!

- Website (Apache)
  Set up my first website and email functionality along with the associated MX, A, and C records.
  This was something I always wanted to learn.

- Web Administration:  WebAdmin, Samba, Cups

- Backup -- BackupPC -- for some reason, I have not figured this one out.


What am I missing?  Comments?

Thanks

Carl

---

### Post by ByteJuggler on 2008-04-05
So you got the VPN working properly then?  (Remote clients accessing machines other than the VPN server on the VPN machines network?)  That's good.  Fixing that involves I believe enabling/adding routing/packet forwarding in the kernel.  I don't know the exact commands needed, but you can use Firestarter to enable this I believe.  However, Firestarter can cause it's own set of oddities in such a which is why I've not suggested it yet.  How/What exactly did you do to get the VPN client accessing the VPN'ed LAN?  Very glad it seems to be working out for you BTW.  (I actually am wondering about one other thing:  Once set up, joining and authenticating against the Samba-run domain [from a Windows clients] perspective is the same as against a Windows domain controller, so I'm curious what you referred to when you say it's not as nice?  Are you referring to the configuration of the server?  )

BTW, the knowledge you gained, would I think be very useful to put into a how-to somewhere... maybe on the Ubuntu community documentation site.  I'm sure there'll be others interested in doing a similar setup, so you documenting your experience may prove to be a *very* popular reference, even if there are similar-ish pages out there already!

---

