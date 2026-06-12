---
title: "VMware player"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-12-08
How can i run an os in VMware player

It only recognizes the vmx format

How can i run an iso on it???

---

### Post by deadgobby on 2006-12-08
I saw this on Ubie's wiki site
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=VMware&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=VMware&titlesearch=Titles)

---

### Post by pay on 2006-12-08
Here is where you can download images. [http://www.vmware.com/vmtn/appliances/directory/](http://www.vmware.com/vmtn/appliances/directory/)
vmware player isn't capable of making your own images though. However you can make your own with vmware-server (which is free aswell).

---

### Post by Hendrixski on 2006-12-08
I use VMWare server, and I love it.  I hear only bad things about the player.

---

### Post by fasoulas on 2006-12-08
OK thnx for ur relpies

I installed vmware player from automatix2 and now i will unintall it and i want to install vmware player that can run iso files as some of you said correct me if i have wrong

Can someone post me the commands to install vmware server??

---

### Post by civic_si on 2006-12-08
if you are using the GUI then just go to 

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

and go through the download once down loaded you can

tar -xfzv VMware-server-1.0.1-2996.tar.gz

then cd vmware-server-distrib

sudo ./vmware-install.pl

the script will ask a bunch of questions I just accepted the defaults.
The script did not make a icon for me so i made my own but you can just hit
alt and f2 to use the run command and type vmware-server

and then you can make your own Virtual Machines

---

### Post by fasoulas on 2006-12-08
BUT accuming that i have downloaded the ubuntu 6.10 as an iso image how can i run it from vmware server

---

### Post by derjames on 2006-12-08
You can use easyvmx to create the virtual machine

[www.easyvmx.com](www.easyvmx.com)

'qemu' can also create the files...

however why don't you choose VMWARE server instead VMware player... the former gives you more options (you can create the VMX files)and is also free...

cheers

---

### Post by aysiu on 2006-12-08
I've found this guide helpful:
[http://www.linuxforums.org/applications/using_vmware_player_to_test_linux_distributions.html](http://www.linuxforums.org/applications/using_vmware_player_to_test_linux_distributions.html)

---

### Post by derjames on 2006-12-08
> **fasoulas said:**
> BUT accuming that i have downloaded the ubuntu 6.10 as an iso image how can i run it from vmware server

Go to virtual machine -> settings

then select CD rom from the list

on the right side select USE ISO IMAGE

push browse and selectd the file you downloaded...

turn on the virtual machine and it will boot from the CD...

hope this helps

---

### Post by fasoulas on 2006-12-09
I have downloaded these packages :

VMware Server for Linux
Management Interface.

from [http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

Now can someone explain to me how can i install the vmware server ???

I was trying all day to find how but i couldn't understand because i am new to these things 

So can someone explain how to do it in simple english??

I have to say that i installed vmware player from automatix and after i unintalled it to put vmware server 
BUT 
after a search in synaptic i found that some modules are still there 
(vmware-player-kernel modules,xserver xorg driver vmware e.t.c)

Should i remove them pls help me

---

### Post by ZERO_SHIFT on 2006-12-09
May I suggest the open sourced alternaive to VMware, Qemu.

You can install it through Synaptic.

---

### Post by fasoulas on 2006-12-09
> **ZERO_SHIFT said:**
> May I suggest the open sourced alternaive to VMware, Qemu.

You can install it through Synaptic.

But with qemu can i run other operating systems while they rae in iso files??

---

### Post by useResa on 2006-12-09
> **fasoulas said:**
> I have downloaded these packages :

VMware Server for Linux
Management Interface.

from [http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

Now can someone explain to me how can i install the vmware server ???

I was trying all day to find how but i couldn't understand because i am new to these things 

So can someone explain how to do it in simple english??

I have to say that i installed vmware player from automatix and after i unintalled it to put vmware server 
BUT 
after a search in synaptic i found that some modules are still there 
(vmware-player-kernel modules,xserver xorg driver vmware e.t.c)

Should i remove them pls help me

The way to install VMWare has been mentioned by civic_si in post #6 of this thread. After you have downloaded the file, open a terminal.

Go to directory where you have downloaded the file and enter the following```
 tar -xfzv VMware-server-1.0.1-2996.tar.gz
```
(Replace the filename if your filename is different ;))
If it has completed unpacking the file, type the following```
cd vmware-server-distrib
```
This directory is created when the file is unpacked.
Finally type the following```
 sudo ./vmware-install.pl
```

> **civic_si said:**
> The script will ask a bunch of questions I just accepted the defaults.

The script did not make a icon for me so i made my own but you can just hit alt and f2 to use the run command and type vmware-server
and then you can make your own Virtual Machines
As far as I remember an icon was created in my case under "Applications --> System Tools", but maybe I am wrong.

Finally I like to add that I really like VMWare Server!
It provides a great opportunity to try different distro's or new releases (for example this reply is made in a VM running Feisty :D)
Furthermore I have Windows XP running in a VM (required because of my work) and in another VM I have PCLinuxOS. All (except WinXP) installed using downloaded .iso files.

---

### Post by fasoulas on 2006-12-09
i can't understand what you mean by saying from this point

Go to directory where you have downloaded the file and enter the following
Code:

tar -xfzv VMware-server-1.0.1-2996.tar.gz

(Replace the filename if your filename is different )
If it has completed unpacking the file, type the following
Code:

cd vmware-server-distrib

This directory is created when the file is unpacked.
Finally type the following
Code:

sudo ./vmware-install.pl

WHAT DO YOU MEAN be saying 
Go to directory where you have downloaded the file and enter the following

the files i have downloaded is on the desktop with the name

VMware-server-1.0.1-29996.tar.gz

---

### Post by useResa on 2006-12-09
> **fasoulas said:**
> i can't understand what you mean by saying from this point

Go to directory where you have downloaded the file and enter the following
Code:

tar -xfzv VMware-server-1.0.1-2996.tar.gz

(Replace the filename if your filename is different )
If it has completed unpacking the file, type the following
Code:

cd vmware-server-distrib

This directory is created when the file is unpacked.
Finally type the following
Code:

sudo ./vmware-install.pl

WHAT DO YOU MEAN be saying 
Go to directory where you have downloaded the file and enter the following

the files i have downloaded is on the desktop with the name

VMware-server-1.0.1-29996.tar.gz

Open a terminal via Applications-->Accessories-->Terminal
Since you have downloaded the file to the desktop type after the prompt```
cd ~/Desktop
```

The prompt will now show your name, followed by ":~/Desktop$"

Next type after the prompt```
 tar -xfzv VMware-server-1.0.1-2996.tar.gz
```
This will unpack (unzip if you will) the file and create a folder called "vmware-server-distrib". (You can see this folder on your desktop)

When the prompt is back, you can go to this folder by typing```
cd vmware-server-distrib
```
The prompt will now show your name, followed by ":~/Desktop/vmware-server-distrib$".

Finally, to install vmware server you type after the prompt```
 sudo ./vmware-install.pl
```
The sudo is required since you should install this program as root.

Hope this helps you.

---

### Post by fasoulas on 2006-12-09
A previous installation of VMware software has been detected.

Failure

Execution aborted.


Thnx for the info useResa 

but mow i see this.Maybe it is because i have previously installed vmware player 

Any Help?

By the way what i was trying to achive all day with vmware i have done it with qemu in just five minutes 

But it is a good way to get expirienced!!!

What are the differences between qemu and vmware?

---

### Post by useResa on 2006-12-09
> **fasoulas said:**
> A previous installation of VMware software has been detected.
Failure
Execution aborted.

Thnx for the info useResa 
but mow i see this.Maybe it is because i have previously installed vmware player
Based on the error you are getting I  guess you are right

> **fasoulas said:**
>  Any Help?
I would remove all vmware related packages and then try the installation again

> **fasoulas said:**
>  By the way what i was trying to achive all day with vmware i have done it with qemu in just five minutes 

But it is a good way to get expirienced!!!

What are the differences between qemu and vmware?
I don't know qemu and have never tried it, so I can't answer this for you. I never experienced any problems, but I have always used VMWare Server.
Glad that I could somewhat help you. And maybe ... try VMWare Server another time?

---

### Post by ZERO_SHIFT on 2006-12-10
I strongly recommend Qemu. I personally tried it and it worked perfectly.

I used Qemu because I came across the same problem with VMWare.

I tried running Windows XP Pro on Dapper and it worked.(But no Sound)

I also recommend installing Qemu launcher after you install Qemu.

This thread might come in handy.

[http://ubuntuforums.org/showthread.php?t=187413&highlight=qemu](http://ubuntuforums.org/showthread.php?t=187413&highlight=qemu)

Good Luck.

---

### Post by fasoulas on 2006-12-11
> **ZERO_SHIFT said:**
> I strongly recommend Qemu. I personally tried it and it worked perfectly.

I used Qemu because I came across the same problem with VMWare.

I tried running Windows XP Pro on Dapper and it worked.(But no Sound)

I also recommend installing Qemu launcher after you install Qemu.

This thread might come in handy.

[http://ubuntuforums.org/showthread.php?t=187413&highlight=qemu](http://ubuntuforums.org/showthread.php?t=187413&highlight=qemu)

Good Luck.
Thnx for thew info but what is Qemu launcher?

---

### Post by ZERO_SHIFT on 2006-12-11
> **fasoulas said:**
> Thnx for thew info but what is Qemu launcher?

Qemu launcher is an application that eases the use of Qemu **_however it is not required to run Qemu_**

Post your progress with Qemu.

---

### Post by ZERO_SHIFT on 2006-12-14
This is a pic of SuSE Linux Enterprise Desktop(SLED) 10 running on top of Edgy.

[http://photos1.blogger.com/x/blogger/5685/2610/400/400936/Screenshot-1.png]("http://photos1.blogger.com/x/blogger/5685/2610/400/400936/Screenshot-1.png")

I will post a Qemu How-To soon. So keep tuned.

---

### Post by fasoulas on 2006-12-15
> **ZERO_SHIFT said:**
> This is a pic of SuSE Linux Enterprise Desktop(SLED) 10 running on top of Edgy.

[http://photos1.blogger.com/x/blogger/5685/2610/400/400936/Screenshot-1.png]("http://photos1.blogger.com/x/blogger/5685/2610/400/400936/Screenshot-1.png")

I will post a Qemu How-To soon. So keep tuned.

ok thnx for ur attension
be the way the link with the foto u posted here is not showing it says error 403

I wonna ask something 
i downloaded qemu from the synaptic but i want the latest release that supports something like a plugin for the i386 prossesors that makes qemu runs faster 
have u heard of it???

How can i download the latest release?

---

### Post by AndyCooll on 2006-12-15
> **ZERO_SHIFT said:**
> I strongly recommend Qemu. I personally tried it and it worked perfectly.

I wouldn't necessarily recommend Qemu. Whenever I have tried to install it, I've had nothing but grief (though this is possibly simply my own experience).  Installing Qemu has worked ok, but installing the accelerator (which isn't open-source) hasn't.

And that brings me to one of the main issues, Qemu is noticeably slower than VMware.

Here is an excellent copy and paste guide to installing VMware Server: [HowTo: Windows (XP) on Ubuntu with VMware Server]("http://www.ubuntuforums.org/showthread.php?t=183209")
It also shows you the principles of creating VMware images (in this case XP) and howto resolve common problems.

:cool:

---

