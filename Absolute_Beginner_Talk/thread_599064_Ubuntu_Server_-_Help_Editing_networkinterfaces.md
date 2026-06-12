---
title: "Ubuntu Server - Help Editing network/interfaces"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Josecito on 2007-10-31
I am a complete beginner at this. 

I got Ubuntu server installed. Now the tutorial i was reading on setting this up says i have to edit 
etc/network/interfaces

when i type in 

vi etc/network/interfaces

all i get is a blank  screen that has "~" across the left side

i figured maybe i have to manually type all my info in since there is nothing to edit, taking into consideration i have no idea about what I'm doing i typed in 

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

i changed the info according to my set up, hope I'm supposed to do that.

but after that i am stuck in what to do when i go to save and close, which i think is 
:wq 
I get an error message saying that the file cannot be opened for writing, or something along those lines.

can someone please help i am kind of excited about having this set up instead of running xampp on a windows machines.

thanks in advance to all of you guys.:confused:

---

### Post by barbz127 on 2007-10-31
try

sudo vi etc/network/interfaces

that should display the info you want to change then :w to write and :q to quit.

you will then have to down then up the eth0 device (ifconfig eth0 down and ifconfig eth0 up)

it should come up with the new settings, run ifconfig to check

Paul

---

### Post by Josecito on 2007-10-31
I tried that, but what i get is a black screen with the "~" symbol on the left. No information is in there

It looks like this 

~
~
~
~
~
~
~

Thanks,

---

### Post by barbz127 on 2007-10-31
thats with the sudo in front? the file is in use by the system so you need to run it as sudo 

Paul

---

### Post by Josecito on 2007-11-01
I did sudo vi etc/network/interfaces 

That takes me straight to the black screen with the "~"

I am stumped. I dont know what else to try. I figured i would just type that in and make a couple of changes but thats as far as i have been able to get.

Reinstall you think? Maybe i messed up somewhere. But there isn't much from the point of installation to that point for me to mess up. 

Any ideas??

Again thanks.

---

### Post by barbz127 on 2007-11-01
what do you get if you do an ifconfig - has it picked up any adapters?

type in lspci and see if anything looks like a network adapter

this is mine
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

---

### Post by Josecito on 2007-11-01
Thanks i will try that next.

I'm currently doing a fresh install again maybe,  by chance i messed something up.

Thanks a lot for your help.

I will let you know what happens then.

---

### Post by barbz127 on 2007-11-01
Fair enough - drastic measure :)

If the interfaces file was empty or not created it may be because the system did not detect the network card - are you using onboard or a pci based card?

I tried a gigabit pci card a while back but it wasnt support so it never picked it up, etc,etc.

Paul

---

### Post by robrmd9 on 2007-11-01
> **Josecito said:**
> I tried that, but what i get is a black screen with the "~" symbol on the left. No information is in there

It looks like this 

~
~
~
~
~
~
~

Thanks,

Hey,

You are getting the ~s because the file you are trying to edit doesn't exist.  This is because the file you want to edit is located at /etc/network/interfaces (note the leading slash before etc).

So try

```
sudo vi /etc/network/interfaces
```

I would also recommend using nano instead of vi, which is easier for new users.

---

