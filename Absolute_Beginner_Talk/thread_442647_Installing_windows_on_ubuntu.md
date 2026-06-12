---
title: "Installing windows on ubuntu?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Ramthebuffs on 2007-05-13
Is this possible?  I've just realized that I need windows on this computer on occasion.  I thought I would just be quick and throw in a windows boot disk and start with windows and follow some simple instructions on adding ubuntu as a dual, but it won't read for some reason.  None of my windows boot disks will read on startup, but the ubuntu disk will read on startup.

I'm willing to totally reformat the disk to blank and start from there but I don't even know how to do that.

---

### Post by wormser on 2007-05-13
You can install VMware Server and run windows in it.

---

### Post by Ramthebuffs on 2007-05-13
I was just thinking, I won't even be able to pop the drive into my other desktop and reformat that way will I?

---

### Post by lazyart on 2007-05-13
You can run VirtualBox and create a virtual machine within Ubuntu.  I just did this and it's real easy to pull off.

---

### Post by wormser on 2007-05-13
I am not exactly sure what you are asking.  VMware is a program that lets you install other operating systems in it.  So, you open VMware Server and install XP or whatever into  it.  There is no reformating.

---

### Post by Ramthebuffs on 2007-05-13
The reason I need to reformat is because I need to be able to communicate with my serial cable to a satellite box and I don't think this is possible without @ least having a dual boot.  I'm not good enough with linux to really try and figure out how to use the serial otherwise.

---

### Post by Nythain on 2007-05-13
just a note, virtualbox is just as good, and some say better than vmware, and FREE

---

### Post by LostArt on 2007-05-13
You could use Win4Lin for windows emulation. Wine and cedega will run games, If you're trying to dual boot enter the boot menu on startup, for instance on my computer when Toshiba flashes on the screen I hit F12 and I enter the boot menu, then choose boot from cd and the disk will load first, allowing you to use windows install disk bada bing bada boom, that is if you've already partitioned your hard drive, if you haven't done that, make a live cd of the ubuntu partition software (don't remember what it's called, but someone will know) then boot from the cd and you can partition the hard drive.

And there you have it

---

### Post by Ramthebuffs on 2007-05-13
The problem is that the windows disc won't boot.  Its an original xp disk that I used to setup this computer when I built it.  I have boot from CD first on my boot list and the ubuntu cd will boot just fine, but none of my XP discs boot @ startup.

---

### Post by veloce on 2007-05-13
> **Ramthebuffs said:**
> The problem is that the windows disc won't boot.  Its an original xp disk that I used to setup this computer when I built it.  I have boot from CD first on my boot list and the ubuntu cd will boot just fine, but none of my XP discs boot @ startup.

If none of your windows discs will boot, then none of the solutions recommended will work (unless Wine can access a serial port - anyone confirm/deny?).

If you can borrow a windows disc that will boot, then you could use the reg key from your own disc for a legal install.

VMWare Server WILL allow you to access your serial port.  Also, while there seems to be some residual confusion about this from virtualbox supporters, vmware server is FREE (though only as in beer, not as in speech).  The bonus is, provided you have reasonable hardware, XP may run better as a vm than native! (It certainly does on my centrino duo with 1Gb RAM).

---

### Post by Ramthebuffs on 2007-05-14
I'm about to throw this HD @ the house across the street.  I was enjoying ubuntu, but this is really spoiling the last month I've had it.  I've read about making a bootable dos disk, but I don't have a floppy available.  I'm so frustrated, I've been trying to fix this for about 6 hours now with less than 0 progress.

---

### Post by Zuuswa on 2007-05-14
Have you at least tried these people's suggestions about running xp in a virtual environment?  It sounds like this would be your solution, as VMWare *can* utilize the serial port.

---

### Post by irish_flu on 2007-05-14
My box is really flaky about booting to some (perfectly fine) CDs too, man.  I just had to restart my Windows box (which I just threw a clean new HD in) about ten times before it would boot to my XP CD.  I have no idea why.

Do you have another CD or DVD drive you can try?  Maybe it's just a little flaky.

You've probably already thought about this, but you're not missing a really quick "press any key to boot to CD", are you?

