---
title: "Uninstalling linux and installing windows 7"
date: 2013-09-08
forum: Any Other OS
---

### Post by toby_peterken on 2013-09-08
I have ubuntu 13.04 and I want to be able to use autodesk products.I have a usb with a windows 7 .iso.  

How do I install windows 7 over the top of ubuntu,  i don't want linux anymore.

---

### Post by davetv on 2013-09-08
You will need to burn the iso as a bootable dvd, then boot from the dvd.

---

### Post by buzzingrobot on 2013-09-08
If memory serves, the Windows installer will simply overwrite whatever it finds on the drive.

If it balks, use the installer to remove and format the Ubuntu partitions, and then proceed.

---

### Post by toby_peterken on 2013-09-09
It keeps saying it needs to find advice drivers.  Hwere qare they and how do I install them.

---

### Post by carl4926 on 2013-09-09
> **toby_peterken said:**
> It keeps saying it needs to find advice drivers.  Hwere qare they and how do I install them.
Do you mean before install or are you talking post install?

---

### Post by toby_peterken on 2013-09-09
Neither.  it is during install after you choose the language settings.  I have also tried vista and that doesn't work either.  I currently only have access to the usb .iso.

---

### Post by carl4926 on 2013-09-09
Is this a genuine copy of windows? Have you used it before?
Select the drive and format it before starting the install might help/

---

### Post by buzzingrobot on 2013-09-09
What kind of hardware is this?

Device drivers can be located and installed via Device Manager.  They may also be installed in a Windows Update.  They are typically also available directly from the vendors.

On some machines, especially laptops that depend on wifi because no wired ethernet is available, at a minimum the drivers for the wifi card will need to be obtained and placed on a USB stick.  Then, when the initial Windows install completes, those drivers can be installed from the USB stick, wifi enabled, and the other missing drivers can then be located, downloaded, and installed.

If you cannot get Windows to install at all because it complains about missing device drivers, you will need to identify and obtain those drivers and make them available during the install.

---

### Post by toby_peterken on 2013-09-09
How to i find out what driverxs they are and how do i make them avalible.
@ carl - o have tried many digffernt .isos and none have worked

---

### Post by buzzingrobot on 2013-09-09
You need to know what devices are in the machine to know what drivers are needed. This should be available at the machine's manufacturer's site.

However... Windows is rather good at detecting missing device drivers, finding them for you, and installing them.  You will need net access for that.  Hence, the suggestion to download (on a working machine) the drivers for your wifi.  After Windows is installed, plug in the USB stick containing the driver, launch Device Manager from Control Panel, locate the appropriate entry, you'll be prompted for a location for the driver, so let it find the USB stick (Windows will see it as another drive). When the install completes, reboot and sign into your wifi via the icon in the panel.

If you can install using a wired ethernet connection, this entire dance may be eliminated.

Bottom line: Device Manager will go out on the net and find drivers.  Failing that, you can find them at vendor sites. *All* of them may be available at the site of your machine's vendor. But, you must have net access first.

Once I got net access, I'd first run all the Windows Updates because that will likely update many drivers. Keep running them until it says there are no more. Then, check Device Manager for problems.

