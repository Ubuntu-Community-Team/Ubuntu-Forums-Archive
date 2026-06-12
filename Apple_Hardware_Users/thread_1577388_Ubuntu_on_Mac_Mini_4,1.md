---
title: "Ubuntu on Mac Mini 4,1"
date: 2010-09-18
forum: Apple Hardware Users
---

### Post by Shii0 on 2010-09-18
Hi,
I'm trying to install Ubuntu 10.10 server beta (since it have kernel that supports new chipset in mac mini) as only OS to run several low utilization VMs.
So far I was able to install it without a problem, both controller and network is working fine.
Problem happens after the installation during 1st boot. Message is showed ([drm]... impossible to read) and within a second monitor will turn off.
I have booted with install dvd but there is no error in logs on system, after drm messages it continues to network setup.
I would suspect gpu drivers, but as its server edition and installation was working fine its probably not the case unless there is some change in newest server edition that requires gpu.
Does anyone encounter same issue or have any idea how to fix it?

---

### Post by logandzwon on 2010-09-20
Hi Shii0,
  You have the same idea I do.  How did you get ubuntu on there at all, did you get the usb DVD?

---

### Post by Shii0 on 2010-09-20
> **logandzwon said:**
> Hi Shii0,
  You have the same idea I do.  How did you get ubuntu on there at all, did you get the usb DVD?
I bought standard version of mac mini with 8GB ram so I have build in DVD. HDD space is more then sufficient for my use since I will be using external storage and storage exported from other servers.
But boot from usb should not be problem trough rEFIt, I have tried it with usb key out of curiosity, but I dont plan to use rEFIt at all.
If you have server version of mac mini, you could also boot into osx and make 2nd disk/one of partitions into bootable installation. I have not tried it, but thats how bootcamp works after all.

---

### Post by logandzwon on 2010-09-20
Thanks for the info Shii0,

My plans are a little different.
I'm trying to use the built-in dual HD as a raid 0 for speed.
I do not want the OS X on the machine at all because I want to run the included OS X Server in a VM.

I made an Apple bootable USB stick with 10.04.1 daily, but it run into an issue when it came to installing GRUB on the MBR.

---

### Post by Shii0 on 2010-09-20
> **logandzwon said:**
> Thanks for the info Shii0,

My plans are a little different.
I'm trying to use the built-in dual HD as a raid 0 for speed.
I do not want the OS X on the machine at all because I want to run the included OS X Server in a VM.

I made an Apple bootable USB stick with 10.04.1 daily, but it run into an issue when it came to installing GRUB on the MBR.
Is it really Mac mini 4.1? With 10.04 it did not even found disks for me.
Kernel 2.6.35 is needed for mcp89 chipset used in mac mini 4.1.
I have used this one:
ubuntu-10.10-beta-server-amd64.iso

---

### Post by donnib on 2010-09-29
> **Shii0 said:**
> Hi,
I'm trying to install Ubuntu 10.10 server beta (since it have kernel that supports new chipset in mac mini) as only OS to run several low utilization VMs.
So far I was able to install it without a problem, both controller and network is working fine.
Problem happens after the installation during 1st boot. Message is showed ([drm]... impossible to read) and within a second monitor will turn off.
I have booted with install dvd but there is no error in logs on system, after drm messages it continues to network setup.
I would suspect gpu drivers, but as its server edition and installation was working fine its probably not the case unless there is some change in newest server edition that requires gpu.
Does anyone encounter same issue or have any idea how to fix it?

Hi,
Did you find a solution for your problem ? 

donnib

---

### Post by Shii0 on 2010-09-30
> **donnib said:**
> Hi,
Did you find a solution for your problem ? 

donnib
no, I have already tried all possible ways found on internet and there was no change.
for now I have stored my mac mini away as I dont see any hope for it any time soon

---

