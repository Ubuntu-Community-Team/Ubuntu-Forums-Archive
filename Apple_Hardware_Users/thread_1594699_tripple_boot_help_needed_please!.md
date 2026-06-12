---
title: "tripple boot help needed please!"
date: 2010-10-12
forum: Apple Hardware Users
---

### Post by jjex22 on 2010-10-12
Hi all, I am trying to set up a triple boot of mac osx 10.4, ubuntu and openbsd on a g4 emac (2003 - the 1ghz, usb 1.x version NOT usb 2.0 version.)

Here's where I'm at - all three OS are installed and yaboot is configured to boot into either osx or ubuntu with no difficulties. The problem is getting yaboot to load bsd. like many i followed the yaboot.conf instructions and added 
'bsd=/dev/hda7'
and ybined it. no success. 

Then I found this link here...
[http://ubuntuforums.org/showthread.php?t=198983](http://ubuntuforums.org/showthread.php?t=198983)

Unfortunately I'm completly new to ppc machines and even though I have got this far I'm now a little stuck. does anyone know if the patch mentioned in this thread is available now, or if not how I find 'ofboot.b? is it in open firmware or in ubuntu? if in openfirmware, could someone please provide the full commands to edit this script as I really am brand new to OF and my newly learned 'printenv' is not showing anything close!

many thanks in advance!

---

