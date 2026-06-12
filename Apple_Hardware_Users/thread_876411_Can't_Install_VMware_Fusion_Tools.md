---
title: "Can't Install VMware Fusion Tools"
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by obelix112za on 2008-07-31
Hi, 1st day ever using Ubuntu.

I have an iMac 20" 4GB RAM Intel Core 2 Duo (alu), about 8 months old.

Were using parallels, but really struggled to install Windows & Ubuntu, so I got VMware fusion, installed both Windows XP & Ubuntu without any problems.

As you all know, Ubuntu at it's basic screen settings isn't bad, but I want to / have to install VMware Fusion Tools.

I'm no expert, but I learn fairly fast & can generally solve common problems easily. I understand to install VMware F Tools I need to have Super Admin Rights (or something similar). I went & changed the root folders password to my own, also gave myself root admin priviledges, but to no avail. In the Terminal Command, whenever I type in (su -), I'm then asked for my password, but when I've typed that it, access is denied / or wrong password or something.

Please someone help, I spent 5 hours today (googled it, help docs etc), did exactly everything as I read it, still nothing.

I know there's more to Ubuntu than what I've experienced.

VMware Fusion 1.1.3 (94249)
Leopard, fully updated
Newest Ubuntu Version

Thanx

---

### Post by david_lynch on 2008-07-31
> **obelix112za said:**
> I went & changed the root folders password to my own, also gave myself root admin priviledges, but to no avail. In the Terminal Command, whenever I type in (su -), I'm then asked for my password, but when I've typed that it, access is denied / or wrong password or something.

Not really sure what you mean when you say you "changed the root folders password to my own". Help me understand what you were trying to do, and exactly how you went about it.

Perhaps you just need a heads-up on ubuntu security. The user credentials you were prompted for, and entered during, the ubuntu install are for the admin user. That user id has superuser access through sudo. Can you log in as that user? If so, can you successfully run sudo?

---

### Post by cyberdork33 on 2008-07-31
You do not need to modify the root password, not do you ever need to login as root. You should use 'sudo' to run commands with root permissions.

To install the tools, first upgrade you system:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
reboot if prompted. After that, install a few things you might need to compile the modules in the tools package:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
Next select to install vmware tools from the menus and in the terminal, navigate to the virtual cdrom:
```
cd /media/cdrom
```
On the virtual cdrom there is a script you should run with root permissions to install the tools:
```
sudo ./vmware-install.pl
```

Say 'yes' to all the prompts.

---

### Post by obelix112za on 2008-08-01
When I say gave myself root priviledges, I went into Users & Groups & changed the password in the root account to be the same as my own account.

I tried updating, this is what happens


[IMG]http://i204.photobucket.com/albums/bb216/obelix112za/Ubuntu1.jpg[/IMG]

---

### Post by obelix112za on 2008-08-01
My password doesn't seem to work, I've tried sudo & everything.

Also remember, I'm very new to this, never really had to use terminal before, so it's probably a stupid mistake I'm making.

---

### Post by obelix112za on 2008-08-01
If I don't answer back soon, I'm working all weekend, so probably only back next week some time...

---

### Post by cyberdork33 on 2008-08-01
> **obelix112za said:**
> When I say gave myself root priviledges, I went into Users & Groups & changed the password in the root account to be the same as my own account.Which should not be done. There is no reason to set the root password in Ubuntu.

> I tried updating, this is what happens
It looks like sudo might be broken... for one thing, your password should not be displayed in the terminal. 

When you enter the command you will be prompted to enter your _user_ password
```
cyberdork33@Ubuntu-Virtual:~$ sudo apt-get update
[sudo] password for cyberdork33:
```You will not be able to see what you are typing. type your user password and hit enter, and the command will execute.

---

### Post by obelix112za on 2008-08-01
I think I got it installed, but how do I know it is really installed? What difference should it make?
Sound stupid, but I really don't know...

---

### Post by cyberdork33 on 2008-08-01
> **obelix112za said:**
> I think I got it installed, but how do I know it is really installed? What difference should it make?
Sound stupid, but I really don't know...
It won't lock your mouse/keyboard in the window... you can freely move it in and out and click on things.

You can select much higher screen resolutions...

---

