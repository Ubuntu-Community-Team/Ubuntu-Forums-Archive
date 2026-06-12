---
title: "Apple Intel Users FAQ"
date: 2007-07-04
forum: Apple Hardware Users
---

### Post by Gen2ly on 2007-07-04
*[COLOR="DarkOrange"]Welcome to the Apple Users Forum!  This Faq is designed for Apple Intel Users.[/COLOR]*

If you have a question, feel free to ask it in the forums - a fair number of forum users are very willing to help.  Likewise, alot of answers can also be found here.  To help avoid replicate threads it is requested to search the topic concerned before posting a new topic.


**[COLOR="DarkRed"][SIZE="5"]Installation and Basic Setup[/SIZE][/COLOR]**

[**[COLOR="Sienna"]The MacBook Ubuntu Wiki[/COLOR]**]("https://help.ubuntu.com/community/MacBook")
[LIST]
[*]Covers details of installing Ubuntu on a MacBook.  First time users best start at the wiki.
[/LIST]
[**[COLOR="Sienna"]The iMac Ubuntu Wiki[/COLOR]**]("https://help.ubuntu.com/community/Intel_iMac")
[LIST]
[*]Covers details of installing Ubuntu on a iMac.  MacBook and iMac installtion are very similiar.
[/LIST]
[**[COLOR="Sienna"]Bluetooth Setup[/COLOR]**](https://help.ubuntu.com/community/BluetoothSetup)
[LIST]
[*]If you use a short-distance wireless device this has some nice information.
[/LIST]
[**[COLOR="Sienna"]HOWTO: iSight[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=764616")
[LIST]
[*]How to get your iSight camera running.
[/LIST]
[[COLOR="Sienna"]**HOWTO: Synaptics Touchpad**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=493758")
[LIST]
[*]A Touchpad tutorial - the touchpad has alot of configurations.
[/LIST]


**[COLOR="DarkRed"][SIZE="5"]Advanced Posts[/SIZE][/COLOR]**

[**[COLOR="Sienna"]HOWTO: Compile a Kernel for your MacBook[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=442941")
[LIST]
[*]More advanced users can to compile their own kernel.  This provides advantages over general kernels that can be a bit slower, and not as nicely tuned to your system.
[/LIST]
[[COLOR="Sienna"]**Benanzo's post on Howto Compile Madwifi Drivers**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25")
[LIST]
[*]Compile the madwifi drivers from scratch.
[/LIST]
[**[COLOR="Sienna"]Howto Check and Repair HFS+ Drives/Partitions in Ubuntu[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494")
[LIST]
[*]Darwin utilities provide a way to check and repair HFS+ drives from within Linux.  Here's what needs to be done to build them.
[/LIST]

---

### Post by cyberdork33 on 2007-10-30
[B][SIZE=4][COLOR=DarkRed]Before Posting anything:[/COLOR]
[http://ubuntuforums.org/showthread.php?t=869215](http://ubuntuforums.org/showthread.php?t=869215)[/SIZE][/B]

**[COLOR=DarkRed][SIZE=4]Hardy / Intrepid Installation BUG:[/SIZE][/COLOR]**
If you have problems booting Ubuntu after installing Ubuntu 8.04 or 8.10, please see this link. There is a bug in the Ubuntu installer.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

**[COLOR=DarkRed][SIZE=4]What is the Mactel-Support PPA?[/SIZE][/COLOR]**
A lot of threads and how-tos may mention the mactel-support ppa. This is a community-maintained repository containing software fixes for Intel Macs. A full description of each package in the PPA and what it is for can be found in this link:
[https://wiki.ubuntu.com/MactelSupportTeam/PPA]("https://help.ubuntu.com/community/MactelPPA")

[B][COLOR=DarkRed][SIZE=4]Advanced Topic: GRUB2 / GRUB-EFI
[/SIZE][/COLOR][/B]If you'd like to experiment with booting Linux without BIOS emulation, directly via EFI, check the following thread for info.
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)
[B][COLOR=DarkRed][SIZE=4] 
Additional Posts Useful to Intel-Mac owners.[/SIZE][/COLOR][/B]

_[**32-bit or 64-bit (i386 vs AMD64)?**]("http://ubuntuforums.org/showthread.php?t=765428")_
[LIST]
[*]If you have a Core2 CPU (sorry Core(1) is only 32bit), then you might wonder which version of Ubuntu to use.
[/LIST]
 _[**Using NDISWrapper with the Broadcom 4328 Wi-Fi Card**]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4")_
[LIST]
[*]This card is used in the Intel iMacs as well as the new SantaRosa Macbooks (>Macbook2,1) and Macbook Pros (>MacbookPro3,1)
[*]There seems to be a problem with ndiswrapper and Ubuntu Studio. Try using the generic linux kernel rather than the rt kernel.
[/LIST]
_[**Booting from External (USB and Firewire Drives)**]("http://ubuntuforums.org/showthread.php?t=510030")_
[LIST]
[*]There are issues with booting legacy OSs (Read Linux) from an external hard drive or flash drive. Some have supposedly got it to work.
[*]If you have a Mac Mini, you can get it working. See [this thread]("http://ubuntuforums.org/showthread.php?t=869324") for information.
[/LIST]
_[**Set Macbook (Pro) Fan Speeds**]("http://ubuntuforums.org/showthread.php?t=611596")_
[LIST]
[*]Macbook owners can get a lot of control over their fan speed if they feel the machine is getting too hot.
[/LIST]
_[**Mac Pro (NOT Macbook Pro) Sound Issues**]("http://ubuntuforums.org/showthread.php?t=518391")_
[LIST]
[*]There is a problem with Gutsy on Mac Pros that causes the sound to be very low. Here is the fix.
[/LIST]
_[**iMac 20" / 24" Aluminum: Sound Patch**]("http://ubuntuforums.org/showpost.php?p=3697702&postcount=5")_
[LIST]
[*]There is a problem with ALSA on the aluminum iMac. nicfagn has created a patch.
[/LIST]
_[**Strange Power-related Issues?**]("http://ubuntuforums.org/showthread.php?t=502674")_
[LIST]
[*]On Mac laptops, sometimes you can see some strange reporting for the battery / power system. Resetting the SMC can fix this.
[/LIST]
[_**Installing Ubuntu on a Mac Pro**_]("http://ubuntuforums.org/showthread.php?t=842100")
[LIST]
[*]If you try to install Ubuntu on a Mac Pro (on a second hard drive), you will likely run into booting problems. There is some manual work you have to do to get it working. [http://ubuntuforums.org/showthread.php?t=553587](http://ubuntuforums.org/showthread.php?t=553587)
[*]More in-depth info is here: [http://ubuntuforums.org/showthread.php?t=842100](http://ubuntuforums.org/showthread.php?t=842100)
[/LIST]
[**_HOW-TO: Apple Remote Control_**]("http://ubuntuforums.org/showthread.php?t=806703")
[LIST]
[*]For aluminum iMacs, additional info might be helpful if you have problems: [http://ubuntuforums.org/showthread.php?t=607797](http://ubuntuforums.org/showthread.php?t=607797)
[/LIST]
_[**HOW-TO: get the MBP keyboard backlight working properly**]("http://ubuntuforums.org/showthread.php?p=4437462")_
[LIST]
[*]An excellent How-To for Configuring the keyboard backlight with pommed.
[/LIST]
_[**HOW-TO: Dual-boot MBP with Ubuntu encrypted  **]("http://ubuntuforums.org/showthread.php?p=4604645")_
[LIST]
[*]If you want to install Ubuntu on an encrypted partition this is a good guide.
[/LIST]
_[**Macbook Keyboard configuration information  **]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Apple_Keyboard")_
[LIST]
[*]This page in the Gentoo wiki gets in depth about Apple keyboard default behavior and methods of customization.
[/LIST]
[URL="http://ubuntuforums.org/showpost.php?p=5166788&postcount=21"][U][B]Single Boot Ubuntu Without Long Delay
[/B][/U][/URL]
[LIST]
[*]If you completely wipe out OS X and install Ubuntu only, you will get long delays at bootup. This shows you how to use the bless command on your OS X disc to fix the problem.
[/LIST]
[_**Assign a Keyboard key as right-click**_]("http://ubuntuforums.org/showpost.php?p=5801976&postcount=3")
[LIST]
[*]Because there is only one button on Mac touchpads, you might want to assign a keyboard key as right-click.
[*]This information will also help you assign keys to perform other functions as well.
[/LIST]
[URL="http://ubuntuforums.org/showthread.php?t=914697"][U][B]Broadcom WiFi cards in Intrepid 8.10
[/B][/U][/URL]
[LIST]
[*]Broadcom has provided a driver for Linux.
[/LIST]

---

### Post by Fink on 2007-12-20
I really think the bluetooth setup is cool, my buddy has it on his Mac and I was very impressed

---

### Post by macuser2000 on 2008-01-14
The 24-inch Aluminum iMac sound issue applies to the 20-inch Aluminum iMac too. The same fix works.

---

### Post by cyberdork33 on 2008-01-14
> **macuser2000 said:**
> The 24-inch Aluminum iMac sound issue applies to the 20-inch Aluminum iMac too. The same fix works.
Added 20" to the description.

For others,Contributions or fixes to the posted information are always welcome. Thanks!

---

### Post by Sita Ram on 2008-02-06
Thanks for the awesome info.
  
Quick question,  Where is all the extensive info on Intel White Imac's (specifically the 1.8 ghz/ 2.0 ghz models)?

Ciao for now.

---

### Post by cyberdork33 on 2008-02-06
> **Sita Ram said:**
> Quick question,  Where is all the extensive info on Intel White Imac's (specifically the 1.8 ghz/ 2.0 ghz models)?There really isn't any because there isn't any special configuration required. 

Go to:
[http://wiki.ubuntu.com](http://wiki.ubuntu.com) 
and search "imac" in the top right corner.

---

### Post by mabovo on 2008-02-09
Is there a HowTo for MacBook keyboard configuration in other languages different from GB or US ?

---

### Post by Bose on 2008-02-28
Wow...when deciding to try Ubuntu for the first time I had NO idea how little I really knew about computers.  I used Windows for about 10 years and just recently bought a Macbook.  I'm smarter than the average cookie when it comes to computers, but reading some of these guides have left me absolutely dumbfounded. 

Can someone explain the following things to me?

Daily Snapshot

Subversion

Can Ubuntu be installed on a Macbook (Core2duo) via USB flash drive?

Thanks for the help guys :)

---

### Post by cyberdork33 on 2008-02-28
A "Daily Snapshot" refers to software development. It is a snapshot of the code for that particular day. These are usually generated by some source management software such as....

subversion [svn] (This is a popular one for open source projects). There are several others though such as git, bzr, darcs, and cvs.

I would answer your last question with a yes except it depends on what you mean... So far nobody has been able to get Mactels to boot from usb drives (other than external CD drives) in a consistent way.

---

### Post by Bose on 2008-02-29
Thanks for the info!

---

### Post by aongenae on 2008-03-31
> **mabovo said:**
> Is there a HowTo for MacBook keyboard configuration in other languages different from GB or US ?

I have a belgian/french (it's exactly the same on apple computer) keyboard and I configure it this way:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=914540#p914540](http://forum.ubuntu-fr.org/viewtopic.php?pid=914540#p914540)

it works from feisty up to hardy beta

---

### Post by Aurora on 2008-04-13
I think this line in the Ubuntu MacBook WIKI needs to be updated:

"If necessary, use Boot Camp to resize your OSX partition and make space for Ubuntu. Don't waste a CD creating a Windows driver disk. Reboot."

AFAIK, users who still run Tiger and have not already installed Boot Camp, will not be able to install it, because the license has expired, and OSX won't load it.  We will need to know how to resize the OSX partition without using Boot Camp.   I think GParted can do this, but I'm not sure.

Paul in Seattle

---

### Post by Gen2ly on 2008-04-13
Hmm, does seem to be a valid point, I forgot the license expired already.  :)  

Yes gparted can resize unjournaled partition but in reduction only.  If there isn't a note already, I think it's a good idea.

---

### Post by cyberdork33 on 2008-04-13
you can still use the commandline in OSX Tiger. "diskutil resizeVolume".

gparted is also an option as stated.

---

### Post by daya on 2008-04-26
Which Ubuntu ISO to install on MacBook Pro Intel 2.4 GHz 4GB RAM (hopefully this is Santa Rosa), I am not sure if the download option provided at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) for 64 Bit AMD and Intel is the right one?

---

### Post by McLeod Brennaman on 2008-04-26
Doesn't matter, the Core 2 Duo can run as either x86 or x86_64 (amd64), so just pick whichever suits your fancy. There is plenty of hot debate on which is the "better" structure, but generally speaking, x86 (32-bit) is more common, x86_64 (amd64)(64-bit) can be "faster." I strongly suggest doing a bit of research to see which structure more fits your computing usage.

But anyways, just out of curiosity, 4GB? I thought the max our chipset supported was 3GB? I recently threw in a 2GB stick next to my original 1GB and thought that was as far as I could max it (never use it all anyways, gotta love linux). And AFAIK the Santa Rosa is the latest (last 1-2 years, not sure about that, been at least since last August since that's when I got mine) generation of MBP.

Also, on the Boot Camp issue. All one has to do to get it to work (assuming you still have the Boot Camp Beta .dmg somewhere, if not, I'm sure there's all sorts of shady torrents for it) is set the system clock back to September 2007.

---

### Post by rupali_4 on 2008-05-02
You can do everything you want to do in a day on [www.baajaa.com](www.baajaa.com). You can look at job openings, find a date, rent an apartment, sell your bike and buy used items. And if you are interested in showbiz you can post your profile along with pics and your video as well. Also Balaji Telefilms is conducting auditions on [www.baajaa.com](www.baajaa.com) . All this and lots more on [www.baajaa.com](www.baajaa.com) !

One of the new features added on [www.baajaa.com](www.baajaa.com) is Yellow Pages. You can create a simple listing of your business for free. But what is really interesting is that you can Create Your Own Website (with your Logo, 5 pics, Company Profile, List of Products & Services, Video) and you get a Free Premium Yellow Page listing. For just Rs.3999/- !
 
Thanks

---

### Post by choicearizona on 2008-05-25
I bought my Apple for business purposes but some companies I do business with do not support it.  Can I convert part of my hard drive to windows as someone I know has suggested?

---

### Post by mediamind on 2008-05-25
I've installed Hardy on my first generation Macbook Pro and would like to be able to use an external monitor and connect to LCD projectors. I followed the instructions on the [Macbook Pro Community Documentation page]("https://help.ubuntu.com/community/MacBookPro") and have successfully (see below) installed the most recent fglrx driver (ATI Proprietary). 

My problem is that the ATI Catalyst Control Center (Applications-->Accessories) fails to launch when I click on it. I've tried reinstalling it and also running it via Alt+F2 with no success.

When I verify the driver using "fglrxinfo" I get this:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7415 Release 

And when I use this "glxinfo | grep direct" I get:
direct rendering: Yes 

Any help would be very much appreciated!

---

### Post by yinetglez on 2008-05-30
I have a macbook pro, I need know how I instaler ubuntu in my laptop??, please

---

### Post by cyberdork33 on 2008-05-30
> **yinetglez said:**
> I have a macbook pro, I need know how I instaler ubuntu in my laptop??, please
It depends on what version Macbook Pro you have, but here are the guides:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://help.ubuntu.com/community/MacBookPro/SantaRosa](https://help.ubuntu.com/community/MacBookPro/SantaRosa)
[https://help.ubuntu.com/community/MacBookPro/Penryn](https://help.ubuntu.com/community/MacBookPro/Penryn)

---

### Post by veiho on 2008-06-11
I have found out something that i think, might be useful for others as well as it's not well known.

[SIZE="4"]How to single boot Linux without delay on Macbook.[/SIZE] (tested with Macbook 2.1)

So, I like Macbook, but OSX not at all.

1. If you have OSX installed, boot to it and mute sound. This assures that you won't be annoyed by the startup/poweron sound afterwards. I even used [This software]("http://www5e.biglobe.ne.jp/~arcana/software.en.html") to be absolutely sure.
Restart to confirm that no startup sound is audible.

2. Prepare rEFIt boot disk (CD-RW).

3. Boot Ubuntu install and remove **all partitions**, partition as you like for your Linux installation. Install Ubuntu, restart.

4. Put in rEFIt CD and holding down alt key, boot rEFIT cd. Synchronize GUID and MBR. Restart.

5. Insert OSX disc, boot from it, open terminal and enter following:
> bless --device /dev/disk0s2 --setBoot --legacy --verbose
where /dev/disk0s2 is the partition you installed grub (do 'diskutil list' to find out correct partition). Of course, '--verbose' is optional. This makes Macbook EFI firmware boot your Linux installation in legacy mode without long delay (20s vs 3s).

6. Restart your Macbook (don't forget to remove OSX disc). And boot directly to Linux!

---

### Post by cyberdork33 on 2008-06-11
excellent. I was not aware that you could bless a device... This ought to help the single-boot Ubuntu on Mac users out there a lot.

---

### Post by gmc on 2008-06-16
> **veiho said:**
> I have found out something that i think, might be useful for others as well as it's not well known. 

Awesome! I can confirm this works on the mini too. No more gong every time I turn on my home media system.

Thank You

---

### Post by The Coy on 2008-07-10
Hi, new to the site and Ubuntu. I've been searching for a bit now and couldn't find any answers, maybe I'm just blind. Are the wiki for the MacBook and MacBook Pros the same as for an iMac? I have an iMac (8,1) and am trying to dual-boot Leopard and Ubuntu (because Windows is the pitchfork to Microsoft's Satan). Thanks.

---

### Post by cyberdork33 on 2008-07-10
> **The Coy said:**
> Hi, new to the site and Ubuntu. I've been searching for a bit now and couldn't find any answers, maybe I'm just blind. Are the wiki for the MacBook and MacBook Pros the same as for an iMac? I have an iMac (8,1) and am trying to dual-boot Leopard and Ubuntu (because Windows is the pitchfork to Microsoft's Satan). Thanks.
you can follow the installation instructions for any mac, they are all basically the same. The fixes for hardware after the installation will be different. There is an imac specific page here:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

I don't believe there is an iMac8,1 yet. I would check that. you can do this command in the terminal on the Ubuntu LiveCD, or you can check the version in System Profiler on OSX.```
sudo dmidecode| grep Product
```

---

### Post by abuakel on 2008-07-11
Does the MacBook Ubuntu Wiki show how to dualboot with a macbook and Ubuntu?

---

### Post by cyberdork33 on 2008-07-11
> **abuakel said:**
> Does the MacBook Ubuntu Wiki show how to dualboot with a macbook and Ubuntu?
yes, it appears to.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by cenannel on 2008-07-15
I am happy with these....

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)
:popcorn:

---

### Post by ronystephen on 2008-07-26
I've been searching for a bit now and couldn't find any answers, Are the Google for the Mac Book Pros the same as for an iMac? I have an iMac (8, 1) and I am trying to dual-boot Leopard and Ubuntu.

===============================================================
Rony stephen.
  [Addiction Recovery West Virginia ]("http://www.addictionrecovery.net/west-virginia ")

---

### Post by megaloch on 2008-07-29
And so ... ? Just joined ubuntu. 

Have a Core 2 Duo OSX ~ specifically what do I download. 

Someone told me to use Safari on Ubuntu (as opposed to Firefox) ... ? 
Using bootcamp, I get Vista: but noticed Firefox 3.1 cut off my Internet. What is more bizarre ~ I started getting Greek font on it.

---

### Post by ynot988 on 2008-08-02
I cannot get the fix to work on my 20 inch. Can you give me some more detailed instructions? I am kind of new to all this, and I have to start somewhere.

---

### Post by cyberdork33 on 2008-08-03
> **ynot988 said:**
> I cannot get the fix to work on my 20 inch. Can you give me some more detailed instructions? I am kind of new to all this, and I have to start somewhere.
What "fix"?

You should start a thread in the forum and fully describe the issue.

---

### Post by sy1 on 2008-08-04
[QUOTE=veiho;5166788]I have found out something that i think, might be useful for others as well as it's not well known.

[SIZE="4"]How to single boot Linux without delay on Macbook.[/SIZE] (tested with Macbook 2.1)

So, I like Macbook, but OSX not at all.


Hi Veiho,

Fantastic thread, is there another way to get the rEFIt CD? I have Mint (Elyssa) installed on my macbook (intel)?

---

### Post by sy1 on 2008-08-05
[QUOTE=veiho;5166788]I have found out something that i think, might be useful for others as well as it's not well known.






Never mind that last question Vieho, I followed your advise using my factory OSX disk, went to terminal and used bless to set legacy boot - 


THANKS!

---

### Post by sy1 on 2008-08-05
I agree with dork, this was extremely helpful!

Thanks!

---

### Post by goodluckguys on 2008-08-15
MOVING? ivansmoving.narod.ru LOW PRICES!!!

---

### Post by Adoring on 2008-08-23
Thank you

[COLOR="White"]http://www.al-mohd.com/[/COLOR]
[COLOR="White"]http://www.al-mohd.com/forum/[/COLOR]

---

### Post by johnmarker on 2008-08-25
hiiiiiiiii

john......

 what  is all about  ...

:guitar:

  	[  TennesseeDrugAddiction]("http://www.drugaddiction.net/tennessee")

---

### Post by sygrup on 2008-09-04
The 24-inch Aluminum iMac sound issue applies to the 20-inch Aluminum iMac too. The same fix works.

---

### Post by franki.macha on 2008-09-14
> **veiho said:**
> I have found out something that i think, might be useful for others as well as it's not well known.

[SIZE="4"]How to single boot Linux without delay on Macbook.[/SIZE] (tested with Macbook 2.1)

So, I like Macbook, but OSX not at all.

1. If you have OSX installed, boot to it and mute sound. This assures that you won't be annoyed by the startup/poweron sound afterwards. I even used [This software]("http://www5e.biglobe.ne.jp/~arcana/software.en.html") to be absolutely sure.
Restart to confirm that no startup sound is audible.

2. Prepare rEFIt boot disk (CD-RW).

3. Boot Ubuntu install and remove **all partitions**, partition as you like for your Linux installation. Install Ubuntu, restart.

4. Put in rEFIt CD and holding down alt key, boot rEFIT cd. Synchronize GUID and MBR. Restart.

5. Insert OSX disc, boot from it, open terminal and enter following:

where /dev/disk0s2 is the partition you installed grub (do 'diskutil list' to find out correct partition). Of course, '--verbose' is optional. This makes Macbook EFI firmware boot your Linux installation in legacy mode without long delay (20s vs 3s).

6. Restart your Macbook (don't forget to remove OSX disc). And boot directly to Linux!


is there any way of doing this now that i've already installed ubuntu? :s

i presume i can write a rEFIt disc and an OSX disc (as i've lost mine..) and follow steps 4 through 6?

will this work, and is there any other way of removing that damn annoying sound :P

thanks to anyone who can help me out of my ignorance, and thanks to veiho for this brilliant pearl of wisdom ;)

---

### Post by sallyreena on 2008-09-15
The MacBook Air has a full-size screen and a full-size keyboard. So ignore the fact that it is an ultraportable, most of the time when you're actually using it you'll forget how thin it is and simply focus on whatever you need it to do.
-------------
Sally
[Social media marketing]("http://www.drivenwide.com")

---

### Post by genius_1a2b on 2008-09-24
paypal wholesale ARMANI (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Bape (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale boot (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Burberry max (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Chanel (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Christan Audiger shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale Timberland (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale UGG (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Versace shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale women jordans (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale WOWEN (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dsquared (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dunk(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale ED hardy shoes(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Evisu(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale GOODYEAR(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))    paypal wholesale dsq shoes(paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dsquared (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dunk (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale ED hardy shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale COURT FORCE (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale converse (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale D&G shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dior shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale D&G shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale dsq shoes (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))     paypal wholesale Dsquared (paypal payment)([http://www.atitrade.com](http://www.atitrade.com))

---

### Post by ! SaY MaN ! on 2008-10-04
ubuntu is great ! :guitar:


[forums]("http://www.3rbloadiz.com/vb") - [games]("http://www.3rbloadiz.com/games") - [video]("http://www.3rbloadiz.com/video") - [upload]("http://www.3rbloadiz.com/up") - [songs]("http://www.3rbloadiz.com/") - [directory]("http://www.3rbloadiz.com/dlil") - [islam]("http://www.3rbloadiz.com/islam") - [movies]("http://www.3rbloadiz.com/movies") - [chat]("http://www.3rbloadiz.com/vb")

---

### Post by powerqun on 2008-10-22
An old lady's husband had just died and she felt their was no reason to live anymore. She called the doctor and asked exactly where her heart was. He told her it should be under her left breast. That night she went to the emergency room with a shot in the knee.     ....................................................................................................................................................buy [world of warcraft gold](http://www.mmoinn.com/)| cheap [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)| site: [http://www.mmoinn.com](http://www.mmoinn.com)|cheapest [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)|buy [wow gold](http://www.mmoinn.com)

---

### Post by Stasven on 2008-11-27
Machine: iMac7,1
Operating System: OS X Leopard

Hi there, I'm wanting to install Ubuntu 8.10 (I made a CD) onto a partitioned part of my Macintosh HDD but I'm not sure how I should format it. I used to have XP running off of an NTFS partition but I removed it so I could install Ubuntu. I've read online to just boot up from the Ubuntu CD and follow instructions for partition but I'd like some more opinions if possible.

My impatience has had the better of me once again. I set up a "Windows" partition via BootCamp (60GB, FAT32 I presume) and then booted up from Ubuntu disk (strangely labelled as "Windows"). It all seemed to be working well, and I reset the computer. I then held down the Option key to switch to the Ubuntu HDD partition and the only recognised drive was the Macintosh. 

I checked Disk Utility and there are two new drives, that are grey-ed out: "Linux Swap" and "disk0s4" as partitions of my internal drive. 

I don't know what to do now. Disk Utility says that out of my "298.1 GB WDC WD3200AAJS-40RYA0 Media" internal HDD are my drives: Macintosh (236.9 GB); Ubuntu [BootCamp Partition] (124.5 MB); DISK0S4 (58.3 GB); and Linux Swap (2.5 GB).

How can I just make it work as two simple partitions; one for Macintosh, one for Ubuntu? :( :confused:

---

### Post by Leslie Viljoen on 2008-11-28
> **Stasven said:**
> Hi there, I'm wanting to install Ubuntu 8.10 (I made a CD) onto a 

Please repost this as a new topic in the main forum, you won't get replies in this thread.

---

### Post by waterj2 on 2008-11-29
> **sygrup said:**
> The 24-inch Aluminum iMac sound issue applies to the 20-inch Aluminum iMac too. The same fix works.How about the Mac Mini? I seem to have the same problem (sound is *way* too quiet), any idea if the fix is the same?

---

### Post by Chrisj303 on 2008-12-15
I have recently gone back to triple-booting OS X/Windows/Ubuntu on my MBP 4,1.

Now WiFi is sorted OOTB, I figured it would be less painful, less dicking about than it used to be. 

However, trying to find the relevant information through these forums and the Wiki(s) was a nightmare. I honestly think it could do with an overhaul.

Its VERY hard to find specific information on these boards, no matter how clever you are with the search engine, you WILL end up with pages and pages of threads to trawal through. 

Its taken me two days of digging about, to get *everything* working - and I mean 2 FULL days!

---

### Post by cyberdork33 on 2008-12-15
> **Chrisj303 said:**
> I have recently gone back to triple-booting OS X/Windows/Ubuntu on my MBP 4,1.

Now WiFi is sorted OOTB, I figured it would be less painful, less dicking about than it used to be. 

However, trying to find the relevant information through these forums and the Wiki(s) was a nightmare. I honestly think it could do with an overhaul.

Its VERY hard to find specific information on these boards, no matter how clever you are with the search engine, you WILL end up with pages and pages of threads to trawal through. 

Its taken me two days of digging about, to get *everything* working - and I mean 2 FULL days!
One of the reasons it is so messy right now is that things ARE in an overhaul. See the "Before You Post" link in my signature to get to the right documentation for a specific mac version. You can find out more about what we are doing through the following thread:
[http://ubuntuforums.org/showthread.php?t=969360](http://ubuntuforums.org/showthread.php?t=969360)
And there is a lot of planning and organizational info here:
[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)

---

### Post by hudai on 2008-12-30
:popcorn:

---

### Post by emmary on 2009-01-07
Apple Laptop Charger
[Model #: CGR-091-LTP] 
 
 
  
Click the picture to enlarge  
 
 Model #  CGR-091-LTP 
M.O.Q.  None 
 
 
Quantity  Unit Price  
Sample 1 US$10.14 
10-29 US$9.19 
30-49 Login 
50-99 Login 
100-199 Login 
200+ Login 
 
 
Available Options: 
Color: Black 
 

Login or register
to create an order. 
Request for price quote
for large quantity order  
 



--------------------------------------------------------------------------------


You have a nice Apple laptop? Then this is a perfect laptop charger for Apple series. Have your power and enjoy the ultra entertainment.Have it now and you won't miss it. 



Features 


Apple iBook 12", 14" Apple iBook G4 12", 14" Apple PowerBook G4 12"
15", 17", Titanium Apple iBook 1999, 2000, Blueberry, Graphite, Indigo, Lime Green, Tangerine Apple PowerBook 1400C/CS Apple
PowerBook 2400, 3400/C Apple PowerBook
G3 bronze keyboard, firewire, 1997, 1998, 1999, Lombard, Pismo Apple
PowerBook G3 Wall Street 



Package Content 


1*Charger 



Specification 


Output Voltage 24V 
Output Current 2A 
Apower(W) 50 
Output connector size 7.7*2.5 
AC pin 2 PIN 
Laptop AC Adapter for GATEWAY 400SD4, 400VTX Input 100-240V 
Input Frequency 50 ~ 60Hz 
Operating Environment In Use : 0°C ~ +40°C, Storage : -40° C ~ +85° C 
Relative Humidity 5% ~ 95%RH (non-condensing) 
Color Black 
Size (LxWxH) 10.8cm x 4.6cm x 3.0cm 
Package Gross Weight 0.000kg 
Package Size (LxWxH) 15cm x 13cm x 5.0cm 
Package Type Gift Box

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by jrdemasi on 2009-02-07
> **veiho said:**
> I have found out something that i think, might be useful for others as well as it's not well known.

[SIZE="4"]How to single boot Linux without delay on Macbook.[/SIZE] (tested with Macbook 2.1)

So, I like Macbook, but OSX not at all.

1. If you have OSX installed, boot to it and mute sound. This assures that you won't be annoyed by the startup/poweron sound afterwards. I even used [This software]("http://www5e.biglobe.ne.jp/~arcana/software.en.html") to be absolutely sure.
Restart to confirm that no startup sound is audible.

2. Prepare rEFIt boot disk (CD-RW).

3. Boot Ubuntu install and remove **all partitions**, partition as you like for your Linux installation. Install Ubuntu, restart.

4. Put in rEFIt CD and holding down alt key, boot rEFIT cd. Synchronize GUID and MBR. Restart.

5. Insert OSX disc, boot from it, open terminal and enter following:

where /dev/disk0s2 is the partition you installed grub (do 'diskutil list' to find out correct partition). Of course, '--verbose' is optional. This makes Macbook EFI firmware boot your Linux installation in legacy mode without long delay (20s vs 3s).

6. Restart your Macbook (don't forget to remove OSX disc). And boot directly to Linux!

Does this work with any Linux OS? I don't recall you stating that you actually installed rEFIt anywhere.  I'm trying to single boot a linux OS, but not Ubuntu due to the hard drive killing properties of Intrepid.

---

### Post by cyberdork33 on 2009-02-07
> **jrdemasi said:**
> Does this work with any Linux OS? I don't recall you stating that you actually installed rEFIt anywhere.  I'm trying to single boot a linux OS, but not Ubuntu due to the hard drive killing properties of Intrepid.
It will not kill your hard drive, but anyway...
Yes, it will work with any OS.

---

### Post by wiltors on 2009-02-12
> **veiho said:**
> 
6. Restart your Macbook (don't forget to remove OSX disc). And boot directly to Linux!

I LOVE YOU
that might sound a little creepy but it's only cuz i've been trying to figure out how to do that for DAYS. thank you :lolflag:

---

### Post by fbugnon on 2009-02-16
> **veiho said:**
> 
5. Insert OSX disc, boot from it, open terminal and enter following:

where /dev/disk0s2 is the partition you installed grub (do 'diskutil list' to find out correct partition). Of course, '--verbose' is optional. This makes Macbook EFI firmware boot your Linux installation in legacy mode without long delay (20s vs 3s).


I'm using a triple boot without rEfit on a first generation MacBook Pro (only bootcamp) and I use the option-alt key to choose what partition to boot from: either "HD" to boot from Mac OS or "Windows" to get into the GRUB and then choose Ubuntu or Windows 7 beta.

I've also notice a certain delay from pressing the power button until it gets into the HD X*Windows option (or automatically to GRUB if I don't press anything).  

So I would like to know if it is possible to use this "blessing" option to shorten this delay even in my triple-boot system?  Or is it meant to works only on a single-boot system?

Thank you.

---

### Post by Litropy on 2009-08-10
Does the 24'/20' patch entry of the faq still apply or does it need to be updated?

---

### Post by Jayomat on 2010-08-03
> **veiho said:**
> I have found out something that i think, might be useful for others as well as it's not well known.

[SIZE=4]How to single boot Linux without delay on Macbook.[/SIZE] (tested with Macbook 2.1)

So, I like Macbook, but OSX not at all.

1. If you have OSX installed, boot to it and mute sound. This assures that you won't be annoyed by the startup/poweron sound afterwards. I even used [This software]("http://www5e.biglobe.ne.jp/%7Earcana/software.en.html") to be absolutely sure.
Restart to confirm that no startup sound is audible.

2. Prepare rEFIt boot disk (CD-RW).

3. Boot Ubuntu install and remove **all partitions**, partition as you like for your Linux installation. Install Ubuntu, restart.

4. Put in rEFIt CD and holding down alt key, boot rEFIT cd. Synchronize GUID and MBR. Restart.

5. Insert OSX disc, boot from it, open terminal and enter following:

where /dev/disk0s2 is the partition you installed grub (do 'diskutil list' to find out correct partition). Of course, '--verbose' is optional. This makes Macbook EFI firmware boot your Linux installation in legacy mode without long delay (20s vs 3s).

6. Restart your Macbook (don't forget to remove OSX disc). And boot directly to Linux!

Hi there! I have already installed Ubuntu 9.10 but unfortunately also already deleted my OSX partition. Anyway is there  a way to accomplish the sped up start without booting into OSX? 

Any answer is appreciated:)

---

### Post by PicklePumpers on 2010-09-11
> **Jayomat said:**
> Hi there! I have already installed Ubuntu 9.10 but unfortunately also already deleted my OSX partition. Anyway is there  a way to accomplish the sped up start without booting into OSX? 

Any answer is appreciated:)

Boot from your OS X install DVD.

---

### Post by PicklePumpers on 2010-09-11
> **veiho said:**
> 
4. Put in rEFIt CD and holding down alt key, boot rEFIT cd. Synchronize GUID and MBR. Restart.

There is no "Synchronize GUID and MBR" option. If you meant to do something else that results in this please be more specific. This may be an option that is no longer there but it's unclear. 

> **veiho said:**
> 
5. Insert OSX disc, boot from it, open terminal and enter following:

where /dev/disk0s2 is the partition you installed grub (do 'diskutil list' to find out correct partition). Of course, '--verbose' is optional. This makes Macbook EFI firmware boot your Linux installation in legacy mode without long delay (20s vs 3s).


It's unclear which partition GRUB is installed on. I have a 1MB partition with what looks like a GUID, a 244MB partition that is labeled "Microsoft Basic Data ", and my Linux LVM partition.

Using grub-update-from-legacy I saw that it was the 244MB partition, which is what I assumed, but setting that using your info didn't make a bit of difference. There is still a 30 to 40 second delay while the EFI looks for an EFI drive. Only then does it boot Linux.

I'm going to try the GRUB-EFI thingy now to see if that helps.

---

