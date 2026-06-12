---
title: "Xubuntu Networking"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by PANiC_nz on 2006-09-03
Hi

Ive recently installed Xubuntu on a P3 450MHz, after the installation i ran Automatix (as far as i can tell successfully). Im connected to my network, with an IP from my DHCP server, and am able to surf the internet. So far no problems.

I want to gain access to some movies, mp3's and images on another PC, but am not sure how to browse my network? I tryed inputing the IP address into the file explorer but that failed. Do i need some particular software to browse my network? or am i just blind?

Any help is greatly appreciated

Regards

Panic

---

### Post by jimrz on 2006-09-04
> **PANiC_nz said:**
> Hi

Ive recently installed Xubuntu on a P3 450MHz, after the installation i ran Automatix (as far as i can tell successfully). Im connected to my network, with an IP from my DHCP server, and am able to surf the internet. So far no problems.

I want to gain access to some movies, mp3's and images on another PC, but am not sure how to browse my network? I tryed inputing the IP address into the file explorer but that failed. Do i need some particular software to browse my network? or am i just blind?

Any help is greatly appreciated

Regards

Panic

Samba works nicely for me and is available via Synaptic + there are plenty of posts you can find by searching these forums and/or the wike to help guide you through setup.

---

### Post by msak007 on 2006-09-04
Xubuntu's File Manager (Thunar) does not support network / Samba browsing like Nautilus or Konqueror do. I found this out recently when I tried Xubuntu on an older computer (AMD 500 MHz / 128 RAM) and quickly switched (I found a few other features lacking). Apparently it's on the wishlist for a future version, but I needed it now. Kubuntu actually runs faster on it but that's another story...

Anyway as far as network shares, you have 2 options (aside from using the terminal to navigate):

1. Mount the network share locally so Thunar can see it as a "local" drive and you navigate to it (recommended). [Here's]("http://ubuntuforums.org/showthread.php?t=128873&highlight=cifs") a thread outlining how to do that (using cifs instead of smbfs).
2. Intall another file manager (like xffm4, Nautilus, etc.) that has network browsing capability. [Here's]("http://www.ubuntuforums.org/showthread.php?t=98692&highlight=xubuntu+samba") a thread outlining how to install Nautilus in Xubuntu. 

Method # 2 is not as efficient as method # 1 (you have to install a lot of the Gnome components required with Nautilus), but if you frequently visit different network locations where it's not feasible to mount them permanently using fstab, it may be better for you.

---

### Post by PANiC_nz on 2006-09-04
So do you think i'd be better off installing kubuntu? I think i'll try the Nautilus option, will post back later hopefully with a success story. Thanks for the help its really appreciated, i thought i was goin blind when i couldnt figure out how to browse my network.

---

### Post by msak007 on 2006-09-04
> **PANiC_nz said:**
> So do you think i'd be better off installing kubuntu? I think i'll try the Nautilus option, will post back later hopefully with a success story. Thanks for the help its really appreciated, i thought i was goin blind when i couldnt figure out how to browse my network.

I never suggested that you install Kubuntu instead. I was just saying that's what I ended up installing in the end. It's what I'm most familiar with (KDE), and thought I'd give it a shot to see if it would actually install. I really didn't think the machine could handle it (sure there is lag, that's expected) but not only did the Live CD run better, the machine is performing better than it did with Xubuntu (contrary to every single piece of advice I have read that indicates otherwise). My recommendation was doing the first option, but if that's not how you want to do it then yeah I would suggest installing Nautilus. Of course you *could* always install Ubuntu or Kubuntu to see if it runs the same or better, and then make your final decision. There are other window managers such as FluxBox or IceWM that you may also want to give a shot.

---

### Post by PANiC_nz on 2006-09-04
Well i managed to get Nautalis to install, but for some reason it wont access the network. It brings up the following error message:

"smb:///" is not a valid location

any tips?

regards

panic

---

### Post by Titus A Duxass on 2006-09-04
If the other pc is also linux use ssh.
There is a good howto on the forum.

I use it with ubuntu, kubuntu, xubuntu and mythdora.

---

### Post by handy on 2006-09-04
I set up with NFS, a week ago using [this page]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT")!

It was not hard to do, & worked fine, even though we are using ver 4. NFS now in Dapper!

You mount remote directories, (whole drives if you want) & just browse with nautilus, or whatever you want to use.

Just another choice to make it harder! :)

---

### Post by msak007 on 2006-09-04
> **PANiC_nz said:**
> Well i managed to get Nautalis to install, but for some reason it wont access the network. It brings up the following error message:

"smb:///" is not a valid location

I apologize, I completely forgot that I ran into that error when I tried this method. You need to install libgnomevfs2-extra:
```
sudo aptitude install libgnomevfgs2-extra
``` Hope this helps.

@ handy: Thunar can see a remote location just like Nautilus or Konqueror can if the remote drive is mounted locally, but the root problem the OP wanted to address was not being able to browse the network graphically.

---

### Post by PANiC_nz on 2006-09-04
Cheers, all working fine now

---

### Post by DJiNN on 2006-09-08
> **PANiC_nz said:**
> Cheers, all working fine now

How did you get it working in the end? I'm having the same problem here..... i can access my Xubuntu box from my main Ubuntu machine, but  i can't do the same from the other way around. Thunar is (at the moment) not able to browse network shares natively, and xffm (which i have tried) is great, but completely takes over the machine & desktop, and then i lose the ability to right click the mouse button on the desktop (To access programs, settings etc). 

Has anyone else had any success in this are? :)

---

