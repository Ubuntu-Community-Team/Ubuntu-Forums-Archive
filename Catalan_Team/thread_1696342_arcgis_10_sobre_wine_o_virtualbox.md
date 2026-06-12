---
title: "arcgis 10 sobre wine o virtualbox?"
date: 2011-02-27
forum: Catalan Team
---

### Post by abosch on 2011-02-27
Bones!
Tinc el wine a l'Ubuntu 9.10. VUll instal·lar-me l'ArcGis 10 i l'últim pas no em deixa. 
Sabeu si és xq s'ha de tenir el virtualbox? o necessito windows per alguna cosa?

Merci!

[usuari proper al registrat]

---

### Post by abosch on 2011-04-01
No ho he acabat solucionant de la millor manera, però enganxo informació que m'ha ajudat per clarificar conceptes i saber una mica *per on em movia* sistema virtual, wine ... per si pot ajudar a algú.



> achoo02   
Ubuntu Extra Shot
Join Date: Aug 2006
Location: Tampa, FL
Beans: 394 
Re: ArcGIS on VirtualBox 

Programs cannot be run "from VirtualBox". VirtualBox is virtual machine software that will allow you to install a guest operating system within VBox...a 'system within a system' if you will.

For any Windows program to run, you will need to install Windows XP (or whatever flavor of Windows you want) on the virtual machine. Once XP is installed within VBox, any Windows progam installed within the virtual machine will run as if XP was installed on bare metal (with the exception of programs with heavy 3D graphics, but that's changing as well).

BTW...I have ArcGIS 9.2 installed on my virtual instance of XP, and it works just fine. A little slower than if XP was native...but that's to be expected.
________________

Objekt  
Dipped in Ubuntu
Join Date: Oct 2007
Beans: 581 
Ubuntu 10.04 Lucid Lynx 

Re: Virtualizing Windows on Ubuntu 

Outline of how virtualization works:

-You boot your installed OS, Ubuntu. This is called the "host" in virtualization terminology.

-Once Ubuntu is loaded, you run some sort of virtualization program. 

-With the virtualization program, e.g. VMWare, you load the virtual Windows Vista machine. This is the "guest" system.

-You do whatever you need to do in the guest system. For example, run your GIS application.

So, there is never a choice of which one to boot. You will always boot Ubuntu first. There is no other operating system installed on your real, physical machine - Vista is only virtual.

If that still doesn't make sense, it will once you do it. Doesn't matter whether you use Virtualbox or VMWare, they work pretty much the same once you have them set up. 

One thing to keep in mind: The virtual machine (guest) will not have direct access to your computer's hardware. It will use a simulated video card, sound hardware, etc. Virtualbox has some rudimentary 3D support, but I don't know about VMWare. Not sure how well 3D works in either. So far I haven't had any luck in Virtualbox. 3D apps either refuse to run, or have weird glitches when they do run (mouse uncontrollable for example).
_________________

mister_playboy  
Ubuntu Extra Shot
Join Date: Feb 2009
Location: Nebraska, USA
Beans: 374 
Ubuntu 10.10 Maverick Meerkat 
Re: Virtualbox for 9.10 

The host and guest OSs can share files via "Shared Folders" after you have installed the guest additions.

VirtualBox comes with a very useful instruction manual... it will guide you through the process. 
__________________________

fernandoch  
5 Cups of Ubuntu
Join Date: Nov 2006
Beans: 40 
Re: Ubuntu 10.10 64 bits and virtualbox 

Thank you guys, but what I did was to remove all libqt4* packages and did the apt-get install virtualbox again and it worked like a charm.

As I said before, never had this problem before...

Thank you all again!
________________

Tutorial VirtualBox a doc.ubuntu-es ...

[http://doc.ubuntu-es.org/Virtualbox](http://doc.ubuntu-es.org/Virtualbox)
__________________

_0R10N  
Way Too Much Ubuntu
Join Date: Apr 2010
Beans: 316 
Ubuntu 10.04 Lucid Lynx 
Re: VirtualBox installation 

You should download the virtualbox-3.1 package from the repositories, adding previously the finger-print given at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

I recommend this, because versions who don't require finger-print, lack of several features like USB support.

Kind regards!

_0R10N >>
______________________

ltipto1  
First Cup of Ubuntu
Join Date: Apr 2009
Location: Savannah, Georgia, USA
Beans: 8 
Ubuntu 9.10 Karmic Koala 
VirtualBox 3.0 problems on Ubuntu 9.10 ... 

I installed VirtualBox and discovered that the OSE version doesn't include USB support. I used Ubuntu Software Center to remove the program. I then jumped through the hoops to install the right repository and installed VirtualBox 3.0 CSE which DOES support USB. However, when I try to run it I get an error:

"Kernel driver not installed (rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

I'm a noobie, and don't know what to do from here... Any suggestions...
___________________

aitjcize  
5 Cups of Ubuntu
Join Date: Aug 2008
Beans: 15 
Re: VirtualBox 3.0 problems on Ubuntu 9.10 ... 

Quote:
Originally Posted by ricardo.gloe 
Open a terminal (Applications,Accessories).

Type: sudo /etc/init.d/vboxdrv setup

Wiat until it finishes and then you should be able to open your vm's.

Probably the next time you boot, you'll get the same error and have to repeat this process. 


I have the exact same problem and still haven't found the permanent solution.
I think it's because of the new Upstart
dmesg | grep VirtualBox
=> Nothing...

vboxdrv is not load at startup
just type:
sudo /etc/init.d/vboxdrv start

you don't have to compile it again...
________________________

manolomanolo 
Way Too Much Ubuntu
Join Date: Apr 2007
Beans: 295 
Ubuntu 10.04 Lucid Lynx 
Re: VirtualBox / Karmic 

Quote:
Kernel driver not installed (rc=-190

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary. 
As the error message says, you must install DKMS package first and then executing 'vboxdrv setup'.

So, please try and run
Code:
sudo apt-get install dkms
and then
Code:
sudo /etc/init.d/vboxdrv setup
it worked for me 
_________________

EricDrijv  
5 Cups of Ubuntu
Join Date: Dec 2009
Location: Netherlands
Beans: 27 
Ubuntu 9.10 Karmic Koala 
Re: VirtualBox / Karmic 

Sometimes Virtualbox.org doesn't work in Karmic
First do a sudo apt-get remove virtualbox-3.1
You can install the Virtualbox from Sun it always works
[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)
________________

Virtualbox vs partition

[http://ubuntuforums.org/showthread.php?t=1285693&highlight=virtualbox+arcgis+10](http://ubuntuforums.org/showthread.php?t=1285693&highlight=virtualbox+arcgis+10)
__________________


---

