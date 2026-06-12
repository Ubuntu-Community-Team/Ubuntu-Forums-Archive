---
title: "T22 Microphone Issues"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by grj23 on 2008-03-02
Hi

I've installed Ubuntu 7.10 Gutsy Gibbon on my IBM T22.  I had to install with the alternative installer, and even then the screen would go blank after the splash instead of going to the login screen.  I fixed this with these instructions: ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Suspend_and_Hibernate_with_ACPI](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Suspend_and_Hibernate_with_ACPI)
) which basically say add "acpi=force" to the end of the kernel line in menu.lst

I then installed skype (using medibuntu, not [www.skype.com](www.skype.com) for reasons which I don't really understand, but apparently it's better)

On calling the echo123 my voice cannot be heard, i.e. there's something wrong with the microphone.  This is comparable with the issue here I think ([http://ubuntuforums.org/showthread.php?t=630522](http://ubuntuforums.org/showthread.php?t=630522)).  I get the same error as this.

There's a solution listed here ([http://ubuntuforums.org/showthread.php?t=333341](http://ubuntuforums.org/showthread.php?t=333341)), but unfortunately this says to add acpi=off to the end of the kernel line in menu.lst.  I've not tried this, because it was very painful to get the computer to boot properly in the first place and I don't want to mess around with this!

I also found a post on [http://samjordan.co.uk/?p=25](http://samjordan.co.uk/?p=25).  Does anyone know whether this is a good idea?  It looks a little inelegant, but if it works I'll happily give it a bash!  

Does anyone have any other ideas of how to fix this microphone?  Thanks

---

### Post by mike.desmo on 2008-03-02
The ACPI=force usually can be rectified by updating the bios. This can easily be accomplished by going to the IBM/Lenovo site, entering the model number, going to the drivers index and have the program check your bios. If it does need updated follow the instructions and it works well. The bios update can fix many of the other problems you are having

---

### Post by divindavid on 2008-03-02
i could never get my mic to work on my T22

---

### Post by divindavid on 2008-03-02
just to be sure go to the top right of you desktop and double click on the sound icon and make sure that you mic is not muted

---

