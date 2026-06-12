---
title: "Windows has driver problems too!"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by catlett on 2006-03-29
For all you "haters" of Linux out there, I thought I would enlighten you. Windows isn't trouble free. Most people get windows pre-installed on their system. The hardware manufacturer has techs that write the drivers for their hardware and install them on your computer. If you had to install windows from an installation cd you would have arrors and problems. If you don't believe me follow this link  [http://www.microsoft.com/windowsxp/using/64bit/russel_x64faq.mspx](http://www.microsoft.com/windowsxp/using/64bit/russel_x64faq.mspx) This is Microsofts faq page for Windows XP Pro 64. As you can see by the questions and answers, Microsoft has driver problems as well. For those of you who don't want to follow the link, I'll print the meat of the faq here.  
> Q.	What computers can run Windows XP Professional X64 Edition?
A.	

Windows XP Professional x64 Edition is designed to work with 64-bit processors from AMD and Intel that support the x64 extensions to the x86 architecture. These include the Athlon 64, Athlon 64 FX, Mobile Athlon 64, Turion 64, and Opteron processors from AMD, and the Xeon with EM64T and Pentium 4 with EM64T from Intel.
Q.	Can I run Windows XP Professional X64 Edition on my Itanium Workstation?
A.	

No. The Itanium processor is a 64-bit processor that has a different architecture than the x64 processors. A version of Windows XP for the Itanium processor is no longer available. Windows Server 2003 Enterprise Edition continues to support the Itanium processor.
Q.	Can I run Windows XP Professional X64 Edition on my Centrino laptop?
A.	

No, the Pentium M series of processors used in Centrino laptops are not 64-bit processors and can not use the x64 Edition of Windows XP Professional. There are x64-compatible laptops currently shipping that are based on AMD processors.
Q.	Why is there no Home x64 Edition of Windows XP? Who should buy Windows XP Professional X64 Edition?
A.	

These are closely related questions. The initial target audience for Windows XP Professional x64 Edition is anyone who is running into performance and memory limits on their 32-bit systems, for example, developers, media artists, CAD/CAM, scientific workstations and enthusiasts who are running the most demanding applications, and who require the capabilities of the Professional Edition of Windows XP. Windows XP Home Edition is targeted at the home user and has fewer features. At this point, especially with the current limited driver support, Windows XP Professional x64 Edition is not targeted at the casual home user.
Q.	Why is there no driver for my [Insert your device name here]?
A.	

Windows XP Professional x64 Edition requires that all system drivers be rewritten as 64-bit drivers, 32-bit drivers will not work. The hardware manufacturers are the ones who need to write new drivers, and they're working on it, but it's a resource issue. Writing and certifying a driver takes time and lots and lots of testing. Resources are always constrained, so the manufacturer needs to make a business decision about which hardware has priority for new drivers. This generally means that the focus is on the newest equipment, and older drivers may take a while, or never be done.
Q.	Where is the best place to get drivers for my [Insert your device name here]?
A.	

The best place to get drivers for any device is the device manufacturer. However, if you have a lot of different devices, you may find it awkward to find and get all the drivers you need. The best collection of drivers I've seen to date is on [http://www.planetamd64.com/](http://www.planetamd64.com/). This will undoubtedly change over time, but at the time of this writing, that's where I go when I'm having driver issues and can't get the driver direct from the manufacturer.
Q.	There isn't a 64-bit printer driver for my printer, what can I do?
A.	

First, and foremost, tell your printer manufacturer that you want a 64-bit driver. The more a company hears from their users that they want a driver for a particular model, the more likely they are to shift resources to make sure that driver gets written and tested.
Q.	How do I use the download trial version to make a boot CD?
A.	

The downloadable trial version of Windows XP Professional x64 Edition is an ISO image file, you can't just copy it to a CD, you need to actually burn the image to the CD. For an excellent description of the process with several different software programs, see How to write an ISO file to CD.
Q.	How do I use my SATA drive?
A.	

Many x64 computers use a combined RAID and SATA controller. These controllers do not have native drivers in the released version of Windows XP Professional x64 Edition, so you need to download a driver from your hardware manufacturer, or the manufacturer of the controller, or from one of the community sites that are providing driver agglomeration such as [http://www.planetamd64.com/](http://www.planetamd64.com/). When you have the driver, you'll need to copy the driver files to a floppy disk, and use the F6 option to install the drivers during initial setup.
Q.	The installation goes okay, but the first time it boots up, I get a blue screen? What do I do?
A.	

This is a problem with SATA drives that don't have a correct driver loaded during initial installation. New drivers for x64 require correct "decorations" and while they may appear to be accepted during the text mode phase of installation, they will fail during the initial GUI boot. For more information, read changes for vendor-provided storage drivers loaded using F6.
Q.	My computer needs an updated BIOS, but the BIOS update program only runs in 32-Bit Windows. What do I do?
A.	

This is a tough one until vendors catch up and make their utilities compatible with x64. Until then, your best workaround is to either set your computer up for dual booting, or create a special boot hard drive that runs 32-bit Windows XP. This is a great use for an old 4 to 10 GB hard drive that you have lying around. Open up your computer and carefully remove your Windows XP Professional x64 Edition hard drive. Plug in your spare drive, and install a 32-bit version of Windows XP on it. Or even a copy of Windows 98 if your BIOS update program will run from Windows 98. The key is, don't install anything else on this hard drive – just use it to update the BIOS, and then remove it and put the Windows XP Professional x64 Edition hard drive back in. And meanwhile, complain to your hardware manufacturer about the situation.

---

### Post by WolfJay_83 on 2006-03-29
Verry true, Just look at the (possibly multiple) CD's of drivers that come with any given computer or device.  I don't think I've ever seen a printer or video card without an accompanying driver cd (which you may or may not need ofcourse). Home built computers often require a myriad of cd driver instullations after windows install.

When I installed Ubuntu on my fiance's computer, she presented me with a stack of driver cds.  You should have seen the bewhildered look on her face when I said that linux doesnt need those.  Ubuntu recognized everything and worked fine -bar some minor soundcard issues.

My families DELL machine requires you to go through a browser based driver install of drivers that- no joke, takes me about an hour.

As far as I'm concerned, in this respect, Ubuntu is doing much better than windows.  If those hardware drivers would start helping out, then linux would be miles ahead of windows in terms of compatibility.

---

### Post by NeghVar on 2006-03-29
I feel I must note in the interest of fairness that this is the 64 bit version of windows you are referencing and that this version as is pointed out is not intended for home users but rather businesses that deal with heavy memory requirements and increased performance demands.

The 32 bit version does have problems but the issue here is hardware vendors not Ubuntu or Linux. Some do a good job of putting out Linux drivers while others completely ignore this issue all together.

---

### Post by Coelocanth on 2006-03-29
Keep in mind that's specific to the 64 bit version of Win XP Pro. From what I understand, the 64 bit version of Ubuntu isn't trouble free either.

As for installing drivers, I built my computer a couple months ago and loaded Win XP (Home edition) on it with no troubles whatsoever (this was before I found Linux/Ubuntu). Driver installation was a snap. Once the OS was installed, I had all the updated drivers for my system in very short order.

I'm not saying Windows is the next best thing since sliced bread, nor am I saying Linux isn't, but it's not fair to take a single example and represent it as typical.

As a side note: how many people out there are saying Windows is 'trouble free' anyway? If they are, they're completely fooling themselves.

---

### Post by Sef on 2006-03-29
> I feel I must note in the interest of fairness that this is the 64 bit version of windows you are referencing and that this version as is pointed out is not intended for home users but rather businesses that deal with heavy memory requirements and increased performance demands.

Also too Windows 64 bit version is new.  On the other hand, Unix 64 and Linux 64 bit version has been around for a while.  Which do you think would have the better 64 bit drivers.  (Yes, Unix has been around about 20 years longer than Linux.)  



> The 32 bit version does have problems but the issue here is hardware vendors not Ubuntu or Linux. Some do a good job of putting out Linux drivers while others completely ignore this issue all together.

Which is why HP or Epson printers are recommended over Dell and Lexmark.

---

### Post by catlett on 2006-03-29
I'm not trying to be unfair. It is just that everyone puts an Ubuntu cd in and then screams bloody murder if everything doesn't work out of the box. And they all say they're going back to windows because it doesn't have these problems. Also, the 32 bit version that you get on your computer is loaded with hardware company drivers. Even a 32 bit version weon't necessarily work perfect out of the box. I mainly put it up because XP has the same issue as Linux. The hardware manufacturer makes the driver. And they won't put money into something if they don't think it is profitable. To some of them Linux is not profitable. And now it seems some of them deem 64 bit drivers uhnprofitable. The point of it all is, it is not the operating sytems fault. If the hardware manufacturer hasn't written a driver for your system, you will have issues. Linux does a beter job when the hardware company doesn't write a driver because someone in open source usually tries to write one. Whereas with windows noone is writing an open source driver to help you out.

---

### Post by NeghVar on 2006-03-29
> Also, the 32 bit version that you get on your computer is loaded with hardware company drivers. Even a 32 bit version weon't necessarily work perfect out of the box.

You'll note that I didnt say 32 bit xp will work perfectly. As to the first part I'll assume the broadest possible intention meaning that the oem disc I buy has drivers made by the hw companies, which is certainly true.

If your referring to prebuilt comps like hp, compaq (cousins from hell), dell etc, then get off it man, i have NEVER bought a prebuilt, I have built every single comp I have EVER owned myself. I have had a few problems with drivers on Windows going back to 95, the reason hw companies make drivers is because so many of their users use windows.

As Linux grows so to will the hw maufacturers support for it, and as to printers yes I know hp is good for their linux support, and as far as I know running a cannon on linux is near impossible.

Sorry if some of this seems inflamitory, just a wee bit tired of people assuming the whole world buys their comp prebuilt.

---

