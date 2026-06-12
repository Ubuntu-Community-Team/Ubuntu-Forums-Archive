---
title: "Virtualization"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-05-18
Hello,

I've been a long time Windows XP user, but I recently switched my old desktop over to Ubuntu.  I like the clean interface, the stability and the simple fact that it's efficient.  I've recently considered switching over my laptop, which is my main computer, to Ubuntu, but the problem is there are some programs I cannot live without.  I need Photoshop CS3 and Sony Vegas to do some of the work I do.  I've been hearing a lot about virtualization, and I had a few questions on it:

1.  Through virtualizaiton, how slow would running a program such as Photoshop be compared to running it normally in Windows XP?

2.  When I start a Windows program, would the computer then boot the Windows operating system, or does this OS boot when Ubuntu does?

3.  Is the benefits of virtualiation worth the hassles?

4.  Would I be able to play some of my windows games (such as F.E.A.R.) virtualized, or would the performance lag be too much?

Thanks for the help,

Helixed

---

### Post by trent dillman on 2007-05-18
...

---

### Post by kyphi on 2007-05-18
Yes, I too know of the difficulty of having Windows programmes that I consider essential.

The solutions I have employed are:

Two hard drives to separate operating systems - if one fails, the other still works and can effect a recovery.

Codeweavers CrossOver Linux runs several of my programmes that were originally written for Windows.

Innotek VirtualBox runs a copy of XP with PhotoImpact 8 without any prblems and no slower than XP.  I would have to add, that VirtualBox gives you the option when closing, to power off the machine or to save the machine state.  If I opt for the latter when I have had PhotoImpact open, on the next start I can access PhotoImpact in seconds without having to go through the Windows start-up sequence nor the PhotoImpact start-up sequence.

I am not familiar with Sony Vegas.

To play games, you are better off with dual boot, as trent said.  For me, that is XPs only purpose.

---

### Post by trent dillman on 2007-05-18
...

---

