---
title: "VMWare or any virtual machine"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-08
Trying to get VMWare or a number of other virtual machines to work on my system.

Can someone explain to me what is happening here in this terminal windows:

caruso@caruso-desktop:~$ sudo apt-get install build-essential uname -r apt-get install linux-headers-'kernel version' apt-get install gcc-3.4 apt-get install g++-3.4
E: Command line option 'r' [from -r] is not known.
caruso@caruso-desktop:~$ apt-get install build-essential uname -r apt-get install linux-headers-'kernel version' apt-get install gcc-3.4 apt-get install g++-3.4
E: Command line option 'r' [from -r] is not known.
caruso@caruso-desktop:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
caruso@caruso-desktop:~$ sudo apt-get install build-essential
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
caruso@caruso-desktop:~$ sudo dpkg --configure -a
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.191.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] yes

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.90.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] yes

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player


Also, I tried to install Virtual Box.  It keeps telling me that only one installation package can run simultaneously . . . well, none are.  The only way I can get rid of that message is to power the computer down and reboot.  Then, the first instance of Virtual Box stalls.  If I stop it, I can't restart it until I power down and reboot.

As a non-programmer who is considered Win savvy, this Ubuntu stuff is pounding in my head (or has my head pounding).

Help would be appreciated.

Thanks.

Caruso

---

### Post by zvacet on 2007-04-09
```
sudo aptitude install build-essential
```

---

### Post by carusoswi on 2007-04-13
Thanks for the reply.  When I run the command you suggested, the following resulted:

caruso@caruso-desktop:~$ sudo aptitude install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  evolution evolution-data-server evolution-data-server-common 
  evolution-plugins firefox firefox-gnome-support kdelibs-data kdelibs4c2a 
  libaudio2 libcamel1.2-8 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-7 libedataserverui1.2-8 
  libegroupwise1.2-12 libexchange-storage1.2-2 libfreetype6 libkrb53 
  libnspr4 libnss3 libqt3-mt libxfont1 linux-headers-2.6.17-11 
  linux-headers-2.6.17-11-generic linux-image-2.6.17-11-generic 
  linux-libc-dev openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer python-uno ttf-opensymbol wine xserver-xorg-core 
  xserver-xorg-dev 
0 packages upgraded, 0 newly installed, 0 to remove and 48 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
caruso@caruso-desktop:~$ 


Can you tell me what I am doing wrong?
Thanks.
Caruso

---

### Post by seshomaru samma on 2007-04-14
I think you need to get rid of virtualbox before you can install anything else
How did you install virtualbox?

---

### Post by carusoswi on 2007-04-14
> **seshomaru samma said:**
> I think you need to get rid of virtualbox before you can install anything else
How did you install virtualbox?

Poorly and unsuccessfully.  How do I get rid of it (actually, I would like it to run if it will).

Having some success with Crossover, not much at getting a virtual up and running.

Thanks for the reply.

Caruso

---

### Post by forrestcupp on 2007-04-14
I know this may be a stupid question, but did you try just installing vmware-player from the repositories?  It's a lot easier that way.  I didn't have any trouble at all.

---

### Post by carusoswi on 2007-04-14
> **forrestcupp said:**
> I know this may be a stupid question, but did you try just installing vmware-player from the repositories?  It's a lot easier that way.  I didn't have any trouble at all.

I will try it now.

---

### Post by seshomaru samma on 2007-04-14
What I mean is by 'how did you install it' is :
did you download a file a from the internet ?
did you use synaptic?
did you use apt-get (apt-get install virtualbox)?
did you follow some guide or wiki? of so please post it

by knowing which method you used to install you can figure out how to uninstall it

---

### Post by carusoswi on 2007-04-14
I have tried several methods - probably some or all of what you suggested.  I just now used the repository to get Vmware, but, it's actually already on my computer.  When I use the applications menu to start Vmware (the icon is labeled Vmware Player), a "player" opens up that looks not unlike an "explorer" window.  There are two panes that I can click around in, but, I don't know what to do from there.

Just browsing the net, and I see advice to download Vmware Server 1.0.2-39867.tar.gz.

I am downloading it.

Thanks again for offering some help on this.  I am pretty good at XP and other things Win, but very green on ubuntu.

Caruso

---

### Post by carusoswi on 2007-04-14
Additional Info:
When I click on the Vmware icon under Applications-system, the box that appears is an "Open Player" box and is looking for a vmx file.

Caruso

---

### Post by carusoswi on 2007-04-14
here is more.
I try to uninstall vmware by unclicking it in the add/remove menu.  I get a message that I cannot do that, I should use Synaptex.

When I try Synaptex, I get this message:

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Caruso

---

### Post by carusoswi on 2007-04-14
Ok, I found this in another thread from someone who found it on IRC:

sudo dpkg --purge --force-remove-reinstreq brasero

That command allowed me to totally remove Virtualbox so that I could extract it again and attempt to install cleanly.

Hope this helps someone else.  Sure has been a frustrating day so far.

Caruso

---

### Post by steve.horsley on 2007-04-14
Well done finding that command. Now you know how to undo the damage caused by a failed install, you could try again if you want. I have a feeling it needs the build-essential package installing. You could try that, and then see if the install goes any better.

