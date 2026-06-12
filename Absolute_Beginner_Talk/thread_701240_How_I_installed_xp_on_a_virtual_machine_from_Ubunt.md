---
title: "How I installed xp on a virtual machine from Ubuntu desktop."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2008-02-19
Installed xp on a vmware-server last night. I only did it for the experience, as far as I can tell. I have no use for it, really.

What are the advantages of running xp from a virtual machine? Not entirely sure. I assume it is more secure.  I don't have the hassles of dual-booting and file access problems I read so much about in this forum.

What are the disadvantages? I have read it will run slower in a virtual environment. So far, I haven't experienced that. The browser is working fine, and downloading seems normal. I have read that gaming isn't effective. I don't know yet. Maybe the product has improved since the time of those writings.

At any rate, for running an xp operating system where, for example IE is necessary, but ie4linux isn't working, this virtual environment seems to be excellent.

How I did it:

I got vmware-server from synaptic package manager, installed it, and completed a product registration with vmware. The registration is necessary to get a product key. The registration requested things like company name and type of business. I simply input things like "private"  "home use."

Once the installation was completed, I attempted to launch vmware from Applications>>System Tools. Ran the wizard, and had several failed attempts at putting xp on the virtual disk...usually ending with "windows could not detect the hard disk." The vmware server keeps an inventory of virtual machines, and only gave me one opportunity per virtual machine to install the operating system. So, by right clicking on each virtual machine in the inventory, I was able to select "remove from disk" and recover my virtual disk space ( a folder, in actuality).

Finally, I decided to launch vmware from the terminal. In the meantime, however, I had discovered two new folders in my home directory: vmware and .vmware. So I searched the forum a bit, and discovered a thread where someone had mentioned chmod 777 .vmware/preferences. So I fired up the terminal and did chmod 777 vmware and chmod 777 .vmware/preferences.

Then I launched vmware from the terminal with the simple command ```
vmware
```
The wizard ran and I pretty much went with all the default options, though I selected xp pro from a drop down list, instead of the default windows 2000. This time when I powered on the virtual machine, the xp installation went through without a hitch. Needless to say I was impressed.
In about 45 min., I was browsing the web via internet explorer...scary. Well, who knows, maybe I'll need it for something...doubtful.

---

### Post by Sceiron on 2008-02-19
Do you need a licensed version of windows xp pro and a windows installation cd for this ?
-got no clue-

---

### Post by kpkeerthi on 2008-02-19
> I assume it is more secure.
No. It is still vulnerable. You still need all the **anti**-everything in the world to keep your virtual windows safe.

> I have read that gaming isn't effective. I don't know yet. Maybe the product has improved since the time of those writings.
Not (quite) yet. vmware-server 2 **beta** has some experimental 3D support but still not usable for playing games.

---

### Post by spiderbatdad on 2008-02-19
> **Sceiron said:**
> Do you need a licensed version of windows xp pro and a windows installation cd for this ?
-got no clue-

You need a windows product key...so yes. I used the disk that came with my machine.

---

### Post by spiderbatdad on 2008-02-19
> **kpkeerthi said:**
> No. It is still vulnerable. You still need all the **anti**-everything in the world to keep your virtual windows safe.


Not (quite) yet. vmware-server 2 **beta** has some experimental 3D support but still not usable for playing games.

I guess I meant more secure from a hardware perspective. I'm not woried about a virtual operating system getting corrupted, but worried about what some viruses could do to my system and hardware overall...perhaps I should have used the word "safer." The xp, from what I understand,  is only on a virtual hard disk inside a folder. If the xp gets destroyed, my Ubuntu and grub are safe.

---

