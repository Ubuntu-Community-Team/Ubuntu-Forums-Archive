---
title: "vmware"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-01
i will need to use a certain software that only works with windows (martercam v10) so i will need to install vmware.. can you guys give me a hint on how to do it?

---

### Post by davmac on 2006-10-01
If you go to [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) and register for serial numbers, then download the package. You need the "VMWare Server for Linux" .tar.gz file.

Open up a terminal window and navigate to the directory where you downloaded it, then type "tar -xvzf nameofthefile.tar.gz".

You also need the compilers and linux headers installed. In the terminal window type;

 sudo apt-get install build-essential linux-headers-`uname -r`

If you navigate into the new directory you'll see the instructions for completing the installation.

Once you've got it installed, fire it up and connect to the local doodah. Click on the "create new virtual machine" on follow the instructions.

Once you've done this, put the windows install CD in your drive and start the virtual OS. When you've finished installing Windows, in vmware, click on the tools "Install VM Tools" then in the virtual windows it'll appear as a CD, install the tools from the virtual CD.

Hope this helps,

Dave Mac

---

### Post by bulldog on 2006-10-01
> **cmaranhao said:**
> i will need to use a certain software that only works with windows (martercam v10) so i will need to install vmware.. can you guys give me a hint on how to do it?

I'm a noob,but may I ask where the prog is for?

Because if it needs resources which not work in Ubuntu,it won't run in vmware neither.

Example,a wireless connection is not working in Ubuntu,installing windows in vmware will not resolve that problem,it will not run!

---

### Post by ignorance on 2006-10-01
If vmware can subsitute windows, in my thoughts it doesn't matter if it works on ubuntu or not. no?

---

### Post by davmac on 2006-10-02
Mastercam looks like a CAD/CAM package. As long as it isn't trying to do anything too fancy with the graphics or demands any unusual input devices it should be OK under vmware. 

BTW: vmware doesn't substitute windows. From my limited understanding it takes the resources the host system has available and provides them to the guest OS - making it look as if it getting them directly from the machine itself. For example on my laptop I access the outside world with a wireless connection. To my windows session running under vmware it just looks like a standard ethernet connection - because that is how vmware presents an ubuntu resource to the guest.

---

### Post by cmaranhao on 2006-10-02
> **davmac said:**
> Mastercam looks like a CAD/CAM package. As long as it isn't trying to do anything too fancy with the graphics or demands any unusual input devices it should be OK under vmware. 

BTW: vmware doesn't substitute windows. From my limited understanding it takes the resources the host system has available and provides them to the guest OS - making it look as if it getting them directly from the machine itself. For example on my laptop I access the outside world with a wireless connection. To my windows session running under vmware it just looks like a standard ethernet connection - because that is how vmware presents an ubuntu resource to the guest.

exactly, mastercam is a CAD/CAM software, i will need it to complete my degree. i hope it works fine (yes, it has to use my graphics card)

i haven't tried the vmware yet (i am at university right now), maybe tonight (i bet i will have to ask for additional help:mrgreen: )

---

### Post by dmizer on 2006-10-02
with vmware, windows runs on an emulated pc that's based on ubuntu.

that is, a fake processor/memory/hardware is all software based through ubuntu.  so, while running windows in ubuntu, your computer must be able to handle computations from two machines at the same time.  so if you have a computer that's even a little slow, something with high graphical input/output is going to be difficult, and require a lot of ram (ex: as a general rule, graphically intensive gaming is not possible in windows emulated through vmware)

be sure that after you install windows, that you take the time to install the vmware tools.  also, you'll get better responses running windows in full screen mode rather than in windowed mode.

no harm in trying though.  give it a shot and let us know how it turns out.

---

### Post by Klaidas on 2006-10-02
> **ignorance said:**
> If vmware can subsitute windows, in my thoughts it doesn't matter if it works on ubuntu or not. no?

It can't.
Why not just use Windows programs on Windows?

---

### Post by Marsolin on 2006-10-02
You need [VMware Player]("http://linuxappfinder.com/package/vmwareplayer"), not [VMware Server]("http://linuxappfinder.com/package/vmwareserver"). It is available in the Ubuntu dapper and edgy repositories. I wrote an article that explains how to get set up for free. You can find it [here]("http://linuxappfinder.com/blog/switching_from_windows_to_linux_using_vmware_player").

---

