---
title: "ubuntu"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-13
ubuntu problem

when i first installed fullvertion of ubuntu every thing went well it went through this detecting hardware&setting disc parameters
and all was ok but for one which said fail initializing,random number generator but all others ok,now when installing full ubuntu 
vertion i got this message your network is probably not using dhcp protacol,alternatively,the dhcp sever maybe slow or somenetworkhardware
is not workingproperly,now when i boot up ubuntu i get this message and yellow triangleand it says could not look up internet address
for ubuntubreezy.this will prevent gnome from operating correctly it may be possable to correct the problemby adding 
ubuntubreezy to the file/ect/host,
first thing to do is login name >password then in i go the screen is brown and cd at top left now all seem to be working ok 
some stuff does work but some dont such as things working,

places
home forlder working
desktop ffile browser ok
computer
computer file system ok
applacations
games ok     arcchive ok   calculater ok  accessories ok graphices ok
terminal server ok  open office okinternet fire fox web browser  ok
sound video ok system tools
and if i search for files i just put name gnome in and it finds 2733 files but when i use sudo nothing comes up or gksudo the same

now the things that dont work 
addministrations 
device manager  no working
disk not woking
language no woking
log in screen shop no network no service not  shared folder not synaptic package manager not time date not user groupe not
and thats about it i have not been able to get out onto the web for downloads because i dont know how at the moment

---

### Post by Mustard on 2005-12-13
It sounds like your /etc/hosts file needs editing.

To do this you are going to need to log in as root or use a liveCD to gain access via sudo.  The grub menu at startup has a Recovery mode which should allow you to get to a root prompt.  Alternatively using the live CD you can gain sudo access or login as root and then edit the file that way.  Some further assistance in showing you how to do this can be found in your System>>Help menu by going to the Ubuntu Starters guide and reading the various instructions for 'Rescue Mode'.

Having logged in as root, you could either manually edit the /etc/hosts file or use the hostname command to set a new hostname (this should add the necessary entry in your /etc/hosts file).  Your hostname can be anything you like.  I call my computer 'slave'.  By default its usually set up as 'ubuntu'.

This HOW TO should give you some idea how to do it.

