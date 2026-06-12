---
title: "Ubuntu running withing windows"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by haricharan on 2007-02-16
Is there a possibility that i could boot up already installed ubuntu from withing windows like cygwin. This might sound stupid...but i just thought it would be great...since i can use my already existing settings and applications in ubuntu!!.. If i have to do it in vmware i can access only thru vmware....

---

### Post by HippyVanMan on 2007-02-16
I have the same question, but in reverse. I wish to use pre-installed XP, within ubuntu.

---

### Post by wh0rd on 2007-02-16
Maybe this is what you guys are looking for:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

### Post by HippyVanMan on 2007-02-16
It doesn't seem to tackle how to use an already installed OS, instead just tells us that we shoudl use OS images. But still helpful knowledge :D

---

### Post by haricharan on 2007-02-16
> **HippyVanMan said:**
> I have the same question, but in reverse. I wish to use pre-installed XP, within ubuntu.

Yeah vice-versa would be even better!!....:)

---

### Post by ashmew2 on 2007-02-16
Hi people , does the following link help u to sort out your problems ,?
[I havent tried it out  , i was just googling a few weeks back and bookmared it in case i needed it sometime)

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

I think it helps u run an Existing Windows Installation with UBuntu.. ENjoy

---

### Post by bodhi.zazen on 2007-02-16
I am not sure about pre-installed because these are all emulators ...

But check out vmware :

[http://doc.gwos.org/index.php/VMWare_WindowsXP](http://doc.gwos.org/index.php/VMWare_WindowsXP)

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

[http://www.ubuntuforums.org/showthread.php?&t=342631](http://www.ubuntuforums.org/showthread.php?&t=342631)

[http://www.ubuntuforums.org/showthread.php?&t=361528](http://www.ubuntuforums.org/showthread.php?&t=361528)

---

### Post by ellis rowell on 2007-02-16
It doesn't seem logical to me that you can run two OS's at the same time. I use both Windows and Ubuntu, but separately. I have two HDD's and plug in one or the other. I am thinking of using a two way/two pole switch to change over the positive leads to one or the other.

---

### Post by ashmew2 on 2007-02-16
> **ellis rowell said:**
> It doesn't seem logical to me that you can run two OS's at the same time. I use both Windows and Ubuntu, but separately. I have two HDD's and plug in one or the other. I am thinking of using a two way/two pole switch to change over the positive leads to one or the other.

If u mean its not possible then u shud know it is with WIn4Lin Pro or VMWARE , etc , etc u can run "Virtual Machines" with OSs installed so they will work like any other normal OS (a lil slower and lacking some features like 3d).

If u mean its not worth a try , consider some software that are your favourites on WIndows but u cant just run em on UBuntu even by using wine/Cedega etc , so u can still say good bye to the default windows installation and use your favourite software.

LOl if im wrong , please let me know

---

### Post by haricharan on 2007-02-16
> **ashmew2 said:**
> [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)
Thanks for the link.....the link seems to be promising...let me try it!...;)

---

### Post by ashmew2 on 2007-02-16
@bodhi.zazen

All the links you posted are for running a VMware machine and INSTALL windows on it AFTER installing the Virtual Machine.Isnt it ?

---

### Post by ashmew2 on 2007-02-16
Let me if it works man :D

---

### Post by chrish670 on 2007-02-17
Using the procedure in the Links on Page 1 ... went pretty much without a hitch on my Desktop.  I'm running XP professional SP-2, and didn't wish to install ubuntu directly to my physical harddrive, so using a virtual machine gave me some options.   It was kind of a confusing thing at first during installation, however, because I was seeing a "no Vmware is installed on this computer " warning in lower left side of screen.  I think I may have goofed up my virtual hardrive... I'm not sure.   Vmare loads at start with Linux, but then the picture gets a little distorted until you get onto the login screen to enter your username and password.  Other than that, its installed and works great.

---

### Post by haricharan on 2007-02-18
The link [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html") works fine, except while running Vmplayer you have to do it as root. I was able to see the grub menu and i chose Windows and Windows loads up....but asks me to activate Windows. I tried doing but it says incorrect activation key. I guess it identifies this as another installation of Windows and if I use the same key it says the key is not valid. I have to fix this problem. I shall look into it a lil later.

---

### Post by haricharan on 2007-02-18
Another thing is is if select any of my Ubuntu Versions it corrupts my ext3 partitions and i had to run fsck to fix the file system errors.....

---

### Post by ashmew2 on 2007-02-18
Since you own the copy of Windows , couldnt u use some sort of patch ? I dont think that'll be illegal..

---

### Post by haricharan on 2007-02-24
nope..doesnt work for me..windows loads up but asks for activation and i cudnt activate it either....now when i boot windows normally too it asks for activation..so i had to restore it to previous settings from safe mode....it would be better if i could read the details in vmdk and vxm....i think i could modify something out there...

---

### Post by irish_flu on 2007-02-24
The reason you're getting that is because Windows thinks it's running somewhere other than it was the last time you booted it directly.

VMWare is emulating hardware, and Windows can't help but see that as different hardware than the machine it expected to find (just like if you removed your Windwos drive and popped it into a different computer).

As you probably already know, if Windows XP sees several hardware changes, it wants to be "activated" all over again.  However, since you've already "activated" that serial number once you're gonna have to call Microsoft in order to re-activate it.

FYI, If your copy of XP is an "OEM" copy (as in, the case says something like "for a new Dell computer only", or if the only copy you have is a manufacturer's restore disk)" then Microsoft might not re-activate it (I've heard stories of it going both ways).

---

### Post by haricharan on 2007-02-25
yeah i know and mine is an OEM copy too....so there is no chance of doing it i guess...i might upgrade my Windows XP from Home to Professional later....maybe i could give it a try at that time...

---