### Post by obelix112za on 2008-08-02
I am delighted. Got it installed. Now I'm hooked.

What bugs me now is that I thought (for whatever reason), once I have that installed I can change in the Appearance prefs on the Visual Effects Tab, the extra option, but for some reason I can't. Could it be because I'm running Ubuntu in VMware Fusion?

---

### Post by mfox on 2008-08-03
My Ubuntu 8.04 installation on VMware Fusion won't let me install desktop effects either.  When I try, I get a message stating that desktop effects could not be enabled.  However, I could enable them before I went back to an earlier snapshot.  I was having dependency trouble installing KDE 4.1 and after that I got a dependency error in openoffice writer, thus I went back.  Prior to that, it was possible for me to enable desktop effects.  It might have something to do with whether or not you have Compiz installed (?).

---

### Post by cyberdork33 on 2008-08-03
> **obelix112za said:**
> I am delighted. Got it installed. Now I'm hooked.

What bugs me now is that I thought (for whatever reason), once I have that installed I can change in the Appearance prefs on the Visual Effects Tab, the extra option, but for some reason I can't. Could it be because I'm running Ubuntu in VMware Fusion?
No VM supports 3D acceleration at the moment, thus, no visual effects.

---

### Post by motsteve on 2008-08-03
> **obelix112za said:**
> I think I got it installed, but how do I know it is really installed? What difference should it make?
Sound stupid, but I really don't know...

If your VMware tools are installed, you should be able to copy/paste back and forth to MacOS, you should be able to get a full screen desktop and not blank space with a small screen desktop.  You should also be able to use both OS's as if the windows weren't there, in that you can get in and out of the vm without having to push alt command.  The real test is being able to drag a file from the Mac desktop to the desktop of Ubuntu.  If you can't do any those things, you'll need to install the vmware tools the way outlined in:


[http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html](http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html)

Prepare to type if you do have to install this way, unless you want to switch back and forth to Firefox from the terminal, copying and pasting. Bottom line: having VMware tools is worth all the effort.

---

### Post by timpl on 2008-08-21
> **cyberdork33 said:**
> You do not need to modify the root password, not do you ever need to login as root. You should use 'sudo' to run commands with root permissions.

To install the tools, first upgrade you system:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
reboot if prompted. After that, install a few things you might need to compile the modules in the tools package:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
Next select to install vmware tools from the menus and in the terminal, navigate to the virtual cdrom:
```
cd /media/cdrom
```
On the virtual cdrom there is a script you should run with root permissions to install the tools:
```
sudo ./vmware-install.pl
```

Say 'yes' to all the prompts.

Thanks for all the above.  I tried it on my new installation of Ubuntu 8.04.1 on VMware Fusion 2 Beta 2.  All went well until I got to the last line of   ./vmware-install.pl[/code]    which led to the reply of:

  sudo: ./vmware-install.pl: command not found

My suspicion is that the link of VMWARE Tools to the virtual CDROM is failing.  I am ignorant enough of Linux to be unable to get a list of what is on /media/cdrom .

I would be very grateful for any further assistance as, like the OP, I am stuck.  Hopefully I append the file of the transactions I had on Terminal.

Tim Powys-Lybbe

---

### Post by cyberdork33 on 2008-08-21
> **timpl said:**
> Thanks for all the above.  I tried it on my new installation of Ubuntu 8.04.1 on VMware Fusion 2 Beta 2.  All went well until I got to the last line of   ./vmware-install.pl[/code]    which led to the reply of:

  sudo: ./vmware-install.pl: command not found

My suspicion is that the link of VMWARE Tools to the virtual CDROM is failing.  I am ignorant enough of Linux to be unable to get a list of what is on /media/cdrom .
You have to choose "Install VMWare Tools" from the VM menus before the CDROM image is loaded in your guest OS.

PS. to list files in a directory, use the command "ls" (that is a lowercase L)

---

### Post by timpl on 2008-08-21
> **cyberdork33 said:**
> You have to choose "Install VMWare Tools" from the VM menus before the CDROM image is loaded in your guest OS.

