---
title: "wireless and grub questions"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by catspawsd on 2006-08-20
I am a complete newbie to linux and ubuntu.  I have downloaded and installed the ubunto to my laptop, and I have 2 issues to start.

1. in grub, how can I have the default opereating system be windows instead of ubuntu?  My wife uses the computer too, and she has no wish to play with linux at this time.

2. I have an Acer travelmate 2403wxci, with built-in broadcom adapter.  How can I get this to work in ubuntu.  keep in mind I am a complete newbie to linux and know nothing.

Thanks

---

### Post by thedivvyman on 2006-08-20
Hi - I am also a complete beginner as far as ubuntu is concerned.
First, I didn't install ubuntu on my hard drive for the very reasons you are concerned about. Don't know whether you can swap the default OS in GRUB. I  have  no  doubt  someone  on  here  will  enlighten  you.  I  can  tell  however  that  you  can  forget  your  wireless internet connection. I have spent quite a few hours  seeking  advice  on  this very subject  and  come  to  the  conclusion  that  even  though  certain  wireless  cards  are  supported  by  ubuntu  there  is  a  glitch  in  it  somewhere. Folk  on  this  forum  will advise  you  to  choose  a  wired  connection,  ethernet  probably.  Hope  this  saves  you  some  time.
Good  luck

---

### Post by pteri498 on 2006-08-20
As for your wireless connection, look into ndiswrapper. I used it on knoppix when I was playing with it, and it gave linux a working connection between the operating system and the wireless card by using the Windows driver for it.

Just make sure you follow the instructions CLOSELY.

---

### Post by Tomosaur on 2006-08-20
Changing the default Grub selection is very easy. You can just alter the /boot/grub/menu.lst file and look for the line which says 'default   <num>'. By default, '<num>' will be '0'. Grub counts from zero, so the second item is '1', third is '2' etc etc. Just change the number to suit your needs, but watch out, because the 'Other Operating Systems' line on the Grub menu does count as a menu item.

Alternatively, you might want to take a look at the link in my sig. It may be overkill if you only want to edit the default setting, but it'll do the job, and you may want to play with some other settings.

---

### Post by nickpaton on 2006-08-20
Hi Catspawsd and welcome to the forums

Can I just recommend Tomosaur's excellent GrubEd program, which works very well indeed - one of those 'must have' programs IMHO.

To expand his post you will need to actually carry out the commands as follows:

Open a Terminal; Applications>Accessories>Terminal.

In there type the following:

```
sudo gedit /boot/grub/menu.lst
```

It will ask you to login with the password you use when you start Ubuntu.

After a few seconds this will open a menu.lst and you will find the NUM para right near the top.
Change the default figure from what is probably 0 to 1 and try that.
Keep on trying until Windows is your default.

If however you use GrubED, you can simply select your default OS (Win XP) by clicking on it, and the program takes care of the rest.

Apologies for a slight change of post topic, but shouldn't do any harm putting this here.

Simply click on Tom's link and choose to download it to your Home folder.

Note it's a zip file so to unzip it navigate to your Home folder.

Places>Home Folder, and navigate to the zip file.

Right click on it and select "Extract Here" which will unzip it into a new folder within your Home Folder.

Now go to Tom's post No 7 which explains how to put it on the Desktop.

Just to expand that: 

On the 'Create Launcher' Window:

Name - I called it 'GrubEd'

Go to 'Command Line' and type in the command as per post 7 with your name change after  sudo sh /Home/.

If you want to put in an Icon, click on the No Icon button and select a suitable one.

OK

To run click on the desktop icon which will open a Terminal which requires you to put in your password.
From there enjoy GrubEd!

---

### Post by catspawsd on 2006-08-20
Thanks everyone, especially Tomasaur!  GrubEd is great, works for me.  Now my wife won't complain and I can start learning linux/ubuntu.

Now if only I can get the wireless to work on my laptop.  
I have read a lot of other posts regarding this problem, but they are very confusing to me.  e.g. most of them talk about 'ndiswrapper'.  I don't know what this is, or how to install it. 

This is really a hassle, I boot into ubuntu, try something, then have to back to WinXP to connect to the net and these forums.  

Help!

Anyway, thanks again for the GrubEd info, and hope someone will be able to help with the wireless issue.

---

### Post by nickpaton on 2006-08-21
Hi Michael - pleased to hear you've got GrubEd going - great app.

Onto your wirelesss.  It's quite straight forward and I suggest you do it using Automatix to install Network Manager.

Automatix allows you to install loads of programs which you'll want to use, but without the hassle you can sometimes have  - a clever program all in all.

Go to here:

