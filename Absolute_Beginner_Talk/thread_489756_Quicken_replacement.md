---
title: "Quicken replacement"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by greg_g on 2007-07-01
So, long story short, I want to help my dad convert to Ubuntu.  The main, and practically only, show stopper is Quicken.  I have yet to find a real Quicken replacement.  Sure, GnuCash is fairly powerful, but it doesn't do half of what my dad uses quicken to do.

These things include (but are not limited to): Printing tax forms so he can just sign and mail.  Download date from accounts DIRECTLY into the software (no saving file, importing).  And I'm sure more.

Is there really no alternative for my father?

It is the age-old problem of looking for a new computer, not wanting Vista, but I can't recommend Ubuntu if he can't use Quicken or a real alternative.

Any input would be greatly appreciated, thanks guys,

greg

---

### Post by wolfen69 on 2007-07-01
install virtualbox, do a minimal xp install, and run quicken from there.

---

### Post by greg_g on 2007-07-01
Yeah, I thought of that as an option, it just seemed kind of dirty.  

But that might be the solution.

Any other ideas (I know, I'm fishing here)?

---

### Post by HotShotDJ on 2007-07-01
> **greg_g said:**
> Download date from accounts DIRECTLY into the software (no saving file, importing). 
From the [KMyMoney2]("http://kmymoney2.sourceforge.net/index-home.html") web page:
> Once you have an account set up with online banking, go to the ledger for that account. Then from the "Account/Category" menu, choose "Online update using OFX...". This will connect to you bank, and download a statement for the last 60 days.
I'd be VERY surprised if this feature was not also available in GnuCash.  As far as Taxes, there are no native Linux solutions that I'm aware of.  However, TaxCut has an online version that can be used from you web browser -- I'm sure others do as well.

---

### Post by Eggnog on 2007-07-01
I understand your dad's plight.  Quicken is pretty much the main reason I cannot jump to Ubuntu completely.  I can't find anything that replaces it.  GNUCash, MoneyDance, they are not quite the same as Quicken and he may not be happy with them either.

I installed VMware Server with XP pretty much just for Quicken and the odd Win XP app or two.  It works fine for that.  Quicken does not seem to play well under Wine or Crossover.

---

### Post by totheresq001 on 2007-07-01
Quicken and Quckbooks also run well under virtualbox

---

### Post by Eggnog on 2007-07-01
Speaking of Virtualbox, does it share files and folders between the host and the virtual machine?  I can't seem to figure out how to do that with the free VMware Server.  If Virtualbox does this, is it easy to configure?  I'll make a VB machine if it does this.

Edit:  Sorry about hijacking the thread.  I'm thinking of Quicken, though, and sharing the backup and data files for storage and whatnot.

---

### Post by greg_g on 2007-07-01
Eggnog,

I was wondering that myself.  I am going to go test it with my VirtualBox installation (I don't have Quicken though, just doing a proof of concept with shared files).  My assumption is no, it won't work.


greg

---

### Post by greg_g on 2007-07-01
I was wrong:

[http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/](http://www.blog.arun-prabha.com/2007/05/21/configuring-virtualbox-for-sharing-and-mouse-control/)



PS.One thing, you have to do the "Install Guest Additions" for it to work, it wasn't very clear on that page

---

### Post by Eggnog on 2007-07-01
This is getting better and better.  I may have to ditch the XP machine on the free VMware server, unless there's a way to do it on the free VMware. and go with Virtualbox.  I have them both installed but I've just been using VMware.

---

### Post by DonLorenzo on 2007-09-29
I converted to Ubuntu 7.04 from Win2K when I acquired a new desktop machine in July 2007. Here's my story:

On Win2K I have 2 applications that are Windows only for which I need suitable Linux native replacements: Quicken; Keynote. Alas, there appears to be no suitable replacements for either of these applications that is hosted natively on Linux.

In summary:

[LIST]
[*]Run Win2K in a VMWare-server virtual machine.
[*]By hard policy, I run nothing but these 2 applications in the virtual machine. Nothing! No exceptions.
[*]Use Samba to provide Linux native file space in your home directory. Place the application specific data files in these directories so that the data are backed up with routine home directory backups.
[/LIST]
Some Details:
[LIST]
[*]VMWare-server is free. You have to ask VMWare for a license key. They willingly gave me a key.

[*]Create a virtual machine using VMWare-server's builtin tools. 384MB is plenty of memory for the virtual machine for these 2 applications. 4.5GB of disk is plenty of disk space for Windows and the 2 applications.

[*]It seems to work best for me to run the virtual machine in its own desktop with the "quickswitch" resolution at near full screen size. Depending on your screen size, you may want to use other ways of visualizing the results.

[*]As distributed, Ubuntu 7.04 has a dependency between Samba and VMWare-server's start order in initualization. There is at least one discussion in these forums on the subject. My solution is to run a script before starting the VMWare-server console; the script stops both Samba and VMWare-server, then restarts them with Samba being started first.

[*]When building the Win2K virtual machine, just pretend you are installing it on a real physical machine. Remember to install IE6 (IE5 is the default). IE6 gets updates; I'm not sure IE5 does. Install Service Pack 4. Install VMWare tools from VMWare console assist; the assist mounts an .iso provided in VMWare-server as a CD; the VMWare Tools makes operating your virtual machine a lot easier. After installing VMWare Tools, use ControlPanel->VMWareTools to set "time sync to host". Use ControlPanel->Display to set the screen resolution you prefer; this is truly rich! Pick up all the Windows security updates. Install AVG anti-virus. Do not install ZoneAlarm (I had used AVG, Zonealarm on my old physical machine. There is some conflict (I didn't diagnose it) between VMWare, DHCP, Zonealarm). Do not install anything else; try not to make the Windows virtual machine convenient to use for any other purpose.

[*]A note on security: I chose not to install any form of software firewall in the VM because in my environment there is NAT at the DSL router entering my LAN. With NAT networking used by VMWare to connect the virtual machine to the WAN there is 2 levels of NAT. I figure that the virtual machine is reasonably safe. I run AVG update then scan at every startup. --- Install Quicken with the physical network disconnected. (yes, I'm paranoid) Then take a VMWare snapshot of the virtual machine. This is your restore point should the VM become corrupt or become infected with malware. Make Quicken retrieve his own updates after you take the VM snapshot.

[*]Testing. Before commiting to use VMWare in "production" I tested carefully to see that I could go back, if necessary to a natively hosted Win2K. I did this by running Quicken in the VM, modifying the data via normal operations, then copying the files back to the Windows native machine to see if they were still usable by Quicken. ... they were.

[*]On Backups. The VM itself is modified each time you run windows: temp files; swap; logs; Windows Update. At 2G each for the virtual disk files, this makes for some big backup sets. Consider keeping the VM itself in /var/,,,/whatever and taking a single backup of this data. This keeps your home directory backup set to whatever you've done to data, not the VM itself. Makes for much smaller backup sets for me.
[/LIST]
This has worked out well thus far. Maybe this will be helpful to you too.

---