### Post by anaconda on 2006-10-02
> You need VMware Player, not VMware Server. It is available in the Ubuntu dapper and edgy repositories. I wrote an article that explains how to get set up for free. You can find it here.

why??  
WMWare server is better, with it you can make the virtual machines and use them.
With Player you can just use pre-made virtual machines, but you can't create any...

I think the server is better.

---

### Post by Marsolin on 2006-10-02
I suggested it because [VMware Player]("http://linuxappfinder.com/package/vmwareplayer") is in the Ubuntu repositories and you don't have to worry about registration or serial numbers. It's easy to create a new image for VMware Player, just cut and paste some text and use [QEMU]("http://linuxappfinder.com/package/qemu") to create the disk image with a single command.

---

### Post by djsroknrol on 2006-10-02
Why have 2 programs...server is a better way to go...if you bridge the connection with your host OS, you can also access your files on your host computer.

This is a great link for setting up shop:

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

---

### Post by cmaranhao on 2006-10-02
> **davmac said:**
> If you go to [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) and register for serial numbers, then download the package. You need the "VMWare Server for Linux" .tar.gz file.

Open up a terminal window and navigate to the directory where you downloaded it, then type "tar -xvzf nameofthefile.tar.gz".

You also need the compilers and linux headers installed. In the terminal window type;

 sudo apt-get install build-essential linux-headers-`uname -r`

If you navigate into the new directory you'll see the instructions for completing the installation.

Once you've got it installed, fire it up and connect to the local doodah. Click on the "create new virtual machine" on follow the instructions.

Once you've done this, put the windows install CD in your drive and start the virtual OS. When you've finished installing Windows, in vmware, click on the tools "Install VM Tools" then in the virtual windows it'll appear as a CD, install the tools from the virtual CD.

Hope this helps,

Dave Mac

edit: forget it :mrgreen: dumb question as hell

[http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

---

### Post by cmaranhao on 2006-10-02
> If you navigate into the new directory you'll see the instructions for completing the installation.


i don't get what you mean by that.. i already done this:

tar -xvzf nameofthefile.tar.gz

and this

sudo apt-get install build-essential linux-headers-`uname -r`

what should i do now?

---

### Post by distroman on 2006-10-02
This is a pretty good howto if you ask me.
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Two things,,,

If you get this -
> Unable to untar the "/usr/lib/vmware/modules/source/vmmon.tar" file in the 
"/tmp/vmware-config0" directory.
you can just extract them yourself. 

> In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines] <-- /var/vm
I would suggest placing it in /home/username/SomeFolderName, but you clearly don't have to.

---

### Post by bulldog on 2006-10-02
Did use this HowTo a while ago and works perfect.

May be it's posted,then I'm sorry to do it again :D 

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by cmaranhao on 2006-10-02
i am so confused right now.. because i used a different method than the ones those links have.. the last thing i've done was this:

> maranhao@maranhao:~$ sudo apt-get install build-essential linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-headers-2.6.15-27 linux-kernel-headers make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libstdc++6-4.0-dev linux-headers-2.6.15-27
  linux-headers-2.6.15-27-386 linux-kernel-headers make
