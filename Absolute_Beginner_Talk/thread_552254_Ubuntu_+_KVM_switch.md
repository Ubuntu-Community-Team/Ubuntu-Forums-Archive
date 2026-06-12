---
title: "Ubuntu + KVM switch ?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-09-16
I have a 4 port KVM switch, an  Aluratek AKSP04 I'm using with 3 computers.
These are their corresponding port numbers now.
1 - Dual booting Feisty & XP
2 - Dual booting Edgy & Win98
3 - XP only
4 - blank
The problem I have is my monitor resolution will max out at 800x600 on Ubuntu on every port except port # 1 . Windows works fine on all ports. I've tried all different combonations of setups
& startups with the switch & nothing works.  Basicly I only use Ubuntu on one computer & Windows on the others because of this. Switching computers is not a problem it just seems like the monitor is not recognized by any other port but # 1 in Ubuntu.  
The switch says its Linux compatible & of course their tech support has never heard of this problem.
Does anyone have any ideas?

---

### Post by cmnorton on 2007-09-16
I am using an Acer Travel Mate 630 (laptop) both solo and through an Acer docking station, which is plugged into a Belkin 4 port KVM. The Acer is running Ubuntu 6.06 LTS. 

KVM's are wierd. I have to be set to my Windows WS port, while it boots, or I have no mouse or keyboard. Once it's booted, everything's fine. The only problem I have with Ubuntu is when switching back to that KVM port, I have to move the mouse around alot, to get it to move. Most of the time the keyboard works. My Linux-based Ericom PowerTerm Interconnect applications freeze if the window is active and I switch back to the Ubuntu port, but not always.

My conclusion with your problem is get your KVM manufactuer involved. 

Are you maxed out at 800x600 if you are set to the Ubuntu ports while Ubuntu boots? That might be one to try out.

Good luck.

---

### Post by garyed on 2007-09-16
KVM switches can be wierd but they sure are convenient.
It really doesn't matter how or what OS I boot with. 
All that matters is what port Linux is running on. 
Anything but # 1 & that's it, 800x600 max resolution on any Linux OS, but  all Windows  run fine on any port at 1280x1024.
I wish I understood the way KVM's work besides their switching capabilities. 
They evidently tell the computer there's a monitor hooked to it when the switch is not engaged.

---

### Post by splintercellguy on 2007-09-16
Could this be an xorg.conf thing? Have you tried sudo dpkg-reconfigure xserver-xorg to configure the resolutions?

---

### Post by garyed on 2007-09-16
> **splintercellguy said:**
> Could this be an xorg.conf thing? Have you tried sudo dpkg-reconfigure xserver-xorg to configure the resolutions?

I don't think so.
I spent a few days messing with xorg.config to no avail. 
It was only when I was experimenting with the cables that I found the problem. 
My Edgy machine was working fine but my Feisty one was not. Switching cables made no difference but when I crossed the ports I found my Edgy wasn't working right & my Feisty was.
Edgy originally was on port # 1 & Feisty on # 2. After that I did all kinds of combinations & found the only thing that worked on either distro was port # 1. 
Again the only thing that was wrong would be the screen resolution would go no higher than 800x600.

---

