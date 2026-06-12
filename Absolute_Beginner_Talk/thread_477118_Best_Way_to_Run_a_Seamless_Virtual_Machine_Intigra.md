---
title: "Best Way to Run a Seamless Virtual Machine Intigration"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-18
I'm having a touch time making up my mind for a virtual machine. I heard VirtualBox was great, but 
Number one: 
I live on a college campus and I can't REALLY manipulate my network (I heard there was network tweaking involved)
Two:
Can't find any seamless integration tutorials for Feisty

Can anyone help out?

---

### Post by bodhi.zazen on 2007-06-18
Here is a how-to on VirtualBox : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

And Seamless Integration : [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

VMWare is more stable and has been around longer :


[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

Or if you want open source there is qemu. qemu is going to be slower ...

qemu : [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

The "networking" involved to allow seamless integration is between guest and host and you have control over that. Take a peek at the how-to and let us know if you have questions.

---

### Post by suhanduman on 2007-06-18
Actually Qemu is a little bit different.
Because it can emulate cpu.
You can emulate sparc on inter for example.

For a simple virtual machine, i am using vmware server for years.
It's free and very stable.

---

### Post by bodhi.zazen on 2007-06-18
> **suhanduman said:**
> Actually Qemu is a little bit different.
Because it can emulate cpu.
You can emulate sparc on inter for example.

For a simple virtual machine, i am using vmware server for years.
It's free and very stable.

:lolflag: 

True, true,

I threw it out there as an open source option, some folks prefer those.

There is an open source option for Virtual Box as well ....

But, I agree, I would advise VMWare server. VirtualBox is under rapid development and it is both fun and new (not to mention easy to user), but I have had some stability problems.

---

### Post by dannymichel on 2007-06-18
So VMWare is the way to go?

---

### Post by bodhi.zazen on 2007-06-18
> **dannymichel said:**
> So VMWare is the way to go?

If you want something stable and reliable, yes

If you want to try something new and are willing to accept the fact it is in development (and thus may not be as reliable yet) go with VirtualBox.

qemu is only if you are determined to use an open source solution and want stability ...

---

### Post by dannymichel on 2007-06-18
What is a "SEAMLESS" integration anyway?
I just installed Vista on VMWare.
What can I do to make this more "SEAMLESS"?

---

### Post by jcronkhite on 2007-06-18
I guess you should install the guest tools, or guest additions (whatever they're called) on the VM.  It will launch an installer inside Windows (VM) which adds better video support, SEAMLESS mouse integration (you can move the mouse in and out of the VM window without being locked in the VM window), and other driver support.  I highly recommend this.  I'm currently using VirtualBox and it's been great.  Also, used VMWare and liked it as well.

---

### Post by dannymichel on 2007-06-18
Everything is running slow.
I have no internet connection in Windows 
and I can't set my display size to 1440x900

Do I need to install my video card and ehternet card as I would if I were running a regular Vista install?
I have no idea where to start.

Any ideas?
[[IMG]http://farm2.static.flickr.com/1367/566954322_a7b6b1ea39.jpg?v=0[/IMG]]("http://farm2.static.flickr.com/1367/566954322_a7b6b1ea39_b.jpg")

---

### Post by whistle on 2007-06-18
Well first you could install VMware tools - it says you don't have it installed yet.  Then you could hide your illegal Mac OS torrents before you take a screenshot ;)... well actually, the torrent isn't *illegal*. My bad :D

edit: I'm going to try and get a seamless XP going in Feisty w/ VMware... I'll let you know how it goes, if you want.

---

### Post by dannymichel on 2007-06-18
> **whistle said:**
> Well first you could install VMware tools - it says you don't have it installed yet.  Then you could hide your illegal Mac OS torrents before you take a screenshot ;)... well actually, the torrent isn't *illegal*. My bad :D

edit: I'm going to try and get a seamless XP going in Feisty w/ VMware... I'll let you know how it goes, if you want.
That torrent is PERFECTLY legal.
My mouse is slow too.
How do I install VMTools?

---

### Post by bodhi.zazen on 2007-06-19
LOL

For seamless integration LOOK UP ^^^^ my first post ^^^^

> And Seamless Integration : [https://help.ubuntu.com/community/Se...Virtualization](https://help.ubuntu.com/community/Se...Virtualization)

To install the VMWare tools : [http://www.vmware.com/support/ws5/doc/ws_newguest_tools_windows.html](http://www.vmware.com/support/ws5/doc/ws_newguest_tools_windows.html)

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

---

### Post by T0MA on 2007-06-26
> **dannymichel said:**
> I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]


try using VirtualBox, since it has easy support for your soundcard and you can use the NAT to connect the VM to the internet by port-forwarding connections from the localhost to the vm.

use this how-to and skip the part which disables the network manager and the whole bridge stuff:
[http://ubuntuforums.org/showthread.php?t=433359&highlight=seamless&page=20]("http://ubuntuforums.org/showthread.php?t=433359&highlight=seamless&page=20")

use this instead:
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666

after that you will be able to connect to the vm by localhost:6666

---

### Post by lazyart on 2007-06-26
> **dannymichel said:**
> 
Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

I'm curious-- when you set up the VM did you give it a sound card?  That's a configuration issue.
To see the internet, try a bridged connection.  This gives you a seperate IP that's on your network.

---

