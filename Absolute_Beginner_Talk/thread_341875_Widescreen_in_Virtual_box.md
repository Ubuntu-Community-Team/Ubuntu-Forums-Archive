---
title: "Widescreen in Virtual box"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2007-01-19
Can it be done? I have a widescreen laptop, (15.4 inch) but I only get 1024 x 768. Is there a way to make it 1200 x 800??

---

### Post by BarfBag on 2007-01-19
By virtual box, do you mean virtual machine?  Like, a VMWARE environment, for example?

---

### Post by Jussi01 on 2007-01-19
yeah, I mean virtual box, [http://www.virtualbox.org/](http://www.virtualbox.org/) Kind of like vmware...but simpler.

---

### Post by Hanzerik on 2007-01-19
> **Jussi01 said:**
> Can it be done? I have a widescreen laptop, (15.4 inch) but I only get 1024 x 768. Is there a way to make it 1200 x 800??

You talking about a VM in VMWare? If so then you need to install vmware tools.

Make sure you have the linux headers installed for your running kernel:
sudo apt-get install linux-headers-`uname -r`

And build essentials:
sudo apt-get install build-essential

You can get the VMWare tools from the VMWare Server package. 
tar xzvf VMware-server-1.0.1-29996.tar.gz

Then just copy over the vmware-server-distrib/lib/isoimages/linux.iso image to your clint machine via some means and mount it.

sudo mount -o loop linux.iso /media/cdrom
cp /media/cdrom/VMwareTools-1.0.1-29996.tar.gz ~
cd
tar xzvf VMwareTools-1.0.1-29996.tar.gz
cd vmware-tools-distrib
sudo /vmware-install.pl

You should be good to go by accepting the default locations, and when you get to the part where it asks for a screen resolution, just select the res that you want to use.

---

### Post by Hanzerik on 2007-01-19
Heh, typed all that for nothing :-)

These instructions were for install the tools on vmware player, if you have a vmware server then they are slightly different.

---

### Post by Jussi01 on 2007-01-20
Ok, sorted - thanks to the vbox irc channel - they are very helpful in there. If anyone needs to know you need to install guest editions from the menu. that gives you a whole lot more options!!  

Good Luck.

PS. My experience is that virtual box runs faster, and is simpler to setup than vmware. so I'd highly reccomend it to all.

---

### Post by chris_lenney on 2007-02-07
Can you please elaborate on how to download and install these "guest editions" to enable full screen when running Virtual Box.

Im new to this and can't quite work out what you mean!

Chris

---

### Post by xpod on 2007-02-07
You should be able to go to the devices tab and install your guest additions from there.:)

---

### Post by xpod on 2007-02-07
I dont think they`ll find their guest additions on there:confused: 

Just install your VM  of choice and you`ll automatically have your additions available via the "devices" tab.....Linux and Windows that is

Or you can go look at  bumfuzz`s funny photos:???:

---

### Post by chris_lenney on 2007-02-07
Devices tab? Is that in the Virtual Machine? So i have to actually load up Ubuntu (from my windows host) to infd this tab?

---

### Post by xpod on 2007-02-07
Thats right m8...

Once you`ve loaded up your OS of choice you should have "guest additions" in the devices tab that you can just click on to install.
I`m assuming it will be the same for you with a Windows host and Linux guest

I`m the other way round with XP guest on Ubuntu host but it should`nt be any different i dont think.

---

### Post by xpod on 2007-02-07
[ATTACH]24727[/ATTACH]

Theres what you should see in the tab if that helps

---

### Post by tajmox on 2007-02-23
This worked for me:
[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1003&sliceId=SAL_Public](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1003&sliceId=SAL_Public)

---

