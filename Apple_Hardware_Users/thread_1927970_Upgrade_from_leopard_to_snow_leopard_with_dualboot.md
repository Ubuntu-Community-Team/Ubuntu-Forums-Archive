---
title: "Upgrade from leopard to snow leopard with dualboot refit"
date: 2012-02-19
forum: Apple Hardware Users
---

### Post by stesosaso on 2012-02-19
Hi,

My problem is as following :

[LIST=1]
[*]Mac book pro running leopard and Ubuntu on dualboot using refit
[*]I bought snow leopard DVD on apple store
[*]Launched the new DVD in order to install snow leopard
[/LIST]
The I got an error saying that I cannot install Snow Leopard because the HDD is not bootable...


What's wrong?
For the moment being I am saving all my data.


An other question would be : If I have to reformat all the HDD, or if the actual leopard install has to be deleted totally in order to upgrade, how can I save software that I have bought in the past, but I am really not sure to find it's SN in my old mails (the software is Little Snitch)?


Thanks in advance for your help,
WBR
Stéphane


PS: Please forgive me my bad English as it is not my mother language, I am French.

---

### Post by stesosaso on 2012-02-19
Is there any possibility that refit could be the cause of the message issued by snow leopard installation DVD?

Does any possibility exist in order to remove temporary refit and let Snow Leopard installation disk "think" that there is just an OS X partition with some other partitions on the same disk ?
If yes, what is the procedure to get it done this way, and is it possible to reactivate refit afterwords?

What I want to do is upgrade Leopard to Snow Leopard and then to Lion (without loosing the installed software etc...), reinstall an Ubuntu 10.04 LTS as second OS in order to virtualise Ubuntu in OSX with Vmware Fusion (as I have it right now, but with older versions).

What's the gain in doing that? I can have an Apache Web server on my machine and run it as it would be some where on the net. From OS X, with a browser, I can enter any web address like [http://www.myserver.com](http://www.myserver.com) (if this address is set like that in the hosts) and get in touch with my Apache server via internal IP redirection (hosts entry) by letting Ubuntu run via Fusion.
In this way I have a distanced Web server locally on my machine and I do not need any internet connection for that.
The physical install of Ubuntu onto a partition is justified by the possibility to boot directly with Ubuntu and get it on an network as any other web server in a domain to demonstrate the result in a real configured environment.

Thank for your help and advise
WBR
Stéphane

---

### Post by stesosaso on 2012-02-21
-UP-

133 people red this topic an no one has even an idea?

---

### Post by guidop on 2012-02-23
I only have suggestions of things to try:

If you can still boot into the rEFIt startup screen:

At the rEFIt prompt, start the partitioning tool, and if the tables are not synchronized, sync the GPT andMBR partition tables.


If you can still boot into OSX:

Start Disk Utility and Verify/Repair Disk and Disk Permissions.

If you have a free external drive, use Disk Utility to partition it for OSX, then use a program like Carbon Copy Cloner to make a bootable copy of your installation.  
Check that the copy will boot.  This will help later, in case something goes wrong, you should be able to restore the original Leopard install and all programs.


Disconnect the backup drive, and boot back into OSX on the main drive.

Insert the Snow Leopard Disk and run the installer.  Does it allow you to upgrade now?

I did this upgrade from Leopard to Snow Leopard on my Triple-boot Macbook Pro 2,2, and everything still worked.
(I had to install Rosetta to make my legacy PowerPC apps run.)

Your results may vary.

---

### Post by guidop on 2012-02-24
Make sure your OSX backup REALLY works.
Back up what you need from your Ubuntu install, too.
Clonezilla?  or save your home directory and installed packages list.
[INDENT]To save list: # dpkg --get-selections > /backup/installed-software.log
To restore:  # dpkg --set-selections < /backup/installed-software.log
# dselect
choose i to install.[/INDENT]


Boot from the Snow Leopard DVD.

Run Disk Utility and make two partitions with hybrid MBR to allow dual-booting. First for OSX, second for Ubuntu.  
(Or you could make 1 partition and use later BootCamp to make the Ubuntu partition after you restore OSX.) 

Install Snow Leopard on the first partition.  
Use the Apple Migration Assistant with the backup you made to migrate all your applications and user settings.  
You may also have to install rEFIt.
Make sure all your applications work.

[If some of your applications lost their keys and won't work anymore, you can restore your Leopard install from the backup, and try the upgrade method described in the previous post again.]


Re-install Ubuntu on the second partition.  
You can use the installer partitioning tool to divide the second partition if you want separate /swap and /home partitions.  
Make sure you install GRUB to the /root partition, not the MBR.  
You may have use the rEFIt partitioning tool to sync the GPT and MBR.


I did something like this when on the MacBook Pro when I installed a larger hard drive and upgraded from Tiger to Leopard.  It took nearly all day, including updates.

Again, your results may vary.


I hope something works for you, without you losing anything.  Best of luck.


Once you get Snow Leopard working, the upgrade to Lion should work.
Make sure you look up how to burn a Lion install disk, and burn one before you upgrade, so you can repeat the process in the future without downloading the image again.

---

### Post by stesosaso on 2012-02-27
Many thanks [guidop]("http://ubuntuforums.org/member.php?u=32348") I will try your first recommendations and if nothing works try a clean install.

I can still boot to any of my OS'es (Leopard or Ubuntu) with refit, have realy no problem with my install, but just when I want to upgrade Leopard by inserting the new Snow Leopard DVD, then it hangs because of impossibility to install Snow due to message from Snow installation procedure saying that it is impossible to Boot on my HDD...

I will find a HDD where I can backup all My Leopard. Ubuntu data's are already saved and I do not have any specific software on Linux just different Web sites (globally HTML and Data stuff).

WBR,
Stéphane

---

