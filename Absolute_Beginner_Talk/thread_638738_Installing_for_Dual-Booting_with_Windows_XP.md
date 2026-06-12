---
title: "Installing for Dual-Booting with Windows XP"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by suttles95 on 2007-12-12
I would like to install Ubuntu as a dual-boot with Windows XP, but I have lost my XP restore disk.

Is there a way for me to create a restore disk myself? If so, could I create it on a CD-RW, or does it have to be a CD-R?

Also, are there any disadvantages to dual-booting? Do I lose any functionality? Will all of My Documents (MS Office, videos, pictures) work in both Ubuntu and Windows?

Lastly, I am completely illiterate to coding...is there a link to simple instructions for installing as a dual-boot?

--Brian

---

### Post by aysiu on 2007-12-12
If you have at least 512 MB of RAM, think about installing Ubuntu as a virtual operating system inside Windows:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Then you run no risk of losing Windows and not being able to replace it.

---

### Post by suttles95 on 2007-12-12
I could...

But one reason I'm interested in using Ubuntu is because I'm tired of the typical Windows lag and lock-ups...

If I did that, would I actually be using Ubuntu and not Windows?

How can I tell if I have that much space available?

Do you know how I can create a Windows restore disk myself?

---

### Post by aysiu on 2007-12-12
> **suttles95 said:**
> I could...

But one reason I'm interested in using Ubuntu is because I'm tired of the typical Windows lag and lock-ups...

If I did that, would I actually be using Ubuntu and not Windows? Aye... there's the rub. Installing Ubuntu as a virtual OS inside Windows would require you to boot into Windows and then launch Ubuntu within Windows.

> How can I tell if I have that much space available? It doesn't take much space (about 4 GB to start). As a matter of fact, in VirtualBox, you can choose to have the virtual hard drive start small and expand as needed.

> Do you know how I can create a Windows restore disk myself? Maybe with Acronis or Norton Ghost?

---

### Post by 720iD on 2007-12-12
i am sure you can do what you are wanting to do using nLite

---

### Post by suttles95 on 2007-12-12
What are Acronis or Norton Ghost?

---

