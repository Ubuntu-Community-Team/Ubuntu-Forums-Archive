---
title: "Imac using Parrallels version 3"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by blfarrar on 2008-06-08
First post - Hi everybody - I need a bit of help 
I have an IMAC 24" - I use XP via Parallels (reluctantly) to use one application that isn't & wont be in Apple format..I have tried to use Ubuntu downloads both by CD & ISO file & the two error messages I get are

if I use the Ubuntu 8.04 LTS 64 - looking for X86 processor.
if I use the Ubuntu 8.04 LTS 32 - the system wont boot on installation....
I get the Ubuntu start up screen & am asked to select user language...what do I need to do or get - will I get the same if I get an official Ubuntu (non-downloaded) disc.
I have successfully got XP working on Parallels with all its hassles....this is the reason I need to get Ubuntu working
Thanks

---

### Post by cyberdork33 on 2008-06-08
the 64bit error is becuase you need to change the configuration to be a 64bit system. 

I don't understand what the problem is in selecting a language... You just select your language... The downloaded Ubuntu CDs are exactly the same as the ones you get via shipit (although they have printed labels and CD covers).

---

### Post by blfarrar on 2008-06-08
Sorry Cyberdork33 I may have mislead you...I don't have a problem selecting language..this is the point I get to in the installation.
Just where do you adjust the configuration to 64 bit...I cant find any changes in the parallels system.

---

### Post by cyberdork33 on 2008-06-08
> **blfarrar said:**
> Sorry Cyberdork33 I may have mislead you...I don't have a problem selecting language..this is the point I get to in the installation. And the problem is....? Did you select one of the languages?

The 64bit option should be in the area that you configure your CPU, if it is available. This is a question that is specific to the VM though, and not the fact that you are running Ubuntu, or that you are running on a Mac. You might check the parallels forums for an answer.

---

### Post by blfarrar on 2008-06-09
.....the language already was at English......so just pressed return its then I get the failed boot.....on the32 bit version.
I thought my iMac Intel chip was 64bit if there is a Mac/parallels setting I've yet to find it...no switches in Parallels

I've checked the Parallels website & the application help data...it appears that Parallels supports up to version 7.5.....not 8.
I have to mail Parallels & ask when this is available & if they have a solution.

its at this point I may swap my virtual machine software for something else.....Parallels isn't as good as I thought it would be...it isn't very stable with XP (maybe its XP at fault ??) 


Thanks for the help.

---

### Post by mfox on 2008-06-09
The place in Parallels where you configure the processor (32 or 64 bit) is in the new virtual machine setup. This is when you create the new virtual machine in Parallels.  There is a screen for the type of virtual machine (choose Linux) and below it a scroll box for the type of Linux machine.  This screen is before you are asked for the install disk or iso.  If your iMac is Core 2 duo, you can choose either 32 or 64 bit virtual machine, and your Ubuntu install or live CD iso has to match this choice.  But if you have an early version of the Intel iMac it will be Core Duo (not Core 2 Duo), and you can only install a 32 bit.  Note that if you install a 64 bit, the version of Ubuntu iso should be "AMD-64".

Edit: A few mistakes above; tried to do this from memory but checked my Parallels at the office.  Parallels does NOT provide 64-bit machine support (VMware Fusion does).  When you choose Linux on the aforementioned screen, then you should choose Ubuntu Linux.  In either case, if you want to install 8.04, download the iso "ubuntu-8.04-desktop-i386.iso".  But note that Parallels does not officially support version 8.04; in fact they state that they only support up to 7.04.  The issue is Parallels Tools; it installs easily on 7.04, though I was able to find instructions on how to get it to work on 7.10 and I have that working.  With 8.04, there is an unannounced update to Parallels (version 5604), which you can download [here]("http://download.parallels.com/v3/en/...604-Mac-en.dmg"). I have upgraded to 5604 and then downloaded and installed 8.04, including Parallels Tools.  It works except that the right click and scroll on the mouse don't work, though you can simulate a right click by putting the cursor on what you're interested in and pressing the cmd key on the right side of your keyboard.  There is a long thread on Ubuntu 8.04 on Parallels [URL="http://ubuntuforums.org/showthread.php?p=5147962#post5147962"here[/URL].

---

### Post by cyberdork33 on 2008-06-09
> **blfarrar said:**
> its at this point I may swap my virtual machine software for something else.....Parallels isn't as good as I thought it would be...it isn't very stable with XP (maybe its XP at fault ??)

I use VitualBox now. It is free and works very well with Linux / Windows XP.

---

### Post by entangled on 2008-06-09
I would agree with Cyberdork33. Although I paid for Parallels about a year ago I think Virtualbox is the better option now.
It has worked very well for me on Ubuntu 8.04 and on MacOSX 10.4.11. It seems to have all the functions you need, like tools, mouse in and out, shared folder, networking, window resize, etc. It also seems to run quicker thatn Parallels.

---

### Post by mfox on 2008-06-09
Does VirtualBox allow you to move files to/from Mac/virtual machine with drag and drop?  Parallels doesn't do this with Linux machines, but VMware Fusion does.  That's a very helpful feature!

---

### Post by cyberdork33 on 2008-06-09
> **mfox said:**
> Does VirtualBox allow you to move files to/from Mac/virtual machine with drag and drop?  Parallels doesn't do this with Linux machines, but VMware Fusion does.  That's a very helpful feature!
I don't think so. Shared Directories are created via virtual network servers I believe.

---

### Post by HammerheadNC on 2008-06-10
I installed Ubuntu 8.04 32 bit in Parallels 3.0 on my MacBook Air without any problems. I just used the Ubuntu option for operating system - I don't remember it asking me about 32 or 64 bit but since Parallels said it had to use 32 bit XP I assumed it was 32 bit for all

It is running great by the way - I changed the full screen option to change resolution and it looks like regular Ubuntu :)

Have a good one

Hammerhead

---

### Post by mfox on 2008-06-10
Congrats, HammerheadNC!  I assume that you successfully installed the Parallels Tools if you have the full screen option working, unless you just gave it the full screen coordinates for xorg.conf. Parallels Tools gives you shared folders, on the fly resizing of the virtual machine window and the ability to move your cursor in and out of the window without using a key combination.  If you have problems installing it, there is an unofficial Parallels update to version 5604 that you can get on their Linux Guest OS discussion forum.  I used it to install 8.04, and the Tools were easy to install.  The only remaining problem is that the mouse right click and scroll wheels don't work, but that wouldn't affect you.

---

### Post by HammerheadNC on 2008-06-11
> **mfox said:**
> Congrats, HammerheadNC!  I assume that you successfully installed the Parallels Tools if you have the full screen option working, unless you just gave it the full screen coordinates for xorg.conf. Parallels Tools gives you shared folders, on the fly resizing of the virtual machine window and the ability to move your cursor in and out of the window without using a key combination.  If you have problems installing it, there is an unofficial Parallels update to version 5604 that you can get on their Linux Guest OS discussion forum.  I used it to install 8.04, and the Tools were easy to install.  The only remaining problem is that the mouse right click and scroll wheels don't work, but that wouldn't affect you.

Actually I cannot get the Tools install and there is some mouse slowing which I understand is what the Tools help to fix. If anyone knows how to successfully do this let me know! For the full screen I just picked the resize OS X desktop for Full screen in the Parallels VM settings. I will download the 5604 and see what happens. Do I need to uninstall the 5600 build first?

THANKS

Hammerhead

---

