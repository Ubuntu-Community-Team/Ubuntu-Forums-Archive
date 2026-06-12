---
title: "Error while installing."
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by linuxisee on 2007-11-27
I just downloaded the new Ubuntu 7.10 Gutsy Gibbon and burned it on a cd and then booted it.
After I click on Install Ubuntu i get this error

[0.42400..MP-BIOS bug-8254 timer boot not connected to IO-APIC]
[0.42400.kernel panic-not syncing:IO-APIC+timer doesn't work.Boot with apic=debug and send report.Then try booting wiht the 'noapic' option.

help me.I am not able you use the much hyped and favored Linux OS.. 
Thank You.

---

### Post by Ub1476 on 2007-11-27
It's probably some missing files on the CD. Can you run a CD check on the boot menu?

---

### Post by linuxisee on 2007-11-27
Can you tell me exactly what the error is because this happened when i tried to install the older Ubuntu version.
Wil try and tell u..just stay online..for a while

Thanks..

---

### Post by linuxisee on 2007-11-27
ya i tried to do a cd check and the same error appears again.. 
As i told u the same error occured in the older version of Ubuntu.As ubuntu is for sharing i had given the cd to my friend and he installed it on his PC..

---

### Post by Sef on 2007-11-27
What are your system specs?

---

### Post by Ub1476 on 2007-11-27
Actually it doesn't looks like its a CD error, but hardware. You might want to take a look [here]("http://ubuntuforums.org/showthread.php?t=191355&page=4&highlight=ioapic").

---

### Post by linuxisee on 2007-11-27
Here it goes
AMD Athlon X2 5200+
1GB RAM 
ASUS M2N-MX SE Mobo
XFX Geforce 8500GT 

If you want so more detail specs tell me.. 
Thankx.

---

### Post by linuxisee on 2007-11-27
> **Ub1476 said:**
> Actually it doesn't looks like its a CD error, but hardware. You might want to take a look [here]("http://ubuntuforums.org/showthread.php?t=191355&page=4&highlight=ioapic").

hmm...cant actually figure out wht is it...
can u xplain me .. in simple language.. hehe/ /

---

### Post by ukripper on 2007-11-27
Try 64 bit version

---

### Post by linuxisee on 2007-11-27
aah.. i was gonna download the 64 bit version bt the ISO read "can be used for both 32 bit and 64 bit computing"
Now this statement means i should be able to boot from this CD.
And I knw AMD is 64 bit  ... :)

---

### Post by horowitz53217 on 2007-11-27
I currently have the exact same problem, and I also have tried installing both the 32 and 64 bit versions.  I have a Gateway MT3421, AMD Turion 64 machine.  I really have no idea what to do about this error message.

Scott

---

### Post by Ub1476 on 2007-11-27
Here's what you can try:

1. If you have another OS on your comp, flash your BIOS (update). You'll probably find drivers on your manufactures website.

2. Add noapic to your boot file 

> **Wyldeman said:**
> This is from FOOTER and it worked for me. ADM dual core 5200 myself

 boot to the cd
go down at least on with the arrow
select F6
arrow down to the second line as the top will light up as you go down
at the end of the command do as Footer said add " noapic " without the quotes
Worked for me and i tried all other things
Thanks Footer!!
[http://ubuntuforums.org/showthread.php?t=334083&highlight=MP+bug%3A+8254+timer+to+IO-APIC](http://ubuntuforums.org/showthread.php?t=334083&highlight=MP+bug%3A+8254+timer+to+IO-APIC)
:guitar: :guitar: 

Thier is NEVER a dumb question!
  
3. Edit your BIOS configuration: 

> **mvalderrama said:**
> 
Enter the BIOS Setup utility by pressing the F2 key while the system is booting up and performing POST. 

On the BIOS Main Menu screen, select the Advanced tab to open the Advanced menu screen. 

On the Advanced menu screen, select ACPI Configuration. 

On the ACPI configuration screen, select Advanced ACPI Configuration. 

Change the field to Disabled for ACPI HPET Support. 

Press and release the right arrow key until the Exit menu screen is displayed. 

Follow the instructions on the Exit menu screen to save your changes and exit the Setup utility.

4. As the error message said:

> Boot with apic=debug and send report.Then try booting wiht the 'noapic' option


There are some options for booting on the CD menu, see if you can find anything related there. Hope you get it sorted out:)

---

### Post by ukripper on 2007-11-28
> **Ub1476 said:**
> Here's what you can try:

1. If you have another OS on your comp, flash your BIOS (update). You'll probably find drivers on your manufactures website.

Please give [COLOR="Red"]**warning**[/COLOR] to users when suggesting flashing BIOS(it can break your system if things go wrong and not always recommended on systems today) flashing BIOS was for old hardware when there was no way out and should be used as last resort on new hardware!

---

### Post by horowitz53217 on 2007-12-06
Sadly, I can't even boot to a livecd anymore for ubuntu or any of its derivative OS's.  I don't want to try flashing my bios, because this is a new computer and i use it for work, and it would be a real pain if it screwed up.  I wish there was a less risky solution.

Scott

---