---

### Post by carusoswi on 2007-04-14
> **steve.horsley said:**
> Well done finding that command. Now you know how to undo the damage caused by a failed install, you could try again if you want. I have a feeling it needs the build-essential package installing. You could try that, and then see if the install goes any better.

Well, I learned Windows the same way I'm learning Ubuntu - pick and poke.  As I recall, back in the day, there were quite a few helpful Win-forums around - still are.  None seem as helpful as this Ubuntu forum, however.

I got Vmware to work following the advice and steps in this thread:  [http://ubuntuforums.org/showthread.php?t=342631&highlight=exit+status+1](http://ubuntuforums.org/showthread.php?t=342631&highlight=exit+status+1)

I never succeeded in getting Vmware to recognize my WindowsXPPro.iso image.  I may have misunderstood the directions about that point.  I understood that you were supposed to create a virtual CD ROM drive by storing that file in a hard drive directory, then pointing Vmware to the file when it complained about not being able to locate your CD ROM drive.  That never worked for me - maybe there was something wrong with my .iso image.

I found the recommended CD Burner to be quite clunky, as well.  Anyhow, I gave up on the .iso file and just modified the vmx file so that the little CDROM icon at the top of the virtual machine screen was "lit up" and I loaded WinXP Pro from my regular Microsoft-issued XP disc.

The poster mentioned something about hardware - I'll have to review his info again - I cannot get some of the XP audio software that I like to use to recognize my CD Rom or my sound card.  I get sound, but cannot use that XP software to record, although it will play back.  That seems a little strange, but, then, again, the idea of running what appears to be a fully operable instance of XP from within Ubuntu also feels strange (wonderfully so).

I don't know if it was worth spending a whole day to get this working, and, if my Ubuntu crashed tomorrow, I'd probably have to spend another 3/4 of a day figuring out just what I did to get it working.  It sure helps to have so much excellent, well informed advice on this site.

Thanks again for your reply.

Caruso

---

### Post by HowardDrake on 2007-04-16
Also, one other note for VMware (since I use workstation 6.0 Beta under Feisty Beta at the moment, I know its a lot of beta but its working so far) one recommended site is:

[www.easyvmx.com]("http://www.easyvmx.com")

I use this to create VMX files for VMware, works quite nicely.

---

### Post by jvc26 on 2007-04-16
Another option is to use VMware server, following the instructions [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29") to get hold of it, and if you are using feisty look below here to see the alterations needed to make it install properly.

Note these are from marceloshima originally posted [here]("http://ubuntuforums.org/showthread.php?p=2143833#post2143833")
> 
If you already have VMware Server installed and want it to use the Feisty modules you can jump to Step 3

Step 1 (Installing the modules from repository)
$ sudo apt-get install vmware-server-kernel-modules

Step 2 (Installing VMware Server)
$ tar -xzf VMware-server-1.0.1-29996.tar.gz
$ cd vmware-server-distrib/
$ ./vmware-install.pl

Step 3 (Make VMware Server Daemon work with Feisty modules)
$ sudo sed -i -e "s/\/sbin\/insmod -s -f \"\/lib\/modules\/\`uname -r\`\/misc\/\$1.o\"/modprobe -s -f \$1/" /etc/init.d/vmware

Step 4 (Make the configure script ignore the configure of a new module)
$ sudo sed -i -e "s/sub configure_module {/sub configure_module {\n return 'yes';/" /usr/bin/vmware-config.pl

Step 5 (Reconfigure)
$ sudo vmware-config.pl

Step 6(Restarting the application)
$ sudo /etc/init.d/vmware restart

They got my vmware server working 100% with feisty.
Il

---

### Post by kvonb on 2007-04-16
>  Can someone explain to me what is happening here in this terminal windows:

caruso@caruso-desktop:~$ sudo apt-get install build-essential uname -r apt-get install linux-headers-'kernel version' apt-get install gcc-3.4 apt-get install g++-3.4
E: Command line option 'r' [from -r] is not known.
caruso@caruso-desktop:~$ apt-get install build-essential uname -r apt-get install linux-headers-'kernel version' apt-get install gcc-3.4 apt-get install g++-3.4
E: Command line option 'r' [from -r] is not known.
caruso@caruso-desktop:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
caruso@caruso-desktop:~$ sudo apt-get install build-essential
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
caruso@caruso-desktop:~$ sudo dpkg --configure -a
Setting up vmware-player (1.0.2-2) ...

Yes, look at the very first line:

```
 caruso@caruso-desktop:~$ sudo apt-get install build-essential uname -r 
```

it should be:

```
sudo apt-get install build-essential linux-headers-'uname -r' gcc-3.4 g++-3.4
```

You can copy and paste that whole line above.

The error was caused by a broken command, the **uname -r** was the scrambled part and it messed up everything after that.

Notice in my example above that I install everything on one line, you don't have to type **apt-get install** for each package, just once at the start and seperate each package name with a space.

You'll get the hang of it eventually :)

---

### Post by carusoswi on 2007-04-16
Thanks, everyone.  My Ubuntu machine is cut off from the internet until Friday, so I will not have an opportunity to try these suggestions until then.

Caruso

---