(Are you sure you are correctly burning bootable iso's, not just copying them as you would music or video files?)

---

### Post by carl4926 on 2013-09-09
No device drivers are required to install windows. Least I never yet had such requirement made.

Windows has a utility to make bootable USB's for it's system installations. I suggest you use it. And please be sure you have a genuine microsoft download.

---

### Post by coffeecat on 2013-09-09
> **toby_peterken said:**
> 
@ carl - o have tried many digffernt .isos and none have worked

What is the source of all these different Windows ISOs?

---

### Post by toby_peterken on 2013-09-09
I am using winusb on ubuntu to burn the iso, I am no dual booting.
where is the genuine microsoft download and can it be activated after install.

---

### Post by carl4926 on 2013-09-09
[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/where-can-i-download-windows-7-iso-i-have-a/7d964b05-2be9-4800-bc7f-3ca30356fc3d](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/where-can-i-download-windows-7-iso-i-have-a/7d964b05-2be9-4800-bc7f-3ca30356fc3d)

---

### Post by toby_peterken on 2013-09-10
i have used that one.  I have downloaded it but i think the error will persist

---

### Post by carl4926 on 2013-09-10
Are you using
[http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool)

Have you verified the download of the .iso?

---

### Post by buzzingrobot on 2013-09-10
You still haven't said what hardware you are trying to install on or how you are trying to install.

The normal way to boot into an install image is to interrupt the boot process, enter BIOS setup, alter the boot order to opt for the device holding the image, and continue the boot.

Is that what you are doing?

You said you were prompted to install drivers after language selection. What, exactly, does the message say? Does it list specific devices that need drivers?  Has this been the single consistent issue with every iso you have tried?

---

### Post by toby_peterken on 2013-09-10
@ carl - how do i verify the downlaod
@ buzzing I am doing that to load the install and all it says is that device drivers are missing.  insert the drivers or search

I am not using windows.  i only have linux right now

---

### Post by buzzingrobot on 2013-09-10
> **toby_peterken said:**
> ....all it says is that device drivers are missing.  insert the drivers or search

I am not using windows.  i only have linux right now

If that message is coming from the Windows installer, I have to say I have never seen it. In any case, you can't provide drivers unless the message tells you specifically what drivers are needed.  There are thousands and thousands of Windows drivers.

As was mentioned earlier in this thread, Windows installs without prompting for drivers. At least, that's been my experience over the years. After the initial install, you will need net access to grab the updates, and that may, or may not, require the installation of a driver for your network card. Windows handles all that very well.

But, *again*, without knowing what hardware you are installing on, this is all very hit or miss. If you are using a legitimate Windows install image, burned and booted correctly, and if that message is a legitimate message generated by the Windows installer, then I can only conclude that you are installing on rare and unusual hardware and that has triggered this rare and very unusual message.

---

### Post by toby_peterken on 2013-09-10
I am using a 
intel i5 3.4 ghz 
asus p8zz- v lx motherboard
nvidea gt610
8gb ram 
ubuntu 13.04 64 bit

the iso is theone carl suggested and i am burning it with win usb.

---

### Post by toby_peterken on 2013-09-10
what if i used xp and then used an update version of 7

---

### Post by carl4926 on 2013-09-10
> **toby_peterken said:**
> what if i used xp and then used an update version of 7
I don't think it will work as you expect. It's basically a clean install
[http://windows.microsoft.com/en-us/windows7/help/upgrading-from-windows-xp-to-windows-7#T1=tab01](http://windows.microsoft.com/en-us/windows7/help/upgrading-from-windows-xp-to-windows-7#T1=tab01)

---

### Post by buzzingrobot on 2013-09-10
Googling around, I found a 2011 report of an installer bug that produced this message. Here's the alleged workaround:

When asked for the drivers, click Cancel. This is supposed to return you to the Welcome Screen.

At the Welcome Screen, remove the USB stick and insert it in *another* port.

Click Install Now and cross your fingers.

Dunno if this works, but you have nothing to lose.

---

### Post by RichardET on 2013-09-10
why not buy restore disk from your OEM?  Why all this angst over nothing???

---

### Post by toby_peterken on 2013-09-11
@richard i have a custom pc but my hardrive hasn't changed scince my old xp

---

### Post by erasmusp on 2013-09-11
I must say I am quite amused by this thread. A user posts a request on the Ubuntu Forum of how to install Windows on his PC to replace his Ubuntu. And this thread is already 25 messages long! I know everybody is trying to be very helpful here but surely this has nothing to do with Ubuntu and should rather be addressed somewhere in some Windows forum or perhaps Microsoft site...? There would definitely be more Windows centric help offered on such sites?

Just my 0.02c worth...

---

### Post by carl4926 on 2013-09-11
> **erasmusp said:**
> I must say I am quite amused by this thread. A user posts a request on the Ubuntu Forum of how to install Windows on his PC to replace his Ubuntu. And this thread is already 25 messages long! I know everybody is trying to be very helpful here but surely this has nothing to do with Ubuntu and should rather be addressed somewhere in some Windows forum or perhaps Microsoft site...? There would definitely be more Windows centric help offered on such sites?

Just my 0.02c worth...

Like you say, we are just trying to be helpful.
Better than a kick in the teeth

---

### Post by QIII on 2013-09-11
I must say I am quite *encouraged* by this thread. A user posts a request on  the Ubuntu Forum of how to install Windows on his PC to replace his  Ubuntu. And this thread is already 25 messages long!

It seems a number of the members of our community are more interested in helping a weary traveller to get to his/her destination than deriding them for going there.

---

### Post by erasmusp on 2013-09-11
I know. I tend to draw a lot on my Windows experience to diagnose problems on Linux just because I spent so much time in the Windows world (at work) but surely very few of us are really any Windows experts?

On a Windows site someone might have already recognized his problem and helped him out... ;)

---

### Post by erasmusp on 2013-09-11
> *I must say I am quite encouraged by this thread.*

So am I - a far cry from the stories you tend to hear of how rude Linux users always are to the Noobies...

---

### Post by buzzingrobot on 2013-09-11
I've seen reports of Win 7 asking for a CD/DVD driver because it can't read the iso on the USB.

---

### Post by toby_peterken on 2013-09-11
I have made a discovery.  After trying the same procdess with an xp and a windows 8 iso, it is media drivers i am missing.  Should i:
1 - remove my gpu and run from the mobo 
2-download the gpu drivers from the nvidia website and put them on the stick

---

### Post by buzzingrobot on 2013-09-11
Well, that's a bit confusing.  By "media" I assume you mean the video card?  

Did you get a specific  message?  What did it say? Is the Nvidia enabled in BIOS and did the message specifically mention Nvidia?

I'm asking because I have never heard of Windows demanding installation of a video driver before proceeding with the install.  It will just install in basic VGA mode. 

That said, if you want to try this, there should be no need to remove anything, since "run from the mobo" suggests your board has an integrated Intel video card. Just enter BIOS setup and ensure the Intel is enabled and the Nvidia is disabled (Optimus, too).

---

