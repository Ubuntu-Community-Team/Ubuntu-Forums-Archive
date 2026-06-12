---
title: "Unable to change Resolution"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2007-11-28
I'm trying to change my native resolution and but for some reason I'm unable to

gustason@gustason-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
Password:
xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20071128171233
gustason@gustason-laptop:~$

How do I get past this?

---

### Post by overdrank on 2007-11-28
> **gustasonfrever said:**
> I'm trying to change my native resolution and but for some reason I'm unable to

gustason@gustason-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
Password:
xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20071128171233
gustason@gustason-laptop:~$

How do I get past this?

HI and you could try and remove the -phigh 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gustasonfrever on 2007-11-28
that worked perfectly! The only problem is that I have an intel graphics card (Its a lenovo t61), and I don't see an option that will work with my system. Am I just overlooking it?

After checking it out a bit more I think I do have an NV graphics card. But I'm not sure how to get the "Bus ID" of the video card

ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000
evidently it would be in a format like that. any suggestions?

---

### Post by overdrank on 2007-11-28
> **gustasonfrever said:**
> that worked perfectly! The only problem is that I have an intel graphics card (Its a lenovo t61), and I don't see an option that will work with my system. Am I just overlooking it?

After checking it out a bit more I think I do have an NV graphics card. But I'm not sure how to get the "Bus ID" of the video card

ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000
evidently it would be in a format like that. any suggestions?

Hi and you can leave as the default answer give on the bus id, maybe this link will help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

