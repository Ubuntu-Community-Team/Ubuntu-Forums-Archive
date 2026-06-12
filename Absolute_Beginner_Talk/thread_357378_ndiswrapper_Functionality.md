---
title: "ndiswrapper Functionality"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by .plaid on 2007-02-09
Howdy. 

I'm in the (slow) process of trying to get my PCMCIA WiFi card to work, and have run into a linux-only problem that surely has an easy fix - I just don't see it.

I have successfully installed and can use ndiswrapper to install a driver for the card. That is where the fun begins.

Last night's adventure will give you an idea of my problem:
```
dotplaid@dotplaid-laptop:~/drivers/Intel_WiFi$ sudo ndiswrapper -i netwlan.inf
Password:
Installing netwlan
couldn't copy netwlan.inf at /usr/sbin/ndiswrapper line 135.
```
Ah, well, I typed the wrong file name. So I tried it again:
```
dotplaid@dotplaid-laptop:~/drivers/Intel_WiFi$ sudo ndiswrapper -i netwlan5.inf
Password:
Sorry, try again.
Password:
Installing netwlan5
couldn't copy netwlan5.inf at /usr/sbin/ndiswrapper line 135.
```
"Couldn't copy" seemed to indicate that I'd done something else wrong so I hit the 'arrow-up' key, checked my syntax, and did it again:
```
dotplaid@dotplaid-laptop:~/drivers/Intel_WiFi$ sudo ndiswrapper -i NetWlan5.inf
netwlan5 is already installed. Use -e to remove it
```
Are you kidding me?? So, it turns out that a folder had been created in ndiswrapper. So I followed the terminal's instruction:
```
dotplaid@dotplaid-laptop:~/drivers/Intel_WiFi$ ndiswrapper -e NetWlan5
Driver NetWlan5 is not installed.Use -l to list installed drivers
dotplaid@dotplaid-laptop:~/drivers/Intel_WiFi$ ndiswrapper -l
Installed ndis drivers:
netwlan invalid driver!
netwlan5        invalid driver!
```

So I couldn't install the driver because it was already installed, and I couldn't remove the driver because it wasn't installed. Folders had been created but they were empty. Their existence, however, prevented me from moving forward. 

To get rid of them!

I tried various ways to delete the folders but *root* was the owner of them, not me, so I had to manually change the ownership of the folders to me and then delete them. I changed the ownership of the ndswrapper folder to me, hoping that all subfolders would fall under my ownership, but no such luck. **Is there a better, easier way to work with ndiswrapper?** I don't know how many drivers I will try before I'm brave enough to somethingsomethingsomething my kernel and update some header or other, and would like to think that there is a way to streamline this process.

Thanks for your insights,
.

---

### Post by riven0 on 2007-02-09
I don't use the ndiswrapper, but it may be easier for you to simply use the graphic ndiswrapper installer instead of doing it through the terminal. The package is **ndisgtk **

---

### Post by .plaid on 2007-02-09
Thanks for the tip, riven0. I don't have access to the repositories unless I bring my box (is a laptop still a box? Or a rig, for that matter?) to work - which is certainly doable. The Dapper CD only has ndiswrapper-common, iirc, no utils nor ndisgtk.

Maybe that's a Saturday task....

Anyone know some command-line finesse they'd like to share?

Best regards,
.

---

### Post by .plaid on 2007-02-12
One of these days I'm going to remember about the included *man*uals.

I was looking for -R option, which would recursively apply ownership changes to the folder.

*chown -R user:group folder*

.

---

### Post by c00ch on 2007-02-12
you should try uninstalling the drivers ndiswrapper -l gives you. Remember the the stuff is case-sensitive.

```
ndiswrapper -e NetWlan5
```

is unlikely that you'll be able to uninstall a driver ndiswrapper recognizes as (case-sensitive)

```
netwlan5        invalid driver!
```

As for the installation of the drivers... have you got all the driver files in your Intel_WIFI folder e.g. the .inf, .sys, .cat etc)?

---

### Post by sunexplodes on 2007-02-12
I've run into this exact problem in the past. 

When you try to uninstall invalid drivers, nothing happens. navigate to /etc/ndiswrapper, and delete the folders you find there with the driver names. 

then try again.

---

### Post by .plaid on 2007-02-12
hi c00ch,

It seems like ndiswrapper is not case-sensitive. I thought of that, and tried all the combos, but I noticed that the installed drivers are all lower case. I know that once I changed the (recursive) ownership of /etc/ndiswrapper I was able to install and remove with no problem.

As for the installation of the drivers: no. I have been basing my work (mostly play, right? yeah) on some forum poster or other who said that anything other than the .inf and .sys files could muddle the process. 

At this point I'm not even convinced there's much value in moving forward with this WiFi card - I took it into a big box store this weekend, "No I don't need any help, just looking, tha - no, I said! Get off my leg dude!!" and stuck the card into a handful of laptops running Vista. The systems recognized that I had put a card in the PCMCIA slot, but it couldn't find the right software to install it. Worse, the light on the card never came on - I would imagine that's a power issue, not an install issue. I thought about the firmware, but my distro package manager isn't working right (upon insertion the CDROM browser comes up instead of starting the pkg mgr).

But, please: if you have any insight (I've got most of the HowTos at home) I'm willing to try. 

Thanks for the replies, folks,
.

---