0 upgraded, 15 newly installed, 0 to remove and 3 not upgraded.
Need to get 19.8MB of archives.
After unpacking 127MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18 [1039kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1 [1407kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-27 2.6.15-27.48 [6906kB]
Get:4 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main libc6-dev 2.3.6-0ubuntu20 [2822kB]
Get:5 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-27-386 2.6.15-27.48 [857kB]
Get:7 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:8 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get:9 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main gcc 4:4.0.3-1 [5048B]
Get:10 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1471kB]
Get:11 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main g++-4.0 4.0.3-1ubuntu5 [2271kB]
Get:12 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main g++ 4:4.0.3-1 [1386B]
Get:13 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main make 3.80+3.81.b4-1 [286kB]
Get:14 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main dpkg-dev 1.13.11ubuntu6 [163kB]
Get:15 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) dapper/main build-essential 11.1 [6826B]
Fetched 19.8MB in 1m22s (239kB/s)
Selecting previously deselected package binutils.
(Reading database ... 81036 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27.
Unpacking linux-headers-2.6.15-27 (from .../linux-headers-2.6.15-27_2.6.15-27.48_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-27-386.
Unpacking linux-headers-2.6.15-27-386 (from .../linux-headers-2.6.15-27-386_2.6.15-27.48_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up linux-headers-2.6.15-27 (2.6.15-27.48) ...

Setting up linux-headers-2.6.15-27-386 (2.6.15-27.48) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
maranhao@maranhao:~$


i just don't know what do do next.. until now i've done two commands:

tar -xvzf nameofthefile.tar.gz where name of the file is the name of the file i downloaded from the vmware site

and this

sudo apt-get install build-essential linux-headers-`uname -r`

this last command i quoted above, now i don't know what to do. i am following these instructions (a forum member gave them in this topic and i will quote him ):

>  Originally Posted by davmac  View Post
If you go to [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) and register for serial numbers, then download the package. You need the "VMWare Server for Linux" .tar.gz file.

Open up a terminal window and navigate to the directory where you downloaded it, then type "tar -xvzf nameofthefile.tar.gz".

You also need the compilers and linux headers installed. In the terminal window type;

sudo apt-get install build-essential linux-headers-`uname -r`

If you navigate into the new directory you'll see the instructions for completing the installation.

Once you've got it installed, fire it up and connect to the local doodah. Click on the "create new virtual machine" on follow the instructions.

Once you've done this, put the windows install CD in your drive and start the virtual OS. When you've finished installing Windows, in vmware, click on the tools "Install VM Tools" then in the virtual windows it'll appear as a CD, install the tools from the virtual CD.

Hope this helps,

Dave Mac

as you can see, he says to navigate to the new directory.. but i don't know how to do that (TOTAL NOOB).. can you give me the additional commands to complete the instalation (i can do another one with those links but vmware takes a lot of space and setting 2 vmware's is not very smart on my part)

so, can you give me the commands?

---

### Post by gn2 on 2006-10-02
Recently I installed VMWare Server on PCLinuxOS.

Used KPackage manager to install the .rpm download.

Perhaps you could more easily install VMWare Server from the .rpm using an Ubuntu compatible Package Manager?

---

### Post by summoness on 2006-10-02
The easiest way to install and use vmware is to use automatix - plus u can install other software at the same time. I have been using the experimental version for edgy since I am using that ubuntu version and it works perfectly.VMPlayer is in automatix and then u just go to [www.easyvmx.com](www.easyvmx.com) to set up your virtual machine by filling in a few boxes that are all explained as u go and it gives u a zip file to download that u unzip and u are done.Open the player and select your .vmx file and install your os. :)

---

### Post by cmaranhao on 2006-10-05
i haven't installed vmware yet (i tried a couple of ways and all those failed).. recently i found this in the howto section:

>  How to install VMWare WorkStation

    * Read #General Notes 

sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install make
sudo apt-get install g++
tar xzf VMware-workstation.tar.gz -C /tmp
cd /tmp/vmware-distrib
sudo ./vmware-install.pl
sudo ./vmware-config.pl -c

    * Now you can run Vmware by typing at the command line 

/usr/bin/vmware

    * Note: VMware Workstation installs also the VMware Player so these steps are only needed if you don't have a VMware Workstation license. 

i want someone to answer these questions before i make another attempt (i don't want to get my hard drive full of vmware's](*,) like it already is)

1)if i copy and paste those command lines, will vmware be ready to use or will i have to write more lines??

2)i already have the password so, where should i put the password if i install vmware through those command lines?

3)i want to run vmware through applications menu, can i make a link using alacarte?

4)will any future update mess with vmware?i know some guys over here had their vmware not working after some update.

---

### Post by davmac on 2006-10-06
1) This looks ok and from memory is close to how I installed vmware server (not workstation). BTW: If you've already installed build-essential on line 1 then lines 2 and 3 are redundant.

2) Do you mean the registration key? If so, it asks for it when you're running the install script (vmware-install.pl)

3) It just appeared on my applications>system tools menu. You may need to type "killall gnome-panel" to refresh your menu, or log out and back in again. 

4) Unlikely that a future update will mess with vmware but it may update something vmware depends on and cause problems that way.

Dave Mac

---

### Post by dmizer on 2006-10-06
> **davmac said:**
> 4) Unlikely that a future update will mess with vmware but it may update something vmware depends on and cause problems that way.
every time there is a kernel update you will need to run vmware-install.pl again.

---

### Post by cmaranhao on 2006-10-06
just a quick note before i start installing this.. i received an email with passwords for vmware.. but notice this:

i have like 50 passwords, do i input one at my will? i mean, can i choose any password?

---

### Post by gn2 on 2006-10-06
Yes, the passwords are for multiple virtual machines, and you can even pass them on to your friends.

---