### Post by dfreer on 2007-05-18
3D games (hence F.E.A.R.) do not work yet because vmware hasn't released their 3D card driver yet (although I haven't checked for awhile). Other than that, as long as you are not running the two OS's on the same hard drive you shouldn't notice too much of a lag (assuming you have a somewhat modern laptop with enough memory for both OS's). When two operating systems run on the same hard drive you start getting some insane I/O lockups, not to mention it is bad for the hard drive.

I think virtualization works great if you have two hard drives, other than for games.

---

### Post by helixed on 2007-05-18
I'm running a dell Inspiron E1705 with a gig of memory and a core 2 duo 2.16 GHz processor.  Will this be sufficient for Photoshopping especially?  Also, is it possible for me to run Virtual box and separately boot XP at different times?   How will I handle the file storage between the two OS's?  Obviously I want to be able to access my windows files under Linux and visa versa.  

Thanks,

Helixed

---

### Post by in_flu_ence on 2007-05-18
> **helixed said:**
> Hello,

I've been a long time Windows XP user, but I recently switched my old desktop over to Ubuntu.  I like the clean interface, the stability and the simple fact that it's efficient.  I've recently considered switching over my laptop, which is my main computer, to Ubuntu, but the problem is there are some programs I cannot live without.  I need Photoshop CS3 and Sony Vegas to do some of the work I do.  I've been hearing a lot about virtualization, and I had a few questions on it:

1.  Through virtualizaiton, how slow would running a program such as Photoshop be compared to running it normally in Windows XP?

2.  When I start a Windows program, would the computer then boot the Windows operating system, or does this OS boot when Ubuntu does?

3.  Is the benefits of virtualiation worth the hassles?

4.  Would I be able to play some of my windows games (such as F.E.A.R.) virtualized, or would the performance lag be too much?

Thanks for the help,

Helixed

1. I tried once running some CFD simulation under virtualisation with my desktop and it runs very smoothly. I guess photoshop will run fine if you have enough memory. 

3. virtualisation definitely worth the hassle if you have a powerful machine. I prefer virtualisation over dual boot since you can move from one 'machine' to another easily and quickly.

4. games is one thing i don't really believe virtualisation is a good thing to do. I think it just can't give you the maximum performance (think it can't cope too well with your graphics card and sound card) especially if your host machine is linux-based. Dual boot will be the choice for me in this case.

Among the choices, i prefer vmware over virtualbox. that's just my preference but it has been a quality product all the while and it really serves me well in terms of performance and reliability. I have tried running my virtual machine for weeks without any issue.

Hope this helps.

---

### Post by dawdler on 2007-05-18
High end games like FEAR cannot be run in a VM windows image due to the reason dfreer mentioned, which is no 3D graphics driver nor direct access to the physical graphics device in the VM.

I run a XP VM image to run the deeply-inflated Microsoft VIsual Studio for development purposes at work on a XP host machine that is a 3.0 GHz P4 with 3GB RAM.  Applications that are run in the VM including Visual Studio run very well when the CPU is idling.  Just make sure you give the VM plenty of memory.  You may even have a better experience with virtualization b/c you have a dual-core processor.

I've used Virtual Box on my ubuntu desktop at home, and it does not compare to VMWare in performance and stability.  I tried running various VM Linux distros in Virtual Box and they keep crashing at certain points.

My recommendation is to get a huge harddrive and do both options, dual-boot and use virtualization.  Game on the dual-boot and do work in the VM.

---

### Post by kfries6 on 2007-05-18
Every program is different, and will behave diferently under virtualization.

If I were you, I would give virtualization a try, and see what happens.  If nothing else, you will get a better understanding of your Linux desktop.  With luck, you may find that your programs will run well enough that the ease of access is well worth any potential slowdown.

Here is another trick you might try that I also use.  I need to do complex diagramming and DIA is just not up to speed, so I run Visio.  This is how I to it.  I run a VM that runs Win2k.  Inside of that VM I install Visio and a program called the 2x Application Server.  You can export via terminal services up to 5 applications for free.  Once everything is installed, I configure 2X to export Visio.  I then create an icon on my Linux desktop to run Visio.  While Visio is running in a VM in Windows, I never interact with Windows.  It makes it look as if I have Visio running in Linux (do this and watch the look of shock and horror on your favorite Windows Admins face, its worth the price of admission... free, lol).

Right now I am using VMware, but plan on converting that machine to VirtualBox soon, as I have found better performance characteristics with that program.

Good Luck, just remember, YMMV
Kevin Fries

---

### Post by kfries6 on 2007-05-18
> **helixed said:**
> is it possible for me to run Virtual box and separately boot XP at different times?   How will I handle the file storage between the two OS's?  Obviously I want to be able to access my windows files under Linux and visa versa.

VirtualBox allows you to use a directory on your Linux host in the guest machine.  It can be mounted via NFS or CIFS/SMB.  So in your case, create the shared folder in Linux, then use the command line to share that folder.  Inside your Windows, you will simply use an "NET USE X: <Sharename>" to assign that share to a drive letter.

See section 5.4 of the VirtualBox User Manual.  It has a very simply to follow set of instructions on how to set this up.



Kevin Fries

---

### Post by Pollywoggy on 2007-05-18
I dual boot for games, that is the only reason I have a dual boot system, to play games on the XP partition.
There are a few Windows apps I run in VMware. mostly Quicken, which will run to some extent in Crossover or WINE, but that won't work for games.  For gaming, dual boot is the way to go.

---

### Post by krugman on 2007-05-18
Just a question: someone said that running the two OS from the same HD is not a good idea.
Could you elaborate?

I ask this because I plan to install Ubuntu on my laptop (in addition to Vista) but I would like to run some windows programs thanks to virtual box. However, I only have one hd and a small one what's more (i.e. 80 Gb).Can I still use VB?

Thanks:)

---

### Post by lazyart on 2007-05-18
I can be painful for the hard drive because it's got to work twice as hard reading and writing and paging (using the swap file).

If you can seperate them, by all means do it.  If you spend a great deal of time in the virtual machine you might want to consider getting a 2nd drive for such things.  It good for the life of the drive and better for perfomance- especially if you can put the drives on seperate channels (which is the physical connection to the motherboard).

---

### Post by krugman on 2007-05-18
ok, since my HD is only a 4200 rpm, I guess it is going all the more painful.

I also guess that using separate partition won't help right?

Well, I guess I will have to stick to dual boot...:(

---

### Post by dfreer on 2007-05-18
no a seperate partition won't really make any difference. Your limited by the read/write heads on the hard drive simply having to do 2 the work. Also, since the Virtual machine basically saves all it's data basically in one big file (not actually true in practice) on the linux host, when the windows OS writes something, it buffers it and schedules a good time for it to actually write it, THEN the linux host has to buffer it and schedule a good time to actually write it it creates conflicts (umm something like that anyways). 

A network share with the Virtual machine files would solve your I/O problems, but then you are limited by your network speed (I ran a virtual machine on a server at college from home, a little slow but not that bad considering I had to go through the internet instead of a LAN).

I really want to see if any one has tried this yet (I can't myself as I don't have a computer to do it with :( ), but this may help you. In the ubuntu feisty release notes (or wiki), it talks about rdesktop support. From what it sounds like you should be able to rdesktop into a windows machine and run a windows app in YOUR linux box, in a managed window and everything. You may be limited to having to have a user logged in and only running one app at a time, but this sounds like a great solution. here's the link:

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

