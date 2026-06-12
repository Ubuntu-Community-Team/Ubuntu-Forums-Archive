---
title: "Nvidia further trouble..."
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-08
Hi again, I got my Nvidia drivers to work properly after several problems. I have two questions now...

I don't see a menu to edit the options of my Nvidia settings. 

When I did a search in terminal for what packages were installed on my comp associated to nvidia I got this:

```
 "entered Sudo aptitude search NVidia"
i   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.8776          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-legacy-kernel-source     - NVIDIA binary 'legacy' kernel module sourc
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig    
```

I noticed that nvidia-settings hadn't been installed via my automatic method... so I tried to manually install via "Sudo aptitude install nvidia-settings" and I got this.

```
root@ubuntu:~# sudo aptitude install nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  nvidia-glx 
The following NEW packages will be installed:
  nvidia-settings 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 504kB of archives. After unpacking 1020kB will be used.
The following packages have unmet dependencies:
  nvidia-glx: Conflicts: nvidia-settings but 1.0-3ubuntu7 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
nvidia-glx

Install the following packages:
nvidia-glx-legacy [1.0.7184+2.6.17.5-11 (edgy)]

Score is -370

Accept this solution? [Y/n/q/?] 

```

What does that mean and why would I have to remove my glx to install settings? I know my nvidia driver is loaded because I see the nvidia splash page... is there a sudo terminal command that can tell me if glx is rendering on my nvidia?

(On a side note, what does v next to a package mean in the terminal search results?)

---

### Post by Perfect Storm on 2007-03-08
You don't need to install Nvidia-settings. It's build-in in the driver you downloaded. Simple type nvidia-settings in the terminal is sufficient (or making a launcher for it if you want to click).

---

### Post by starcraft.man on 2007-03-08
Thanks, thats perfect got to the settings. :)

---

