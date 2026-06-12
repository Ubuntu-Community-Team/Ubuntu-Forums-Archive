---
title: "Problem after install ubuntu on new MacBook Pro"
date: 2008-12-20
forum: Apple Hardware Users
---

### Post by jkuiliu on 2008-12-20
i got new mac book (320GB HD, 2.53GHz CPU, 512MB 9600m GT, 4GB of DDR3)
few days ago!! 

struggle on these problems after install ubuntu 8.10

1)no internal sound on my macbook speakers, but i have sound in the headphone;(

2)<*only check the website*> my pc is really hot after running ubuntu for few mins(give it 30mins), but i dont have this problem for running "vista" and "mac self system"

3) no right click on my mousepad, My F12 is my right click;(


:KSplzzzzz help me on these problem.:KS

---

### Post by beauman on 2008-12-20
Unfortunately there is no community help for this hardware available. But for your issues you might get the info from the documantation of the MB 5,1. 

Also, the wiki for the MB 4,1/Intrepid features two different ways of adding right-click functionality. 


This is the entry point for running Ubuntu on Intel CPU-based Mac Hardware: [MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")

**Please confirm**: Your hardware is a MacBook Pro 5,1 (see [Determine your model and hardware revision]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Determine%20your%20model%20and%20hardware%20revision"))

One more thing: If you can spend some time on writing down, what steps you took to get everything running under Intrepid on the MBP 5,1, please come back here.

---

### Post by jkuiliu on 2008-12-21
**MY laptop is MacBookPro5-1/Intrepid**

*i use  boot camp to install vista first(mention can't install xp, give some errors after install). 
*go to vista after reboot, and insert the (mac OS X install dvd) to install boot camp on vista, everything was fine here.
*now install the ubuntu in vista(dont need to reboot vista, just insert the ubuntu cd, then vista will install ubuntu image automatically), then vista will reboot automatically, and ubuntu will install after reboot



:("in install ubuntu 8.10":(
8888888888888888888888888888888888888888888888
problem:
1) after everything done here, i run ubuntu on my machine,
   no sound on my macbook speakers.
2) for just checking websites, computer is getting hotter and hoter,
3) F11 and F12 don't work. i went to <System > preferences > keyboard shortcuts> to set up the key, but F11 and F12 dont work 
8888888888888888888888888888888888888888888888 

[COLOR="Blue"]above problems don't occur in the vista and mac[/COLOR]

---

### Post by beauman on 2008-12-22
> **jkuiliu said:**
> **MY laptop is MacBookPro5-1/Intrepid**

...
*now install the ubuntu in vista(dont need to reboot vista, just insert the ubuntu cd, then vista will install ubuntu image automatically), then vista will reboot automatically, and ubuntu will install after reboot


First, just out of curiosity:
Do you use rEFIt?
How do the partitions on your harddisk look like (size, order, file system)? You can check this in a terminal with

```
sudo gparted
```

[COLOR="Red"](Note: Normally you should never execute commands that are posted somewhere and start with sudo (= execute with sys admin rights), as
long as you don't know the command exactly. You should at least consult the manual of the application, in this case use "man gparted")[/COLOR]


> **jkuiliu said:**
> 
problem:
1) after everything done here, i run ubuntu on my machine,
   no sound on my macbook speakers.


Did you try [community/MacBook5-1/Intrepid#Sound]("https://help.ubuntu.com/community/MacBook5-1/Intrepid#Sound") ?


> **jkuiliu said:**
> 
2) for just checking websites, computer is getting hotter and hoter,

[http://ubuntuforums.org/showthread.php?t=969183]("http://ubuntuforums.org/showthread.php?t=969183") Give me sometime, I have to read it as well. If there is a fix for the problem, somebody should integrate it to the wiki.

> **jkuiliu said:**
> 
3) F11 and F12 don't work. i went to <System > preferences > keyboard shortcuts> to set up the key, but F11 and F12 dont work 


For, the MB I wrote a section on how to map middle and right click to the Apple-/cmd-keys: [community/MacBook4-1/Intrepid/Middle&Right Click with Left&Right Cmd Keys]("https://help.ubuntu.com/community/MacBook4-1/Intrepid#Middle&Right%20Click%20with%20Left&Right%20Cmd%20Keys")
Try if it works on your machine. (Try to note  all your steps, so everybody can see, what you have done.)
Also, a very nice feature is 2-finger-on-mousepad+click=right click: [https://help.ubuntu.com/community/MacBook4-1/Intrepid#Touchpad%20(appletouch)]("https://help.ubuntu.com/community/MacBook4-1/Intrepid#Touchpad%20(appletouch)")

---

### Post by jkuiliu on 2008-12-22
> First, just out of curiosity:
Do you use rEFIt?
How do the partitions on your harddisk look like (size, order, file system)? You can check this in a terminal with

[COLOR="Purple"]***i do use rEFIt!! when i restart my pc, there r 2 Operating system for me to choose, one is mac the other is vista***[/COLOR]

[IMG]file:///home/jack/Desktop/gparted[/IMG]

---

### Post by jkuiliu on 2008-12-22
[IMG]http://file:///home/jack/Desktop/gparted[/IMG]

file:///home/jack/Desktop/gparted

---

### Post by jkuiliu on 2008-12-22
partition filesystem mountpoint label   size    used    unused  flags
/dev/sda1  fat32                  EFI   200MiB  18.1    181.9   boot
/dev/sda2  hfs++                        186.75G 23.64G  163.11G
unallocated unallocated                 128.00Mib
/dev/sda3   hfs+                        30G     12.66G  17.34G
unallocated unallocated                 128.98
/dev/sda4   ntfs     /boot,/host        80.89G  40.69G  40.20G

---

### Post by beauman on 2008-12-22
> **jkuiliu said:**
> partition filesystem mountpoint label   size    used    unused  flags
/dev/sda1  fat32                  EFI   200MiB  18.1    181.9   boot
/dev/sda2  hfs++                        186.75G 23.64G  163.11G
unallocated unallocated                 128.00Mib
/dev/sda3   hfs+                        30G     12.66G  17.34G
unallocated unallocated                 128.98
/dev/sda4   ntfs     /boot,/host        80.89G  40.69G  40.20G

That means you have no partition for Ubuntu, right? Did you install Ubuntu with Wubi? And you can only run Ubuntu as an application under Windows?

---

### Post by Anorexic Leader on 2008-12-22
Okay well I am somewhat similar to jkuiliu's problems.

I own a late Macbook Pro. Got it like 3 months before the new ones. :(

Regardless of model computer, I am running nearly the same triboot setup. I have OS X installed as default, and Vista running via Bootcamp. From Vista I installed Ubuntu 8.04. I didn't want to use 8.10 until I was sure it were fuly stable. My main problem is that my computer randomly freezes shortly after startup. I installed the entire thing this morning and then updated my system. So its up to date, and good to go. The only 2 things I attempted to do was get Wifi and Graphic working. The problems seem to be as follows after enabeling from restricted...

1. Wifi continues to search for networks, and it says its working but nothing is actually connected.

2. Nvidia graphics card received update, but I can't enable the Extra Graphics Setings needed for Compiz, and etc...

From what I have read, it appears that the Nvidia glx drivers for my MBP have caused the computer to lock up. Ubuntu lets me get all the way into my desktop and then it freezes after a few seconds. 

I used to try and run Ubuntu in VMWare Fusion while in OS X. But that of course made several problems. It wouldn't let me enable my resticted drivers (so no compiz) and my sound didn't work.

From my experience with buddies computers, the sound shouldn't be a huge pain, but it appears that graphics are...espcially since Jkuiliu is using the 9600gt in the new Macs with the latest build of Ubuntu. Good luck sir.

So I'm in a rather similar boat to say the least.

---

### Post by cyberdork33 on 2008-12-22
> **Anorexic Leader said:**
> I used to try and run Ubuntu in VMWare Fusion while in OS X. But that of course made several problems. It wouldn't let me enable my resticted drivers (so no compiz) and my sound didn't work.

I think today's latest release of virtualbox supports 3d acceleration :) (also adds vt-x support for OSX which makes things run much faster :) :) )

---

### Post by Anorexic Leader on 2008-12-22
Thanks Cyber, I'll have to check that out...then I'll report back to here if I get it running right.

---

### Post by beauman on 2008-12-22
> **Anorexic Leader said:**
> ... I am running nearly the same triboot setup. 

As I understood so far, jkuiliu has a dualboot system only with OS X and Vista.

Sorry for being a bit lame here, but I like to understand this point. Are you running Ubuntu as an application under Vista, or is Ubuntu running as the one and only operating system, that should be responsible for the fan control for example, that jkuiliu complained about originally?

---

### Post by Anorexic Leader on 2008-12-22
I would have a third partiton on my drive for Ubuntu. But, I didn't want to possibly lose all of my OS X or Vista installs and files associated with. I got backups, but that's still a pain. From what I've read on other sites for research, It is possible to have 3 partitons on a Macbook, but it's rather stingy and bootcamp is evil when it comes to more than 2. You have to go in a rewrite all sorts of fun things.

I have OS X on my internal.

Vista on internal via Bootcamp.

and Ubuntu 8.04 two ways. 1 under OS X as a virtual that doesn't let me use my graphics card in VMWare, and 1 that I have to select seperately when starting up Windows. It is installed on the partition that I have alotted for Windows, but in no way can I access any of my Windows files while in Ubuntu. So in my eyes, this appears to be 3 different operating sys running all natively on my MBP, but of course only 2 partitions. Am I right? This brings me to my next question...

So I instaled Ubuntu using 7 gigs of free space out of the 9 gb I had left on my Windows partition. I generaly only use windows for games, so it was a small partition and not much room was left. I am new to Ubuntu, and **currently** do not plan to use it as my primary OS. So I figured a small install of Ubuntu would be perfect...

While looking around through things on my newly installed flavor, I find that I cannot find an extension to view the files on my Windows partiton, but instead I am able to view several of my files from my Mac's HD. I find this odd, since technically I am on the Windows partition (which of course doesn't recognize the mac's jounrnaled volume) yet I can view the contents of the opposite drive under Linux. I'm sure you all knew this already, but as a newer user to Ubuntu I found it quite intriguing.

So my other question is, if my Windows install file is only 7 gigs, then why can I see the other 80ish gigs remaining of free space on the Mac HD, and is it now safe to write and save files to it?

I mean if I can see it and its free space, that to me seems like its perfectly fine in my book. Just asking here of course for good measure.

Regardless the real issue at hand is the fact that my install of Ubuntu is freezing up and I need to get bacl to low graphics mode or terminal that will allow me to undo the nvidia graphics card update and assign the proper one instead... what about ENVY drivers?

---

### Post by beauman on 2008-12-23
We are discussing two different problems here in one thread, one about a MBP5-1 getting hot under Ubuntu and having problems with mouse emulation, the other about Ubuntu freezing on a MBP4-1.

Perhaps the best thing would be for both of you to start a new thread. When you post a new thread, please try explain in detail, how your setups differ from the standard setup, where Linux is installed into a dedicated ext2/3 partition and is started with the help of a bootloader at system startup. State exactly, how you boot into it.

@jkuiliu: did you have a closer look at the wikis? Any progress with right click emulation?

---

### Post by jkuiliu on 2008-12-23
1) [COLOR="Blue"]under mac system[/COLOR] :use boot camp to install vista(for games here;D),after install vista insert the install DVD from(MacBook Pro), it will install boot camp automatically. after this, everything will be work perfectly under vista. 

2) [COLOR="Blue"]under mac system[/COLOR] :  use disk utility to make separate partition(i made 30g);use [COLOR="Red"]VMware Fustion[/COLOR] to install ubuntu under this partition.

after these simple steps , u will get everything work:D 
*internal sound work under ubuntu (ubuntu8.10-----but not after update ubuntu8.10)
*laptop is no more hot
*morsepad is worked, u can use 2 fingers scroll. right click as well;D

-------------------------------------------------------
Thx everyone for repling on this thread!! Mary Christmas:P
-------------------------------------------------------

---

### Post by beauman on 2008-12-23
:) Great! Have fun with your install!

Same to you!!

---

### Post by Anorexic Leader on 2008-12-23
Yea I can understand that doing what Jkuiliu did will work, but keep in mind that he has a brand new system...most likely there are not many files on his computer already. There is not really a risk for him at the moment to be making new partitions and installing things. There is nothing really there to lose. I on the ohter hand do not wish to take the risk of possibly losing all my files or my OS installs in neither OS X or Vista, regardless of backups. Vista runs fine for me, but now I'm having a new problem with Ubuntu while booting up from my windows partition. I would describe it, but I'll just go make a new thread...

Early Merry Christmas everyone! XD

---

### Post by cyberdork33 on 2008-12-24
> **Anorexic Leader said:**
> Vista on internal via Bootcamp.

and Ubuntu 8.04 two ways. 1 under OS X as a virtual that doesn't let me use my graphics card in VMWare, and 1 that I have to select seperately when starting up Windows. It is installed on the partition that I have alotted for Windows, but in no way can I access any of my Windows files while in Ubuntu. So in my eyes, this appears to be 3 different operating sys running all natively on my MBP, but of course only 2 partitions. Am I right? This brings me to my next question...
So, you used WUBI?

> **beauman said:**
> We are discussing two different problems here in one thread, one about a MBP5-1 getting hot under Ubuntu and having problems with mouse emulation, the other about Ubuntu freezing on a MBP4-1.yes, please!

> **jkuiliu said:**
> 1) [COLOR=Blue]under mac system[/COLOR] :use boot camp to install vista(for games here;D),after install vista insert the install DVD from(MacBook Pro), it will install boot camp automatically. after this, everything will be work perfectly under vista. just a side note, the newest version of bootcamp from the apple website will have updated drivers for Windows!

> **jkuiliu said:**
> 2) [COLOR=Blue]under mac system[/COLOR] :  use disk utility to make separate partition(i made 30g);use [COLOR=Red]VMware Fustion[/COLOR] to install ubuntu under this partition.
hmm, if you are running Ubuntu in VMWare Fusion, then you do not need to make a separate partition. VMWare uses a had drive image file (virtual hard drive) to install to.

---

### Post by jkuiliu on 2008-12-24
> **cyberdork33 said:**
> So, you used WUBI?

yes, please!

just a side note, the newest version of bootcamp from the apple website will have updated drivers for Windows!


hmm, if you are running Ubuntu in VMWare Fusion, then you do not need to make a separate partition. VMWare uses a had drive image file (virtual hard drive) to install to.

##########################
thx for ur additional information!!
#########################
Merry Xmas

---

