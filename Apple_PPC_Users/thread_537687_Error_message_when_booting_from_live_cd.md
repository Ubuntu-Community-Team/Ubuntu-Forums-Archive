---
title: "Error message when booting from live cd"
date: 2007-08-29
forum: Apple PPC Users
---

### Post by kumakuma on 2007-08-29
Hi all

I've been using ubuntu 7.04 on my pc for a couple months now and experimenting with other os's from live cds for fun. I like the stability of ubuntu, and decided to try it on my 800MHz G4 mac. I tried it on a G5 ppc at work to test the live cd and it worked fine (although after it was installed--as a dual boot, along w OSX--we can't get any options for which os to boot and OSX boots every time. but maybe this should be a separate thread?)

anyway, when i restart my mac w the disk in the drive, i press "c" and i get the message to boot from the live cd. it starts fine and the ubuntu logo comes up as normal (though the colours of the ubuntu logo are wonky and psychedelic) and it starts to work, but quickly it stops and i get this message:

/bin/sh: can't access tty; job control turned off
(initramfs)

can anyone shed some light on this predicament? i really want to get this working but have no idea what to do? is it hopeless?
Thanks!

---

### Post by ddrichardson on 2007-08-29
There are several bug reports realting to this, the two most likely are [here ]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084")and [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964").

The only two suggestions I have come across are to:
1. Change the BIOS setting to Compatabilty Mode for SATA
2. Adding combined_mode=libdata to the boot parameters (press F6 at the menu)

---

### Post by kumakuma on 2007-08-29
thank u very much for your prompt reply, ddrichardson. it's nice to see people are so helpful here!

but, i apologize, i am not adept enough w this to quite follow your meaning. i am still very green, though i am really interested in learning how to use linux and the terminal commands etc. there is no one around who can give me the hands-on tutorials i need (i am a non-japanese living in japan, and haven't done this before). 

anyway, what i am saying is: could you please spell out your meaning and tell me more specifically what i need to do, if you have the time?

thanks again!

---

### Post by ddrichardson on 2007-08-29
OK - when Ubuntu boots and gives you the initial menu - press F6 and at the end of the line it gives you add:```
combined_mode=libdata
```
Then press enter.

If this still doesn't help then reboot and go into the BIOS menu - usually F10 or Del. Look under SATA settings and change it to Compatability Mode. Select Exit and Save Changes then reboot.

If these don't help - you're best bet is to follow the two linked bug reports because this problem only seems to have cropped up fairly recently. If is apparently rectified in the next 7.10 release.

---

### Post by stmiller on 2007-08-29
> **ddrichardson said:**
> 
If this still doesn't help then reboot and go into the BIOS menu - usually F10 or Del. Look under SATA settings and change it to Compatability Mode. Select Exit and Save Changes then reboot.


ddrichardson: This is the PowerPC section and Macs don't have a BIOS, nor do they use GRUB.  :)

And as for booting the live CD: There are numerous problems with that Live CD and PowerPC machines. It is released from Ubuntu 'as is,' and untested. So it is recommended that for installing you use the alternative PowerPC CD which goes right to an installer. (No desktop).

---

### Post by ddrichardson on 2007-08-29
> **stmiller said:**
> ddrichardson: This is the PowerPC section and Macs don't have a BIOS, nor do they use GRUB.  :)

And as for booting the live CD: There are numerous problems with that Live CD and PowerPC machines. It is released from Ubuntu 'as is,' and untested. So it is recommended that for installing you use the alternative PowerPC CD which goes right to an installer. (No desktop).

So it is - flipping RSS feeds. I really should pay more attention. :-)

---

### Post by kumakuma on 2007-08-30
thanks guys. appreciate the tips. i tried a few more times before i got yer replies and eventually it worked as it normally should, without any extra help from me. haven't been able to get my internet connection to work yet, but i imagine i should do with a little more effort...
thanks again!

---

### Post by fuzzybunny on 2007-10-12
Also having this problem with a 400Mhz G4...

Can anyone help?

---

