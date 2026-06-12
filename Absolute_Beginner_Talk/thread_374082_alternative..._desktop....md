---
title: "alternative... desktop..."
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by omrsafetyo on 2007-03-02
Hey, I'm pretty new to Ubuntu - and really linux in general.  I use SCO UNIX at work, though - I don't do much administration or anything; I am familiar with the command line; I write the occasional shell script, etc. 

So anyway, I had a question regarding the different iso packages.  I went ahead and downloaded the amd64-alternative version of Ubuntu for my new build (AMD Athlon 64 X2 3600+ core).  I was going to try it out using the live CD - in the past, my biggest linux experience was with knoppix-STD, which is a live-CD distro.  I figured I would try out Ubuntu from the CD drive before installing it - to see if it was user friendly enough for my wife.  I also had a few more distros that I thought I might try - but Ubuntu looked the most windows-user friendly.

Anyway -- I'm guessing you guys are already laughing, because I'm thinking that the "alternative" means that there is no live option on my iso?  Do I need to download the desktop iso for that function?  Its more out of curiousity than anything - I have already installed Ubuntu - and am quite satisfied so far -I will have to try some of the tricks found in the 64 bit forum to install wine and flash, etc. but, I figured I should get some of my newbie questions out of the way.  

So is the "alternative" iso non-live, and the "desltop" iso live?

Thanks.

---

### Post by 23meg on 2007-03-02
>  So is the "alternative" iso non-live, and the "desltop" iso live?

Yes. With the desktop CD you can run a live session, in which you can also install Ubuntu to your hard disk with a graphical installer.

---

### Post by v8YKxgHe on 2007-03-02
> **omrsafetyo said:**
> 

So is the "alternative" iso non-live, and the "desltop" iso live?

Thanks.

Yep, Alternate has no LiveCD option, where as the Desktop CD does.

---

### Post by steven8 on 2007-03-02
The liveCD is a great way to see how well your hardware works with Ubuntu.

---

### Post by omrsafetyo on 2007-03-02
wow, you guys are quick.

I was lucky that my hardware (mostly) worked.  I did have to use a noapic and nolapic flags during my install - but other than that, it was a breeze.  I think that was caused by my motherboard.

I figured that was what the problem was.  I searched for quite a while on the CD for the LiveCD, and later on I was browsing back through the download page - and I assumed that must be what the problem was.  

Thanks for the quick response!

---

### Post by steven8 on 2007-03-02
Cool!  Have fun!! :)

---

### Post by nweissma on 2008-02-14
i can't understand why live-versus-install dichotomy is pivotally important -- it's easy enough to uninstall! therefore, there must be more to alternative-versus-desktop than merely live ("sandbox")-versus-install?!

and as i understand it, the alternative versions provide more features.

also, do the alternative versions offer a GUI?

---

### Post by PeterJS on 2008-02-14
> **nweissma said:**
> i can't understand why live-versus-install dichotomy is pivotally important -- it's easy enough to uninstall! therefore, there must be more to alternative-versus-desktop than merely live ("sandbox")-versus-install?!

and as i understand it, the alternative versions provide more features.

also, do the alternative versions offer a GUI?

That dichotomy is long gone as evidenced by ubuntu desktop/live/installer CD. Both of them are install disks, it just what degree of user expertise and quantity of RAM is available. The alternative CD fulfills two major roles, installing ubuntu on systems that don't have the RAM to support a live environment, they work on low RAM systems because they are non-graphical. They do have some more advanced features, that the very vast majority of people aren't going to need, like encrypted LVM root, and other exotic disk options.

---

### Post by emarkd on 2008-02-14
The alternative disk offers a way to install Ubuntu without the graphics and overhead of a live CD.  Some video hardware won't run the live CD, for instance.  Also low memory systems can't use the Live CD because it needs to break off a chunk of RAM to emulate a hard disk.  Ubuntu will run on 256 MB, but the Live CD surely won't.

In the end, though, you get the same software.  You just take a different path to get there.

---

### Post by Kopachris on 2008-02-14
For anyone's future reference, the Kubuntu Live CD includes a Live option and an alternate install option.  After installing, you can go ahead and download GNOME from the Synaptic package manager.  I assure you, both are very easy to use.  A girl in one of my classes who is not very computer-savvy uses Ubuntu as her primary operating system.

---

### Post by hyper_ch on 2008-02-15
btw, with the alternative install cd you can choose to fully encrypt your filesystem upon installation and the alternative cds can also be used for upgrading (instead of hammering the servers)

---

### Post by nweissma on 2008-02-15
do you know what encryption scheme is used? (there are so many encryption softwares available  they are being bundled even with hardware such as the external drive i just purchased), why would i choose this one)?

and a silly newbie query: what do you mean by a "live cd"? i get the intuitive impression that 'live cd'  is what is called "sandbox" in the vernacular of 'virtual machine': try out a software in a protected/virtual platform; if it causes trouble then just trash it because it was never installed.

let's assume that ram is not a consideration (i have 4GB). for what reasons (besides encryption) would i still select the alternate ?

thanks for your help guys!

---

### Post by LaRoza on 2008-02-15
> **nweissma said:**
> 
and a silly newbie query: what do you mean by a "live cd"? i get the intuitive impression that 'live cd'  is what is called "sandbox" in the vernacular of 'virtual machine': try out a software in a protected/virtual platform; if it causes trouble then just trash it because it was never installed.

let's assume that ram is not a consideration (i have 4GB). for what reasons (besides encryption) would i still select the alternate ?

thanks for your help guys!

"Live CD" means you can run the OS off the CD. Put the CD in, reboot, and you have Ubuntu running without installing it. Of course, it is slower, and any changes are lost when you shut down.

I use the alternate CD because I use it to install the OS only. It has other features too. It can be used to upgrade a system, repair a system, and install a command line system.

---

### Post by nweissma on 2008-02-15
> **LaRoza said:**
> "Live CD" means you can run the OS off the CD. why do i want to do this?

> I use the alternate CD because I use it to install the OS only. It has other features too. It can be used to upgrade a system, repair a system, and install a command line system.i appear to be still confused: are you saying that desktop version cannot be used for upgrade and repair, and that it is not possible to* install * using desktop? what is the procedure for upgrading and why would desktop not include this capability?

---

### Post by nweissma on 2008-02-15
> **LaRoza said:**
>  repair a system, and install a command line system. can i safely say that the command line system is preferred by the more experienced programmers? how often are "repairs" needed? (repairs such as what- file corruption?)

---

### Post by PeterJS on 2008-02-15
> **nweissma said:**
> why do i want to do this?


To test it out, pop in the CD, see if it works. When you're done, reboot, eject, and it it's like ubuntu was never there. No chance of damage to the machine.

> 
i appear to be still confused: are you saying that desktop version cannot be used for upgrade and repair, and that it is not possible to* install * using desktop? what is the procedure for upgrading and why would desktop not include this capability?

You're confusing the desktop, with the desktop CD. You can certainly upgrade between dists from with in the desktop environment with an internet connection. What you can't do is put the live install CD and use that to do an offline upgrade.

On the bit of installing software, you can most certainly install software to the live environment, but like any thing else done live, the changes are gone when you shut the machine down.

---

