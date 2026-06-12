---
title: "VMWare installation issue"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2007-05-06
I downloaded the program as a .rpm file.. This is what I did and it didn't work. :(

> 
owner@owner-desktop:~$ cd Desktop
owner@owner-desktop:~/Desktop$ sudo rpm -ivh VMware-player-1.0.4-44386.i386.rpm
error: Failed dependencies:
        /bin/sh is needed by VMwarePlayer-1.0.4-44386.i386


---

### Post by Stomstedt on 2007-05-06
I decided to download the .tar.gz file... I see these folders and files...
> owner@owner-desktop:~/Desktop/vmware-player-distrib$ ls
bin  doc  etc  FILES  installer  lib  vmware-install.pl


---

### Post by PilotJLR on 2007-05-06
Feisty (probably Edgy too) has this in the repos... just do a "sudo apt-get install vmware-player"


Or if you prefer your tarball, do a 
```

sudo apt-get install build-essential linux-headers-`uname -r`
sudo ./vmware-install.pl

```

---

### Post by Stomstedt on 2007-05-06
> **PilotJLR said:**
> Feisty (probably Edgy too) has this in the repos... just do a "sudo apt-get install vmware-player"


Or if you prefer your tarball, do a 
```

sudo apt-get install build-essential linux-headers-`uname -r`
sudo ./vmware-install.pl

```

If I use 6.06, do I still do it this way?

---

### Post by PilotJLR on 2007-05-06
Yep, just those last 2 lines.

The first line meets dependencies by making sure the compiler and kernel headers are installed (since vmware will need this).
The second line runs the vmware install program as root.

ALSO: be in the vmware-player-distrib directory when you do this

---

### Post by Stomstedt on 2007-05-06
OK now I got that all to work and everything, but what do I do to get a vmx file for my windows installation?

---

### Post by PilotJLR on 2007-05-06
I don't understand... what are you trying to do???



IF you want to virtualize your existing Windows installation on a different partition... then it's possible, but not free. the VMware Converter application does this. That's an enterprise app and is far outside the scope of home use and Player.

---

### Post by Stomstedt on 2007-05-06
I have windows on another partition..  So I can't access it?  I have Windows on my linux installation in the hda1 drive.  So it is still accessible

---

### Post by PilotJLR on 2007-05-06
Right, you can't do this with what you have... VMware Player will "play" an existing virtual machine; VMware Server will let you create a virtual machine from scratch. NEITHER can convert an existing physical machine to a virtual one. That requires the expensive Converter application.

If you have Windows media and a license key, you could use VMware Server to make a NEW virtual machine... again, you would be starting from scratch on that.

---

### Post by ubnewbie2 on 2007-05-06
> **PilotJLR said:**
> I don't understand... what are you trying to do???



IF you want to virtualize your existing Windows installation on a different partition... then it's possible, but not free. the VMware Converter application does this. That's an enterprise app and is far outside the scope of home use and Player.


There is a non-enterprise converter program ([http://www.vmware.com/products/converter/)](http://www.vmware.com/products/converter/)), it's free and I found it worked very well.  I even cloned a remote machine and ran it using the free player. It wasn't that hard to figure out.

Also, you can take and existing virtual machine (that has enough hard disk etc.), start it up, and tell it to boot from cdrom. If you boot it from your Windows install disk, you can then install Windows, just as you would for any new PC.

---

### Post by PilotJLR on 2007-05-06
Wow, good call!!  I thought you HAD to buy VI3 Enterprise to get this, but evidently not.  :-)

This is exactly what you need.

---

### Post by Stomstedt on 2007-05-06
So basically, I install another operating system?  Hmm what directory do i install it to?  I was under the understanding that if you did that, it would create problems for your linux or such..    I saw that on the website they have a converter that is on the website but it is the "starter" or something? Hmmm

EDIT: Aha, thank you both very much :)

---

### Post by Stomstedt on 2007-05-06
That program is an exe file..  Do I use that with linux or..?

---

### Post by ubnewbie2 on 2007-05-06
> **Stomstedt said:**
> So basically, I install another operating system?  Hmm what directory do i install it to?  I was under the understanding that if you did that, it would create problems for your linux or such..    I saw that on the website they have a converter that is on the website but it is the "starter" or something? Hmmm

EDIT: Aha, thank you both very much :)


Sounds like you have it figured out, but to answer your question above, if you are installing it, just keep thinking like it is a real machine.  Therefore, when you install, you can do all the things you would on a real hard drive, including dual booting with the original operating system, or repartitioning and format the whole thing for Windows. Since you should be doing this to a copy of the original virtual machine, you will end up with 2 machines, one for linux, one for Windows, so there's really no need to dual boot inside one of them.:)

---

### Post by ubnewbie2 on 2007-05-06
> **Stomstedt said:**
> That program is an exe file..  Do I use that with linux or..?

I haven't tried Wine, it may work, but it may also work well in a Windows virtual machine:)

---