### Post by cmaranhao on 2006-10-06
thanks mate.. i will try to install this then.

if i mess the instalation, is there a way to remove what i've done? i already have made enough crap the other times :mrgreen:

---

### Post by gn2 on 2006-10-06
What I did with this when I installed it on a different distro (PCLinuxOS withkPackage Manager) was to keep a note of the installed packages as I went, and when I fudged it up I used Synaptic to un-install the packages.

I downloaded the vmware server .rpm and used KPackage Manager as I said, and it was all pretty much point and click stuff...
I think there's a similar Gnome gDebi? package manager in the Ubuntu repositories.

I'm certainly not an expert Linux user, but I managed it OK, just need to get the sound working in it now.....

---

### Post by cmaranhao on 2006-10-06
what is the difference between vmware server and workstation?

because in the dapper howto i can install both of them..

---

### Post by AndyCooll on 2006-10-06
This thread [HOWTO: Windows (XP) on Ubuntu with VMware Server]("http://www.ubuntuforums.org/showthread.php?t=183209") explains it all. Just copy and paste the commands. Works great.

Just a further thought ...has anyone mentioned to you yet that VMware doesn't use your own graphics card settings? It uses the default "dummy" ones built in to the VMware software, and these are bog standard. Hence, anything that requires 3D graphics are pretty much a no no with VMware, e.g. games.

:cool:

---

### Post by AndyCooll on 2006-10-06
> **cmaranhao said:**
> what is the difference between vmware server and workstation?

because in the dapper howto i can install both of them..

Very little difference in truth (less flexibility with snapshots apparently). However Workstation is the paid for version, Server and Player are free (as in beer).

:cool:

---

### Post by cmaranhao on 2006-10-06
if the workstation is the paid version that means i cannot install it, i haven't plaid for anything.. i will go with the link andycool provided and install server instead..

if i have problems i will have to ask you guys.:mrgreen: 

thanks for your input 8)

edit: what if i install vmware player through synaptic? (being a newbie, synaptic is much easier)

should i just go with vmware player? (what do you mean by "less flexibility with snapshots apparently" )

---

### Post by AndyCooll on 2006-10-06
> **cmaranhao said:**
> what if i install vmware player through synaptic? (being a newbie, synaptic is much easier)

should i just go with vmware player? (what do you mean by "less flexibility with snapshots apparently" )

I would take the plunge ...and install Server. It'll be worth it in the long run. The link I gave you explains everything very well, and if you follow it closely and slowly you'll be fine.

A "snapshot" is an advanced tool where VMware makes a copy of your image at a particular moment. So if you then hose your image, you can then always delete that and return to the snapshot you took earlier. Workstation enables you to keep multiple snapshots, whereas Server limits you to one.

:cool:

---

### Post by cmaranhao on 2006-10-06
ok, you convinced me.. i will go with your link.if i have trouble i will ask you :p 

(its just that i already had so many problems with vmware in the past days, i am afraid to mess up one more time)

edit: in that link, the guys who made the topic says, at a certain point "breezy users only"

what does he mean by that? i am a total newbie, should i skip that line?

---

### Post by AndyCooll on 2006-10-06
"Breezy" was the name for the previous version of Ubuntu (5.10), just as Dapper is the name for this current version (6.06).

So, provided you are running the latest version ...yes, you should skip it. 

:cool:

---

### Post by cmaranhao on 2006-10-06
the instalation went well until this part:

> The path "/home/maranhao/vmware/doc" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] yes

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.


what happened? i need additional help

---

### Post by gn2 on 2006-10-06
Difference between server and player, is that server will let you install an OS into a virtual hard drive.

Player will run pre-configured "Appliances" which are images of working OS's and these can be downloaded from VMWare website.
Server is vastly more flexible.

re install problems, are you logged in as an ordinary user?

When I installed on PCLinuxOS it was as Root.

---

### Post by cmaranhao on 2006-10-06
i will try as root then. i don't know much but, when i need to be root i always type

sudo su

is this correct?

---

### Post by gn2 on 2006-10-06
Yes, but I find it easier to log in as super-user, make install changes with Synaptic Package Manager then log back in as normal user.

---

### Post by jnicita on 2006-10-15
yop, any luck with the sound. I have installed it on about 5 machines that were dells and hp's. The sound worked right out of the install. Now Im trying to isntall it on a box that has a cmedia 6 channel sound card. and its now not working with the autodetect sound card, any suggestions?

---