### Post by aysiu on 2007-12-12
> **suttles95 said:**
> What are Acronis or Norton Ghost?
They're backup tools that will restore your hard drive to its exact previous state:
[http://www.acronis.com/homecomputing/products/trueimage/index.html](http://www.acronis.com/homecomputing/products/trueimage/index.html)
[http://www.symantec.com/norton/products/overview.jsp?pcid=br&pvid=ghost12](http://www.symantec.com/norton/products/overview.jsp?pcid=br&pvid=ghost12)

---

### Post by suttles95 on 2007-12-12
nlite sounds interesting...can anyone tell me what that does or how I can use it?

---

### Post by eolson on 2007-12-12
Call the manufacturer and tell them you need a new disk.  Have the serial number of your machine, the windows product key etc. handy.  After a lot of questions and carrying on they'll send you a replacement.

---

### Post by gaelfx on 2007-12-12
Well, I have a dual-boot system set up, and  I can tell you a few things about my experience.
Firstly, most everything will probably carry over easily. Most things produced by MS Office are usable in OpenOffice.org, which, if you don't know and haven't used, is very similar to MS Office. Pictures should also work pretty easily without a hitch. The two problem areas I expect you will encounter are partitioning the drive properly, which the installer for Ubuntu should help you greatly with but can be confusing, and switching from one OS to the other. For the former, I suspect you can easily find a solution searching through this forum for a little bit. For the latter, you may have to use a program called Terminal to change some files to make it easier, which will probably seem a little like coding, but that shouldn't deter you.
Ubuntu uses something called Grub to load the operating system, and normally you are given three seconds a little while after you turn on your computer to change which system it loads, but this can be changed. If you open Terminal after installing (it's in Applications -> Accessories -> Terminal), you should type this:
```
sudo fdisk -l
```
This command is Super-user Do (sudo) fdisk -l, which tells you about your partitions, which is basically telling you how your system has named the parts of your disk that hold Windows and which parts hold Ubuntu, etc.
The one that holds Windows is probably the first line you see that has HPFS/NTFS under the heading 'System'. At the beginning of the line, it should say something like /dev/sdaX, where X is a number, in your case, probably 1. Let's just say that it is 1.
Next, you should do this:
```
sudo gedit /boot/grub/menu.lst
```
This is a long file and it may seem hard to read, but you can read some of it if you want, you may learn some useful things. At the end of the file, there should be a line that says "### END DEBIAN AUTOMAGIC KERNELS LIST". Before this line, enter this:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
Remember that X from before? Well, this is where it matters most. We have assumed that X=1. If X=2, then enter this:
```
title Windows XP
root (hd0,1)
makeactive
chainloader +1
```
So basically, you should really enter this (replacing X-1 with the appropriate value):
```
title Windows XP
root (hd0,X-1)
makeactive
chainloader +1
```
I hope this helps you, it helped me a lot in getting back to my Windows.
You should notice that when you start up your computer, it says "Grub loading stage 1.5..." or something like that. This is when you need to hit ESC to see the Grub menu and load whichever system you want at the moment.

---

### Post by suttles95 on 2007-12-12
gaelfx:

Those instructions sound great...and I can probably follow them easily...

And will I be able to do this without the OS disk...(eMachines doesn't have an OS disc and will charge $20 to send me a restore disk)...

And everything should transfer correctly?

---

### Post by aysiu on 2007-12-12
I've installed a few dual-boots in my day, and I've never had to do any kind of X-1 thing.

If all goes well (which probably happens about 80-90% of the time), Ubuntu should automatically create the proper boot option in the /boot/grub/menu.lst file for Windows. Extra tweaking is a workaround if something goes wrong. It is not the norm.

More details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by gaelfx on 2007-12-12
Well, when you install a dual-boot, it should leave everything on the Windows as is, but it is always better to have a restore disk in case something goes awry. I'm not sure about how to make a restore disk since I have never needed one. I installed Windows AFTER I had Ubuntu on my disk already, so I have the Windows disk to reinstall if need be. If the installation goes through properly, then you should be able to access anything on the Windows part of your disk by going to Places -> Computer, and then double-clicking the Windows disk (which you will only recognize by its size). You will have to enter your Root password, which is the one you enter when installing Ubuntu, to access it, but all the files should be available there. I'm not sure about encrypted files or password-protected files, but if you haven't done anything overt to protect your windows files, you ought to be able to access them once you install Ubuntu. But it might be wise to use the LiveCD version of Ubuntu for a while before you decide to fully install it. It will run slower in the Live version, but it may help you get a feel for how Ubuntu works and whether or not you like that. Just remember, there is always the risk that something can go wrong during installation, and if you aren't comfortable with that, then don't do anything until you have figured out how to create a restore disk. Otherwise, if you're feeling brave, I say go for it! Losing my dependency on Windows was one of the happiest days of my life ;)

---

### Post by eolson on 2007-12-12
> **suttles95 said:**
> gaelfx:

Those instructions sound great...and I can probably follow them easily...

And will I be able to do this without the OS disk...(eMachines doesn't have an OS disc and will charge $20 to send me a restore disk)...

And everything should transfer correctly?


that's strange,  they sent me one for free for my laptop.  Just told them there wasn't one in the box when I bought the machine (there wasn't).

---

### Post by gaelfx on 2007-12-12
Aysiu is right, hopefully, you shouldn't have to do any of that. As I said before, I installed my Windows after installing Ubuntu, so I had to do a little working around, but if, for whatever reason, you are unable to boot Windows again, you should be able to use my instructions, which did come from the deep reaches of this forum (so I can't really take credit for them). Just remember that Grub is your gateway to other systems.

---

### Post by johnnybirdman on 2007-12-12
> **aysiu said:**
> If you have at least 512 MB of RAM, think about installing Ubuntu as a virtual operating system inside Windows:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Then you run no risk of losing Windows and not being able to replace it.

If I'm running 32-bit windows can my virtualbox run a 64-bit OS (I have a core2 currently running 64-bit 7.10)?
Also, can you run multiple virtualboxes at the same time?  Run an Ubuntu desktop and server at the same time?  Does the virtualbox OS get it's own IP address?

---

