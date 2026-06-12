---
title: "Fn Keys on Laptop - Toshiba Satellite A60"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Cheshire Black on 2008-03-06
Hello, forums!  I'm an experienced computer user, but I know very little about programming, scripting, and linux.  LOVE Ubuntu, though.

I've gotten 7.10 Gutsy mostly working on my Toshiba Satellite A60-S156 but I cannot finish the job.  I cannot get my function keys to work, and I cannot change my brightness.  I know, I know, it's an old song.  I've read through many postings, including this:
[http://ubuntuforums.org/showthread.php?t=587636](http://ubuntuforums.org/showthread.php?t=587636)

And had no luck.  The advice is either not applicable or does not work.  Like the first post, I also get 

~$ sudo toshset
required kernel toshiba support not enabled.

~$ sudo fnfxd
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).


Now, I should mention that I do not think I have a Phoenix BIOS.  Most Toshiba complaints revolve around that.  Mine says it is an ACPI BIOS.  Does that mean I should be able to get this to work?

Additionally, I looked into installing omnibook, but my laptop model is not supported.

Are there any other thoughts, suggestions, or questions out there?

Thanks in advance!
--Roy

---

### Post by tdrusk on 2008-03-07
Go to System>Preferences>Keyboard Shortcuts and see if there is a shortcut key for your volume up and down and such.

---

### Post by Cheshire Black on 2008-03-07
There are some things listed.

Volume Mute 0xa0
Volume Down 0xaE
Volume Up 0xb0
etc.  

I tried to assign them to their proper Fn+__ keys, but they do not accept my input.  

Also, there is no keystroke in that list to control brightness.

Thanks for the thought though, that was a good idea.  And I did learn about that new menu.
=)

Roy

---

