---
title: "(maybe) Moving to Ubuntu form Mandrake and have some Q's"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Hudson Hawk on 2005-07-24
Hi im using mandrake linux (2005 LE Download) as a dual boot on an AMD 2600+ WinXP system and an AMD64 WinXP Laptop and considering moving to ubunto and have a few questions:

1) Does the install have any problems setting up a dual booting with XP Home?

2) I have heard the root user is disabled, how does this affect setting permissions, security and running the likes of Apache or setting MySQL permissions?

3) Any good links on getting ATi drivers working under Ubuntu.

4) Im planning on using the Linux system for PHP, Java, HTTP, MonoDevelop(C#), MySQL, Apache, Open Office, Gimp, Blender(assuming i can get my ATI card working), ripping CD's to MP3, burning CD's and DVD's & playing CD's & DVD's .... is there any pitfalls inherant to unbunto I should be aware of?

5) Does it come with the pre-requisites to get gDesklets running? ..... i ran into no end of problems getting it working under Mandrake 2005 LE.

Cheers, 


HH.

---

### Post by Juergen on 2005-07-24
1) not for me :-) 
But AFAIR you have to choose 'expert install', otherwise Ubuntu will repartition and use the whole disk. 
If you have 2 disks, I think normal install should work - but **read all messages**,  don't blame me if something goes wrong ;-)  , or use expert to be sure.
(There are some people for whom expert install doesn't create a sudo-user it seems.
You might want to search here before you start.)

2) These server-apps should run under their own accounts anyway. 
A bug in mySQL shouldn't result in root access-rights for those that know how to exploit it.

3) AFAIK included - you probably need to activate at least one of the 'restricted', 'universe' and maybe 'multiverse', repositories.
To get all the nice programs, you want to enable them anyway, I think.

4) You need to install patented codecs (like mp3) or otherwise restricted stuff from the repositories in 3)

5) Many gdesklets are included, probably again in 'universe' or somewhere, not on the install-CD

If you can get any Linux to run, you usually shouldn't have problems with Ubuntu.
And then there is this forum... ;-)

---

### Post by poofyhairguy on 2005-07-25
first of all- I must be honest, Ubuntu is a little harder than Mandrake. If you HATE the command line...better stick with what you got.

Still here? Good. Its worth it I promise. 

[QUOTE=Hudson Hawk]

1) Does the install have any problems setting up a dual booting with XP Home?[/QUOTE]

None as long as you don't accept the defaults.

> 2) I have heard the root user is disabled, how does this affect setting permissions, security and running the likes of Apache or setting MySQL permissions?

You can make a root account:

[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

> 3) Any good links on getting ATi drivers working under Ubuntu.

Yep.

[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati)

Of course, it won't magically make the ATI drivers better than in Mandrake (as you probably know, ATI's Linux support is lacking). For serious 3D...honestly only Nvidia will do.

> 
4) Im planning on using the Linux system for PHP, Java, HTTP, MonoDevelop(C#), MySQL, Apache, Open Office, Gimp, Blender(assuming i can get my ATI card working), ripping CD's to MP3, burning CD's and DVD's & playing CD's & DVD's .... is there any pitfalls inherant to unbunto I should be aware of?

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Do that. Then enter this command:

> sudo apt-get update

Then scroll down the guide and it will tell you how to install codecs for media files (mp3s included) and how to get good media player.

As you can tell...that guide is THE Ubuntu resource. Be sure to read the notes at the top.

> 5) Does it come with the pre-requisites to get gDesklets running? ..... i ran into no end of problems getting it working under Mandrake 2005 LE.


When you do that last step, you can install gdesklets in synaptic

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

---

### Post by Hudson Hawk on 2005-07-25
Thanks.... well just tried an install and met with frustration  ](*,) 

Nuked my Mandrake partition during the Ubuntu install..... then the CD would not read past 9% of the install(it wrote fine with no errors) .... given how long installs usually are coupled with the fact most of Ubuntu's user are d/ling and burning the disk themselves i dont think it would be irking anyone if it checked the disks integrity before the partitioning option... luckily i have my windows partition to go back to and download and burn a new ubuntu disk... but for some one who didnt it would be an entire reinstall of thier other OS, 600mb+ dl, burn and cross fingers all over again.

I dont know as im no Linux guru and its porbably a rare problem but it would have been nice to know the disk was borked before i nuked half my HDD. :(

here we go again.... (crosses fingures) ;)

---

### Post by Hudson Hawk on 2005-07-25
Arrrg ](*,) what a nightmare....
Got it installed.... but despite not touching my windows partition and the automatic GRUB set up recognising it during installation when i select WinXP Home from the GRUB menu my system reboots  :-x.

I have a generic monitor so im forced in to 640 x 480 resolution with absolutley no way of of setting it during installation and forced to edit Xorg.conf ... which i can not get to work despite following guides on this site :( ... still i'll persist for now

---

### Post by Hudson Hawk on 2005-07-25
Well my desktop is now totaly fluffed.....i ran the X set up utility and obviously set somthing it didn't like as it now fails to load the XServer and dumps me to the command prompt..... i did back up Xorg.config BUT there is no root user so i cant copy it back over the one in use  :mad: 

Is there any point even trying to instal the 64 bit version on my laptop? will it detect the built in 15 inch monitor? and any clues as to why it killed XP's ability to boot on my desktop... 

i'd hate to have to reinstall XP on my laptop ... to do it with an OEM disk rather than a recovery disk (so i can partition the drive) requires me to place it in the fridge, on top of a covered baking dish full of ice or it over heats and falls over :( (And NO acer dont recognise this as a problem becuse they only support software supplied with the system anything else and you can get stuffed as far as they care)

---

### Post by UbuWu on 2005-07-25
[QUOTE=Hudson Hawk]i did back up Xorg.config BUT there is no root user so i cant copy it back over the one in use  :mad: 
[/QUOTE]

You can use sudo for that. Just type sudo in front of the command you want to run as root, and you will get asked for your password. So it would be something like:

sudo cp Xorg.backup Xorg.config

---

### Post by aysiu on 2005-07-25
[QUOTE=Hudson Hawk]
I have a generic monitor so im forced in to 640 x 480 resolution with absolutley no way of of setting it during installation and forced to edit Xorg.conf ... which i can not get to work despite following guides on this site :( ... still i'll persist for now[/QUOTE] How exactly are you editing your xorg.conf file? To get my Ubuntu above 640 x 480, I had to add in the correct HorizSync and VertRefresh ranges for the monitor section of the xorg.conf file. For my monitor, it's 30-62 and 50-70, respectively. What about yours?

---

