---
title: "Instaling with WinXP installed as well"
date: 2010-12-11
forum: Apple Hardware Users
---

### Post by Xadrieth on 2010-12-11
Hey there.

I have a MacBook (mid 2007, with Core 2 Duo), and I'm looking to install a copy of Ubuntu on it.  The thing is though that I already have a copy of Windows XP on this.

I do a lot of programming, and lately have gotten into Linux programming, and I don't want to rely on my mom's old Toshiba with only gets 2 seconds of battery life (not joking), yet has Ubuntu already on there.

So are there any ways I could go around to installing a copy of Ubuntu on this thing, so that I have three OSes.  I don't want to disturb any of my partitions, or have to re-install Windows (which is a pain).

Right now I'm using Boot Camp 1.3 Beta to boot Dual Boot, and have OS X 10.4.9 installed.  Is it possible to partition part of my windows partition, and then then upon booting, go through Boot Camp, select to boot to Windows, then have the Ubuntu boot screen pop up, and then ask me what OS I want to use?

Thanks for your time, or any help.

---

### Post by chicoharv on 2010-12-11
Make an ISO copy of the Ubuntu you want to install, then click install and when it gets to the partion let it show you what it is planning to do. You can always back out b4 you click next. Not sure about boot camp as it may come up with all your OS's listed at startup. At that point you scroll to the OS you want. By the way my laptop runs twicw as long on Ubuntu as my windows XP or vista as less resources are being used. Depending how big your hard drive is you should not have any problems. You could also instal inside of window at a cost of speed and power drain.

---

### Post by Xadrieth on 2010-12-12
Thanks, I'll try that.

As for the power drain, I just think that the battery in my mom's old Toshiba is pretty faulty.  Seeing as then when I had Version 10.x of Ubuntu installed on it, I got a "Battery Recall," notice.  Never got time to replace the battery.

---

### Post by JohnMcB on 2010-12-12
Maybe this will help.I have got triple boot on iMAC,OSX,UBuntu 10.04,Windows XP Pro
Hardware Intel Core 2 Duo,500GB HDD,2GB ram,24" screen,late 2007 model.
OSX and XP installed on bootcamp.Both systems used and to much data to be bothered with new install, but wanted to install Ubuntu as well. This is what worked for me.
Download and install rEFIT, in OSX.
Use Disk Utility,Finder>Go>Utilities>Disk Utility.
Select internal HDD,not partitions but Drive.
Select partition tab.
This should show graphic,select OSX partition and resize to allow space for UBuntu,I used 50GB,but use whatever suits.
Select 'new' empty space or click on '+' and change name to Ubuntu if required.Format as empty space.
Reboot into Windows and Edit boot ini. file to boot from Disk 4,it should presently be 3. Windows must be on last partition.Don't know why but if not will not boot.
Reboot into OSX-May have to do power button shutdown to get out of Windows as it can't find disk 4 at moment.Reformat Ubuntu  partition as MS-DOS FAT
Insert Ubuntu CD/DVD into drive and restart holding down OPTION/ALT key,this should give boot options of OSX hdd, Windows hdd, and Windows CD/DVD.
Choose Windows CD/DVD using arrow keys and Enter.
Follow Ubuntu instructions to install.On my system it automatically detected other systems and chose to install in correct place.I didn't need to alter swap files or anything else, installation took care of it all.
Once installed Ubuntu will restart and give a page of command line info,wait till it asks you to press Enter,when it will eject disk and restart.
You may need to install additional drivers which Ubuntu automatically found on my system,namely ATI and Broadcomm drivers. Have been checked but are not open source so are proprietary drivers.
Now When you start computer you should have screen from rEFIT which allows you to select system to boot. This screen also has option to sync partitions but on mine it was ok.
You will still be able to use bootcamp to swap between windows and mac as before,but have to restart to get Ubuntu.

Reason for doing above.I use OSX at home,college uses windows and going on to use linux for multi-user operating systems, and can access college network from home but is faster if using natively rather than going through college network.
Hopefully this helps.

---

### Post by Xadrieth on 2010-12-12
Thanks for all the help guys, but I just decided to try out Wubi and it worked, though I want to use Ubuntu 10.10, I'm still happy with v10.04

---

