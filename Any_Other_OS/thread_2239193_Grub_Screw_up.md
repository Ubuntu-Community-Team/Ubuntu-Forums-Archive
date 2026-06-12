---
title: "Grub Screw up"
date: 2014-08-12
forum: Any Other OS
---

### Post by Voidn_Warranties on 2014-08-12
Hi and thanks in advance for helping. 

I am working on a friends Win7 box.  They tried installing mint with grub and all worked fine.  They then deleted the kernal and all folders from there to try another OS...

I know I know.  Anyway - Grub is really jazzed up.  Using a mint stick I reinstalled grub but that didn't seem to do what I wanted.  Not being a grub expert I went to Boot-repair on a stick and ran an autofix. 
[http://paste.debian.net/115166](http://paste.debian.net/115166)

Now we get to a windows prompt to repair or start normally.  Tried repair.  It says it failed.  Tried start normally - just sits there with animated win 7 boot logo - but no hard drive activity.

Tried again - clicked advance and told it to boot the second partition...  but that doesn't work 
[http://paste.ubuntu.com/8027369/](http://paste.ubuntu.com/8027369/)

Tried again - clicked auto fix and right back to windows prompt to repair or start normally. 
[http://paste.ubuntu.com/8027438/](http://paste.ubuntu.com/8027438/)

I don't want to punt and reinstall windows but this is a bit beyond me. 

My other thoughts:  reinstall mint and get it to auto rebuild grub?

Any help would really be appreciated!

Thanks,

---

### Post by oldfred on 2014-08-12
Moved to Other OS since Windows or Mint?

You show a Windows boot loader and the normal Windows boot files.
If you can get to repair console and run autofix in Windows, you often have to run it three times to fix issues. 
Or you many need to go to command line and manually run chkdsk until no errors or other fixes.

Boot-Repair cannot do many fixes for Windows, so you need a Windows repair console or if you cannot get to repair console you really need a Windows repairCD or Flash drive.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

 [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

 [http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Voidn_Warranties on 2014-08-13
OldFred,

Thanks for the reply.  Apparently many things were attempted.  

I copied his personal files to a CD and punted.

But the repair via Win install did start but eventually told me that it was unable to solve the problem. 
Whatever was done also made a dir called "Old booot"  Yes = three o's.  Not sure what that was all about. 

Anyway - thanks again for your help.

---