You might also try (if your BIOS supports this) removing the HD from the boot order completely.  After setup finishes and directs you to reboot, you can add the HD back into the boot order.

---

### Post by Ramthebuffs on 2007-05-14
yeah I've tried a lot of things, I've moved the boot order around, I've tried booting with a disconnected HD, I put the HD into my other desktop to see if it was the disk drive, but I still couldn't get a boot.

---

### Post by lazyart on 2007-05-14
Try to make an .iso of the disk, then use that .iso to boot into a virtual machine in VirtualBox (or presumably in vmware though I've never used it)

---

### Post by Ramthebuffs on 2007-05-14
If I use one of the utilities that claims to completely wipe a drive would this solve my problem?  Well enough to not have any remnants of grub?

---

### Post by Campingman on 2007-05-14
Forgive me if I am reading this wrong
If you have decided you need to format your hard drive and the Ubuntu live CD boots fine, you should be able to format from Gparted within the live CD environment.
I cannot understand why anything on the hard drive would prevent the computer from booting from the cd as the bios is looking at the CD before the hard drive?

---

### Post by Ramthebuffs on 2007-05-14
I'm not really sure, I'm not a hardware wizard.  I just throw the pieces together and they work.  But like I said I put the drive in a different computer with the same windows disk and got the same problem.

---

### Post by lazyart on 2007-05-14
> **Ramthebuffs said:**
> I'm not really sure, I'm not a hardware wizard.  I just throw the pieces together and they work.

Since you admit you are not a hardware wizard, please listen when we tell you that formatting the hard drive is not going change a single thing about booting from CD.

Either your CD readers need cleaning, or the media is scuffed up and scratched up or otherwise been rendered unreadable... 

You can remove Ubuntu but you still won't be able to read the disk.  If the Ubuntu CD works in other drives but the Windows disk does not... doesn't that tell you something?

---

### Post by Ramthebuffs on 2007-05-14
Maybe theres something else I can try then?  Perhaps some sort of boot disc from bootdisc.com that will allow me to run some sort of barebones windows so I can then insert my windows disk and install from there.

The disk loads fine when windows is running, and like I said before its what I used as the original op when I built the computer.  Any ideas.

---

### Post by veloce on 2007-05-14
> **Ramthebuffs said:**
> Maybe theres something else I can try then?  Perhaps some sort of boot disc from bootdisc.com that will allow me to run some sort of barebones windows so I can then insert my windows disk and install from there.

The disk loads fine when windows is running, and like I said before its what I used as the original op when I built the computer.  Any ideas.

The best suggestion so far was the one about making an iso from the disc and trying to use it in a vm to install windows into the vm.  This may or may not work, but it is the best idea to try next.

---

### Post by esoterica on 2007-05-14
The version of VMWare that would actually allow you to install Windows from your own CD is definitely not free, in fact it's rather expensive. The free version of VMWare only lets you install already put together Vitrual Machines that other people have built on the high priced paid version and offer to you. Due to Windows Licensing issues you will not find a copy of Windows that will be able to run on the free version of VMWare, nor can you install Windows on only the free version of VMWare, you'd have to purchase a paid version, which would be a waste of money.

Anyhow, onto your problem.

Your Master Boot record sounds like it's been linuxfied (not a real word, I just made that up). The only way I know of for you to fix this would be to have an old school Windows boot disk that actually still had DOS on it and allowed you to run dos commands from it. Like a Windows 98 recovery or repair disk I think being the newest of which you would still be able to do this with if you have one, and those were only directly able to be created on floppy, so you'd need a floppy drive as well.

My guess is that this isn't a working solution for you either because of the floppy drive handicap or lack of such a disk in your possession. The bootable XP and newer disks do not allow you to run DOS so it isn't going to work for what you need to do.

Once booted into actual DOS, that is if you can find a disk out there somewhere that will run and boot to DOS you need to repair your Master Boot record. This is done in DOS by running the command...

FDISK /MBR

Which will then un linixfy your master boot record and allow the drive to once again boot with Windows

Fear not, I have a more drastic alternative for you as well if that isn't a working option for what ever reason.

You can follow my directions I made in this post earlier today...

[http://ubuntuforums.org/showthread.php?t=443400](http://ubuntuforums.org/showthread.php?t=443400)

My instructions in that post will get you 100% fresh and clean on the hard drive, you will loose absolutely everything you may have on this drive, but in reading your requests it sounds like you don't care about that, just want a fresh start. That post will get you a fresh start if you follow my directions to the letter and don't attempt to modify them into what you think may be ok. Straying from doing it EXCATLY like I said it will make your drive worth nothing more than throwing against the house.

Lastly, all Linux users please close your eyes and do not read this next section of my post.

Ok, now that none of the Linux users are reading this part I'll offer another suggestion to you.

It sounds like your a lot more comfortable using Windows, understood, but have a serious interest in learning Linux, also understood.

Dual booting is an easy alternative (install windows first, then install Linux, not the other way around like your trying to now do). Dual booting is however not the best solution, in fact it's actually a pretty bad solution.

My suggestion to you is to go ahead and folow my advice in the other post I linked to above, get the drive back to 100% fresh and clean and go ahead and reinstall a frwsh copy of Windows on your drive. Go ahead and give Windows the entire drive. I suggest this because your going to be more stable and comfortable doing it this way since your use to Windows.

Now download this and install it...

[http://www.microsoft.com/windows/products/winfamily/virtualpc/overview.mspx](http://www.microsoft.com/windows/products/winfamily/virtualpc/overview.mspx)

It's called Virtual PC 2007, it's from Microsoft so it will run well with XP and Vista, a lot less problems than some of the other alternatives out there, either free or paid for. It's also very easy for a typical Windows user to set up, run and manage, also unlike some of the other alternatives (I know because I have actually tried all of them first hand myself, not just read about them somewhere). Even though it comes from Microsoft it is 100% free. They try not to over emphasize the ability to run Linux on it, but if you dig through the documentation a little you'll see that running Linux on it is fully supported.

Once you have Virtual PC 2007 installed you can easily install your Ubuntu Linux and run it in a Window, either maximized, or a restored down Window. It also lets you easily drag and drop files between the host operating system (in your case Windows) and what ever other operating system your running it on. You'll be able to do what ever you want in either Operating System just as if both were installed on real and actual separate computers. With the added advantage of not having to reboot around each time you want to switch Operating Systems on the same computer. Also if you hose up your Linux install you don't end up with a mess fixing things like your seeing can happen right now, you'd just delete the Linux install from your Virtual PC and install another copy of it. Or save a copy of the install folder before you mess with it and then jkst delete the experimental one and revert back to your working "install".

I personally think you'll find this option to be a lot less stressing as you either make the migration to being comfortable enough with Linux to do away with Windows completely, or at least comfortable enough to use it as your primary Operating System instead.

There you have a fix and a solution to all of your current problems.

---

### Post by esoterica on 2007-05-14
P.S.
Since I'll likely never find this post again, if you want to PM me with the exact model and brand of your hard drive I'll help you locate and make sure you get the absolute correct utility for your specific drive incase you have any doubts.

---

### Post by veloce on 2007-05-14
> **esoterica said:**
> The version of VMWare that would actually allow you to install Windows from your own CD is definitely not free, in fact it's rather expensive. The free version of VMWare only lets you install already put together Vitrual Machines that other people have built on the high priced paid version and offer to you. Due to Windows Licensing issues you will not find a copy of Windows that will be able to run on the free version of VMWare, nor can you install Windows on only the free version of VMWare, you'd have to purchase a paid version, which would be a waste of money.


Your information on vmware is significantly out of date (i.e. WRONG).  Vmware **server** is free.  It is also now included in the Feisty repositories (the commercial one) so it is a trivial install.

Yes you need a copy of windows that is legally allowed to be run on your machine.  I have the windows XP that came with my machine installed in a vm on this machine.  There is nothing in the licensing to restrict this.  It would be a breach of the license agreement to use this vm on another host, but no problem on the hardware for which it has the license. (This changes under  for  Vista).

---

### Post by esoterica on 2007-05-14
I must be getting confused by VMWare Player and VMWare Workstation because the one is worthless and the other is far from free.

None the less he isn't going to be able to do anything with it if he can't get the WIndows install CD he has to work on it unless he can at least access the CD once in Linux and copy over the entire I386 directory on the Windows install CD to install from it. If he can get that directory copied over somewhere he'd still need to be able to run Windows commands to fire off the install by running either WINNT.EXE  from a booted VMWare MS DOS installation or WINNT32.EXE from a booted VMWare install of another Windows Operating System that has a GUI.

I've run Windows XP before from the VMWare Workstation version and it was a total pain in the butt because of XP's registration crap, it's by far a lot easier to do it the other way around and run Linux as the Guest Operating System instead if your the type of person who doesn't like dealing with and fixing problems and instead want some solid reliability.

I'm glad you pointed out that VMWare server is easily installed from within Ubuntu though, I didn't know that. I actually have an old copy of Windows 2000 still I'd like to install just because I'm a web developer and actually need some way to run IE6 for testing web development work I do. I had been using Windows Virtual PC  just for this reason, but if I can do away with having to run a Windows box specifically for this reason that would make my day.

---

### Post by veloce on 2007-05-14
> **esoterica said:**
> 

None the less he isn't going to be able to do anything with it if he can't get the WIndows install CD he has to work on it unless he can at least access the CD once in Linux


Agreed.  However, I have had success with getting a vm to boot from an iso created from a disc that wouldn't boot natively.  

It may not work, but I'd have said it was worth a go.

> **esoterica said:**
> 
I've run Windows XP before from the VMWare Workstation version and it was a total pain in the butt because of XP's registration crap, it's by far a lot easier to do it the other way around and run Linux as the Guest Operating System instead if your the type of person who doesn't like dealing with and fixing problems and instead want some solid reliability.


Yes, m$'s registration crap is a pain.  I have a valid licence to use XP Pro and Office Pro on this machine so I was adamant that I was going to do so!  With windows I had no trouble.  With Office I had to ring the support centre and assure the person that I was using it on the machine that it was supplied with.

I keep a backup of the original vm, because if you change the vm configuration too much it kills the registration!  ("Your hardware has changed significantly...")

There is a significant performance improvement from running Ubuntu as the host - it does memory management so much better. (And smp in windows is a joke comparitively.)

---

### Post by edimania on 2007-05-15
I just had to format my entire drive (using gpardet from the U. Live CD) becuase my disk was as someone said "linuxfied", you also mentioned that it can be fixed by using some DOS command (FDISK /MBR), theoriticaly should that work also with the FIXBOOT or some other command from the Recovery Console (Using the Windows Boot CD)? It did not work for me though. 

I really like Ubuntu and now that they will work together with Linspire it will probably improve a whole lot more. 
But until I can have completely the same word, presentation, sheet editing as in Microsoft Office (installing it through WINE or CrossOver does not fix the problem, it crashes over and over again) it's a pain.

---

### Post by veloce on 2007-05-15
> **edimania said:**
> 
my disk was as someone said "linuxfied", 

You say that like its a bad thing! :) 

> **edimania said:**
> 
I really like Ubuntu and now that they will work together with Linspire it will probably improve a whole lot more. 
But until I can have completely the same word, presentation, sheet editing as in Microsoft Office (installing it through WINE or CrossOver does not fix the problem, it crashes over and over again) it's a pain.

If you are stuck on M$ Office then you are better to stick to Windows.  

I'm keen to complete my shift to Open Office but have a number of word and excel macros that need conversion.  I am also unlikely to get away from M$ office for work for a considerable time.

So I use vmware server for all my m$ office work now.  I currently have a virtual machine running via rdp fullscreen on one screen where I am developing  a spreadsheet model for a client and on the other screen I have Evolution, Firefox, Vmware console, Rythmbox, and two terminals. (And that's I'm typing this post).  Works really well for me.

---

### Post by ucjb on 2007-06-29
Run VMware Converter on you windows box, that will create the VM files for your XP VM then start Ubuntu download and run VMware server point the VM to the files you created with the converter

Now you have your XP running on your Ubuntu whenever you need it

---