[http://www.ubuntuforums.org/showthread.php?t=3407](http://www.ubuntuforums.org/showthread.php?t=3407)

I hope that makes some sense anyway.

If you have some further questions you can post in here or visit the ubuntu IRC support channel at irc.freenode.net in channel #ubuntu and see if they can help as well.

I'm assuming that your /etc/sudoers file is correctly set up to allow the primary user to have sudo privileges, but is not functioning correctly due to a misconfiguration of your /etc/hosts file.  From the description above I can't say for sure, but that may be something you need to look into as well.

Below is a sample /etc/hosts file for you to compare.

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The first line is the one that you need to edit.  Note the name of my computer 'slave' on the end of the first line.  Change 'slave' to whatever hostname you desire.

---

### Post by janrinok on 2005-12-13
Richard, Hello again.  You have told us which programs are not working.  But in what way are they not working?  What do you see when you try to start one of them? Do they start but not do what you expect, or do they not even start?  The fact that you have got as far as the brown desktop means that a lot of your system is working correctly, what we now have to do is make sure that the rest of it works as well.  Jan.

---

### Post by richard willacy on 2005-12-13
dhcp and text editor i have not got one of these i think and it abit confusing 
at the moment and how do i know my host name :confused:

---

### Post by Mustard on 2005-12-13
[QUOTE=richard willacy]dhcp and text editor i have not got one of these i think and it abit confusing 
at the moment and how do i know my host name :confused:[/QUOTE]

Your hostname can be anything you want.  Type the command hostname into a terminal and it will tell you your current hostname.

Your terminal is found in your Applications>>Accessories menu.

---

### Post by richard willacy on 2005-12-13
ok jan when i go into somthing i just click onto the thing and somtimes double click bit nothing works apart from right side off the mouse if i click to the right you get two or three things that comes up,ilike desktop and some other words but thats it nothing els,but in live cd vertion i could click onto almost everything and it would open :confused:

---

### Post by janrinok on 2005-12-13
OK Richard, don't worry. 

At the top of your screen, there should be 3 menu headings - Applications, Places, and System.  Left click on System, and then in the menu that opens up select 'Administration' and in that sub-menu click on Synaptic Package Manager.  You should next see a prompt in the middle of the screen asking for a password.  Type the same password that you use to log on, and the Synaptic program should start.  Try it and tell me what happens.  If it doesn't open, is the icon (picture) full colour or does it appear a bit faded?  Do you get as far as the password dialog and does it accept your password?  Jan

---

### Post by richard willacy on 2005-12-13
i did what you say and this is what happed,systems>administrations then click onto synaptic and click onto that and nothing happens its gone but if i go to synaptic then click on the right side of the mouse this is what i get 

add the laucher to panel
add this to desktop
add this to drawer to panel
add this to menue to panel 

and thats it nothing els:confused:

---

### Post by Mustard on 2005-12-13
Can you go to your Application>>Accessories menu and choose Terminal, and enter this command at the prompt...

```
sudo cat /etc/sudoers
```

It may ask for your user password. Tell me what output you get from doing that command.

-edit-

I'm pretty sure this is a /etc/hosts file error from the description above.  An error in the hosts file will make sudo stop working.  That pretty much explains why all the Administration functions aren't working in the menus as they require super user privileges to use them.

---

### Post by richard willacy on 2005-12-13
done what you say and it does nothing apart ftom say 
simonjenkins ubuntubreezy thats it nothing els and i put sudo and gk sudo and the thing is that when i used to live cd i did all this sudo stuff and it worked :confused:

---

### Post by Mustard on 2005-12-13
If you find the idea of editing your /etc/hosts file manually a bit daunting I would be tempted to say that you would be better of reinstalling from the CD again and being very careful to make sure you enter a hostname in the appropriate field when it comes to that question.  Ideally you would just use the defaults that are given by the installation program.

/me heads off to bed.

---

### Post by Mustard on 2005-12-13
[QUOTE=richard willacy]done what you say and it does nothing apart ftom say 
simonjenkins ubuntubreezy thats it nothing els and i put sudo and gk sudo and the thing is that when i used to live cd i did all this sudo stuff and it worked :confused:[/QUOTE]

The problem could be solved by following the instructions above, but as I say, if you find that a bit too confusing, your best option is to reinstall.  The most likely scenario for how this occured is that you made an incorrect entry during the install process that has left you without a proper hostname.  By default the installer chooses the hostname 'ubuntu' for you and you can just hit enter and use that.

---

### Post by richard willacy on 2005-12-13
the problem is over i put new ubuntu cd back into the drive and installed it again and this time i did it right,everything works ok brilliant but now comes installing all my stuff but what i would like to do first is get my modem working bt voyager 105 usb adsl modem and some other things like my radeon 9600xl graphices card,its good when things come right and thanks to all members who helped me on this subject thank you:p

---

### Post by janrinok on 2005-12-13
Sorry Richard - I printed the text below before I noticed your reply # 13.  I do not know anything about your USB modem but I will google for it and try and help you if you want me to.

If what you have printed is the exact copy of your sudoers file then it is corrupted, and is probably the cause of many of your problems.  Unfortunately, you will be prevented from becoming 'root' which is essential not only for running many of the programs but also for correcting the corrupt file.  
But I'm not sure that you have printed the contents of your sudoers file.  For example, why does it have the name 'simonjenkins' in the file?  Is there another user of your computer called simonjenkins?  Did you put that name in the file at some time?  Please check once more by typing 'sudo cat /etc/sudoers'.
If you have corrupted files, the easiest solution might be to re-install everything again.  Accept all the defaults unless you are SURE that you know what you are changing and why.  Anyway, before that, please check your sudoers file again.  Jan.

---

### Post by janrinok on 2005-12-13
Richard, I have checked on Google and although some people have successfully managed to get your modem model to work, many have given up and purchased a different ADSL modem/router.  You might need to resubmit on a new Thread using the title of the 'BT Voyager 105 modem'.  Perhaps someone who knows much more than I do can provide some help.  Good Luck!  Jan

I have checked a bit further. Using Synaptic, install the package 'eciadsl' which will provide the correct driver for your modem.  After that, you might have to ask someone else if you still need help.  Cheers mate.  Jan

---

### Post by fishy on 2005-12-22
Hey guys, I'm having a similar problem. Here's how it happened: I tried getting my Linksys wireless card working with that ndiswrapper utility. After trying to install a few different versions of the linksys driver and having no success, I gave up and booted into windows (where the wireless card works fine).  
Upon rebooting back to ubuntu, I noticed my system took an extremely long time at the "configuring network interfaces" stage.  I get to the GDM and try logging in, and I am faced with the following error: "Could not look up internet address for . This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding to the file /etc/hosts."

After reading this thread, I tried editing my hosts file. However, I get this error: "sudo: unable to lookup via gethostbyname()"
So I reboot my system into recovery mode. I punch in "startx" at the root prompt, and when Gnome loads, I get this error: "Internal error. failed to initialize HAL!" Ignoring that, I continue and try to edit my hosts file - the thing is, my hosts file looks exactly like the example given by Mustard (except instead of "slave" it's "ubuntu"). While there, I also check the sudoers file. Here's what's inside:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults           !lecture,tty_tickets,!fqdn

# User priviledge specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root priviledges
%admin  ALL=(ALL) ALL
```

While in recovery mode, I took the liberty of completely removing ndiswrapper  through synaptic. I was hoping maybe that might do some good, but it doesn't look to be that way.

So it sounds like the problems I'm having match pretty closely to what has been described, but editing the hosts file doesn't appear to resolve anything.
In conclusion: I'm stumped :( 
Any help would be greatly appreciated. Thanks!

P.S. Sorry for being so long winded; I just wanted to provide all the background info in hopes that it would help the troubleshooting process.

---

### Post by fishy on 2005-12-22
Searching further into the forums, I think I might need to fix my sudoers file. However, I have no idea what needs fixing nor how to fix it. Won't correcting the sudoers file only give me the ability to use administrative/sudo functions again? I don't see how it will resolve anything regarding the network interfaces.
This is getting rather frustrating...I don't want to have to reinstall Ubuntu from scratch, as I've spent a fair bit of time customizing it and fear it will be difficult to get it all back again. Damn those wireless cards and the mess they've created for me :(

---

### Post by bscbrit on 2005-12-22
There is no need to edit your sudoers file if it is the same as the one displayed.  What you _do_ need to do is make yourself a member of the admin group.  All members of this group will be given root powers by your sudo file.  Read 'man group' for details how to do this.
However, I agree that your lack of sudo access is not the cause of the network problem.  But, one step at a time....

---

### Post by fishy on 2005-12-22
I opted to just wipe everything and start with a fresh install instead. Considering how I had hit a wall troubleshooting my problem, I figured it would be faster in the end. Thanks anyway though :)

---

### Post by bscbrit on 2005-12-22
yes - sometimes that can seem to be the easiest option.  Neither of us will learn as much, but the main aim is to get you a working system!  Good Luck and come back if you need any more help.

---