### Post by linuxopjemac on 2010-10-01
[https://help.ubuntu.com/community/Macmini4-1/Lucid](https://help.ubuntu.com/community/Macmini4-1/Lucid)
might help

---

### Post by Shii0 on 2010-10-01
> **linuxopjemac said:**
> [https://help.ubuntu.com/community/Macmini4-1/Lucid](https://help.ubuntu.com/community/Macmini4-1/Lucid)
might help
yup, I seen that. there is different problem trough.
gpu driver issue just dont make sense since I'm using server edition with just shell. or do it?
well, even if it do, I cant compile and install drivers since I cant boot os.
everything else seems to be fine, network was working, there was just reboot issue but thats not that critical for me.

---

### Post by donnib on 2010-10-05
> **Shii0 said:**
> no, I have already tried all possible ways found on internet and there was no change.
for now I have stored my mac mini away as I dont see any hope for it any time soon

That sucks big time. Getting my mac mini server in two days, gotta find a way to run vm on it the most efficient way. I read somewhere on net that ubuntu can run but there is some boot option u need to set inorder to work.

---

### Post by Shii0 on 2010-10-06
> **donnib said:**
> That sucks big time. Getting my mac mini server in two days, gotta find a way to run vm on it the most efficient way. I read somewhere on net that ubuntu can run but there is some boot option u need to set inorder to work.
I found two articles claiming different boot options.
Tried both but they did not helped.
For now, I'm waiting for 10.10 release and will try again.

---

### Post by Shii0 on 2010-10-12
Just a small update, final version 10.10 have same issue.

---

### Post by spotspot on 2010-10-14
I have tried Desktop 32b 10.4.1, 10.10, and the 10.4 with updated kernel found here: [https://help.ubuntu.com/community/Macmini4-1/Lucid](https://help.ubuntu.com/community/Macmini4-1/Lucid)

Nothing works!  When it starts X the screen goes black.  I tried it with an analog monitor, and instead of black got a desktop but it was horribly distorted, with lots of horizontal and vertical vibrating lines.

---

### Post by anothergene on 2010-10-15
Has any had success with this mini, I'm considering one for a HTPC.  The things I am looking for specifically are:

XBMC
NVidia drivers and using the graphics card for decoding.
HDMI support with audio
Builting IR working with an Logitech Harmony Remote

Anything else?

---

### Post by Shii0 on 2010-10-15
I have successfully installed ubuntu server 10.10 64bit as kvm:
1. Install from DVD as normal + selected virtual machine server
2. Boot from DVD using "Rescue broken system" option, use hdd partition as root
3. apt-get update
4. add to default grub config: "nomodeset reboot=pci", update grub << fixes both black screen and reboot issue
5. eject dvd, restart normally
6. (optional) install ConVirt Free following guides:
"http://www.convirture.com/wiki/index.php?title=C2_ubuntu_installation"
"http://www.convirture.com/wiki/index.php?title=Patches_2_0"
"http://www.convirture.com/wiki/index.php?title=Convirt2_Installation#Preparing_Managed_Servers"

Only issue is that Convirt does not create xm files, but I did not had time to look into issue yet.

---

### Post by donnib on 2010-10-19
> **Shii0 said:**
> I have successfully installed ubuntu server 10.10 64bit as kvm:
1. Install from DVD as normal + selected virtual machine server
2. Boot from DVD using "Rescue broken system" option, use hdd partition as root
3. apt-get update
4. add to default grub config: "nomodeset reboot=pci", update grub << fixes both black screen and reboot issue
5. eject dvd, restart normally
6. (optional) install ConVirt Free following guides:
"http://www.convirture.com/wiki/index.php?title=C2_ubuntu_installation"
"http://www.convirture.com/wiki/index.php?title=Patches_2_0"
"http://www.convirture.com/wiki/index.php?title=Convirt2_Installation#Preparing_Managed_Servers"

Only issue is that Convirt does not create xm files, but I did not had time to look into issue yet.

Shii0: thanx for sharing this. I am looking exactly for something like that. I need my Mac Mini 2010 Server to act as VM Server. I will try to follow your guide when i get my Mac Mini back from repair since my disk were having bad blocks @ first day i got it :(
How can one take backup of the VM in convirt ? I see the enterprise version has backup support. What do you mean the Convirt does not create xm files ? Not knowing anything about convirt i don't know what xm files are for. I come from a VMWare world :)

---

### Post by Shii0 on 2010-10-19
> **donnib said:**
> Shii0: thanx for sharing this. I am looking exactly for something like that. I need my Mac Mini 2010 Server to act as VM Server. I will try to follow your guide when i get my Mac Mini back from repair since my disk were having bad blocks @ first day i got it :(
How can one take backup of the VM in convirt ? I see the enterprise version has backup support. What do you mean the Convirt does not create xm files ? Not knowing anything about convirt i don't know what xm files are for. I come from a VMWare world :)
Actually I think of giving up Convirt, cant see how they can call this enterprise solution.
Its really unreliable even for development/soho use. It often say successful when something fails, like creation of xm files, randomly refuse to start vm's and some features like forwarding vnc and snapshot does not work most of the time.

I'm looking into using Proxmox, but since it does not work correctly with ubuntu, I will have to switch to different one.

Backups will not work in free edition, but its always possible to set it up via kvm/xen cli.

xm files are "equivalent" to vmdk files. I fixed that, it was mistake in template.

---

### Post by jd_jedi on 2010-10-19
xm files are raw disk format. The xm extension comes from old XenMan legacy :) 

Shii0, you could use the ConVirt forums to get help on the issues you are running in to.

[http://www.convirture.com/forums](http://www.convirture.com/forums)

Thanks

---

### Post by Shii0 on 2010-10-19
> **jd_jedi said:**
> xm files are raw disk format. The xm extension comes from old XenMan legacy :) 

Shii0, you could use the ConVirt forums to get help on the issues you are running in to.

[http://www.convirture.com/forums](http://www.convirture.com/forums)

Thanks
True, but there are too many problems and I'm not paying customer nor I ever would be considering the price.
I need working solution, even temporary, without spending much time at this point, otherwise I would develop it myself.

---

### Post by donnib on 2010-10-20
> **Shii0 said:**
> True, but there are too many problems and I'm not paying customer nor I ever would be considering the price.
I need working solution, even temporary, without spending much time at this point, otherwise I would develop it myself.

I have good experience with VMWare server  ontop of Windows. U could give that a try. I might use that for my Mac mini. I used it for 2-3 years and never had an issue. I also saw proxmox and i see others have tried it on the Mac mini 4,1 without having big success

---