PS. to list files in a directory, use the command "ls" (that is a lowercase L)
Yes, I had indeed clicked on "Install VMWare Tools" first.  The option is still showing "Cancel VMWare Tools Installation".  I still suspect there is something about my installation that prevents it from putting the image in the virtual CDROM.

Thanks for the ls command, I'll go kill Fusion and start again and see what this shows.

Tim Powys-Lybbe

---

### Post by cyberdork33 on 2008-08-21
> **timpl said:**
> Yes, I had indeed clicked on "Install VMWare Tools" first.  The option is still showing "Cancel VMWare Tools Installation".  I still suspect there is something about my installation that prevents it from putting the image in the virtual CDROM.
I would cancel and then enable it again. If the cd was "inserted" (virtually) it would show up on your desktop.

---

### Post by hajk on 2008-08-21
Psst! There is a really simple way of compiling the vmware kernel modules, installing the vmware tools and the vmware toolbox, but I hesitate to explain that here. You know, it's not done the Ubuntu way, since it's the Debian way. No! No! Don't be alarmed! The big fellow (MS) himself says that U equals D, so it's probably OK... No? The Debian testing (Lenny) repository has openvm-source, -tools, and -toolbox packages; just download them and install them with```

sudo dpkg -i openvm-xxxxxxxxxxxxx.deb
```commands. Next, get the compiling environment the easy way,```

sudo aptitude install module-assistant
sudo m-a prepare
```
then compile/install the modules with```

sudo m-a a-i openvm
```
and you're all done. Check with```

lsmod |more
```that some four or five modules are indeed present, then you might also add these modules to the /etc/modules file. But, of course, don't do it this way if you don't want to be tainted by that l33t Debian stuff; in that case keep plodding on the way shown earlier in this thread...:popcorn:

Edit: check [http://packages.debian.org/lenny/open-vm-source](http://packages.debian.org/lenny/open-vm-source) also for a couple of dependencies you may have to install as well...

---

### Post by cyberdork33 on 2008-08-21
> **hajk said:**
> in that case keep plodding on the way shown earlier in this thread...:popcorn:
:tongue:

---

### Post by timpl on 2008-08-21
> **cyberdork33 said:**
> I would cancel and then enable it again. If the cd was "inserted" (virtually) it would show up on your desktop.

Right!  Thanks for the info that the virtual cdrom should show on my desktop: it wasn't.  But what was showing was the virtual cdrom for the Ubuntu installation, Ubuntu 8.04.1 i386, so I used the last braincell and dismounted that and this time the vmtools cdrom image showed up on starting an Install.

That done I went through your procedure but it still would not execute the final command of <sudo ./vmware-install.pl> saying something to the effect that it was not found.  So I used the ls command (thanks) and found there were three objects on the CDROM image, a manifest, a tar.gz file and a rpm file.  I suspected that some un-tarring was needed so roughly followed the original procedure on the VMware site for installing Tools within X.  After a certain amount of to-ing and fro-ing, I got the commands to work and completed the procedures and, incredibly, VMware Tools are now installed.

Many thanks for your help: without it I was quite lost

Tim Powys-Lybbe

---

### Post by cyberdork33 on 2008-08-21
> **timpl said:**
> That done I went through your procedure but it still would not execute the final command of <sudo ./vmware-install.pl> saying something to the effect that it was not found.  So I used the ls command (thanks) and found there were three objects on the CDROM image, a manifest, a tar.gz file and a rpm file.  I suspected that some un-tarring was needed so roughly followed the original procedure on the VMware site for installing Tools within X.
D'oh! Yes I forgot about that part. I must have been out of it that day. :) Glad you got it working.

---

### Post by hvc123 on 2008-08-21
what i do when i want root and sudo just aint gunna cutit/ 

i sudo /bin/bash

this logs u in as root without the need to actually "activeating" the root password

---

### Post by cyberdork33 on 2008-08-21
you can also 'sudo su'

---

### Post by John F on 2009-02-24
On the virtual cdrom there is a script you should run with root permissions to install the tools:
```
sudo ./vmware-install.pl
```

Say 'yes' to all the prompts.[/QUOTE]


I made it all the way to the last step . . . but in the terminal window I got the message "No such file" or words to that effect, and in the file manager window, clicking on the "vmware-install.pl" file and making the terminal choice, nothing happened.

John F

---