[http://getautomatix.com/]("http://getautomatix.com/")

Go to Install and follow the instructions to install on Ubuntu Dapper (I assume you have that version).

One or two points:

1. Open a terminal and use gedit as instructed.  
This will open a new Sources.list window.
Copy and paste somewhere into the Sources.list the line deb.......... dapper main.
Save and close Sources.list Window.

2. The next section is all done in the Terminal - just copy and paste them all in until finally you have run the sudo apt-get update automatix command.

That's it for Automatix, and you will find it in Applications>System Tools.
What you may wish to do is to put it as a shortcut on the desktop by right click and place launcher on Desktop.

Run Automatix and click through the credits and enter password etc.
When Automatix is open scroll down and select Network Manager & OK.
This will load and make them available to you under System>Administration>Windows Wireless Drivers.

Exit Automatix but make sure you click OK to reinstall your original repos.

You will have to go back to XP to search for and make a copy of your Broadcom .inf driver which will be something like bcmwl5.inf. Note it may be a hidden file.

Start up Ubuntu again and place the .inf file in your Home folder.

Fire up Windows Wireless Drivers program and if there is no bcmwl5 file already present in the Currently Installed Wireless Drivers box (unlikely!) click on Install New Driver and navigate to Home folder to bcmwl5.inf file and click Install.
If it installs OK the driver will appear with Hardware Present: yes.

Next onto Configure Network and set up your wireless network.

I had a job getting this to work, and found I had to disable within the program the Ethernet Connection (the wired one) and mess around until the wireless connection suddently bursts into life. Suggest running the wireless part unencrypted until you get it to work.  Also do a reboot
What you are looking to do is to get Default Gateway to be the same as the wireless device and it seems to resist doing this.  Keep persisting until you get it!

Good luck!

---

### Post by catspawsd on 2006-08-22
Thanks Nick.

I obtained and installed the AUTOMATIX program.  This works great, it make the install process MUCH easier, more like I'm used to from windows.

I installed the Network Manager, worked like a charm.  Went to Windows, and searched for the bcmwl5.* files.  Found bcmwl5.sys, bcmwl5.inf, but no ini file.  I copied the .sys and .inf files to a thumbdrive, then booted back to ubunto.  Copied both files to my home directory, and ran the Windows Wireless Drivers progam, installed the driver.  It reported than the driver was installed, and hardware present.  Clicked on configure, and set up the ESSID and WEP key.  The system said the eth1 wireless connection was not active.  Click on activate.  after a while it came back and said it was active.  tried to access the internet, came back "server not found".  Checked the Network info again, connection was again "not activated".  This is the same symptoms I have been having all along.

Any thoughts?

Thanks for you help.

---

### Post by nickpaton on 2006-08-22
HI Michael

This was exactly the problem I had when trying to get Network Manager to accept my settings.

The key to it is to make sure that your _Wireless_ Eth1 is the default Gateway, since I found that it kept changing back to the the wired one.

Don't ask em how but it suddenly all started working, and I think what I did was to disable the Wired LAN connection, and make my Wireless connection the default gateway.

For simplicity I also initially ran the whole set up unencrypted with no WEP key (but obvioulsy with the SSID!)to make sure there was no errors there, stopping the whole thing from working.

Rebooting after making changes was also necessary, and I think may be key to the whole thing as well.

As I said persistence will pay off in the end!

Sorry for giving you the wrong info on the file type - yes it's .inf

---

### Post by thedivvyman on 2006-08-22
Sorry  for  butting  in  here,  but  I  have  the  same  problem. Differences  are  that  I  am  at  present  running  ubuntu  from  the  cd (not installed to hdd) amd  my  wireless  adapter  is  an  Asus  WL-167G.
How  do  I  download Automatix when I have no internet connection when using ubuntu? I am building up courage to install ubuntu to my second hdd, as I do realise that any installations/changes I make while running from cd  will be  wiped after shutting it  down.
Sorry for being a nuisance, but I would really like to use ubuntu with an internet connection.

Thanks
Brian

---

### Post by nickpaton on 2006-08-22
Hi Divvyman and welcome!

I have not personally tried accessing the Internet using the Live CD, but I do know that the advantage of using it, is that nothing is saved on the HDD.  

Therefore if you want to try out your system to access the Internet Wirelessly you will not be able to do it with the Live CD.

Can I encourage you to bite the bullet, partition your HDD and load Ubuntu on.

I realise this is very obvious but remember first to Defrag the disk, then back up any vital data.

There are many posts and Howto's for partitioning your HDD etc., but FWIW I've created the following extra partitions to load Ubuntu:
Ext3 for the main programs
Swap 
Fat32 which allows you to pass files between your Windows and Ubuntu, and is a good general extra storage place.

Now's the time to get down & dirty and go for it - Good LucK:D :D

---

### Post by nickpaton on 2006-08-22
Sorry, duplicate post - deleted!

---

### Post by thedivvyman on 2006-08-22
Thanks  for  the  encouragement - that's  all  I  needed. That  last  partition  you  mentioned fat32  -  will  that  be  my /home folder then? or  is  the  fat32  an  additional  partition?
Cheers

Brian

---

### Post by nickpaton on 2006-08-22
> **thedivvyman said:**
> Thanks  for  the  encouragement - that's  all  I  needed. That  last  partition  you  mentioned fat32  -  will  that  be  my /home folder then? or  is  the  fat32  an  additional  partition?
Cheers

Brian

Some people have their Home folder in a separate partition in case things go belly up, but personally I've simply used the FAT32 partition as a general repository for folders and files, and tend to save anything I want to keep there.

It's a separate partition and mine is about 2Gb or so.  It's down to you how much space you can spare.

For more information on this read:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Also have a look at this which goes into some detail about dual boot and partioning:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/")

Let us know how you get on and any probs we can assist you with - good luck Brian!

Nick

---

