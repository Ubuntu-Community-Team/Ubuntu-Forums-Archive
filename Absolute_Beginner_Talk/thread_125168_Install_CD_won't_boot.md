---
title: "Install CD won't boot"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Rubytuesday on 2006-02-03
Hi there, 
I'm trying to install Ubuntu over Xandros on an old W98 PC, but it seems my CD drive is too dated to boot from a CD. With Xandros, I had to make a floppy CD to get through the installation - would following the same instructions in the Xandros manual (except that I'm doing it with Ubuntu) work? 

Also, the Xandros OS on the system won't boot fully - I'm going to try kill disc to clear the HD and start fresh. Is this the best option to take? 

Any suggestions would be much appreciated :) 
Thanks, Ruby

---

### Post by Mustard on 2006-02-03
If you can't boot from your CD-ROM Drive, go here [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

---

### Post by Rubytuesday on 2006-02-03
Thanks very much, will give it a go :)

---

### Post by Rubytuesday on 2006-02-03
Okay, apologies for the stupidity, but if someone can help spell out the below instructions, I'd be very grateful...

1.Smart Boot Manager is on the Breezy install CD, in the /install folder. Otherwise, you can  download it. (for more information about this,  click here.) 
[COLOR="Blue"]Do I need to open the Breezy CD on my main computer and clcik on this folder? [/COLOR]

2.Now we need to make a boot floppy. To do this, use a utility called  rawwrite. (for more info about this,  click here.) 


3.First format the floppy. In windows, open dos prompt and type c:\> format a: 
[COLOR="Blue"]How do I open dos prompt? Is that the start-run-cmd line in Windows? Sorry...lifetime Mac user trying to work this out![/COLOR]

4.Then use rawrite command: rawrite -f sbootmgr.dsk 
[COLOR="Blue"]I just type this in in the command line? [/COLOR]

Apologies for my ignorance...

---

### Post by steve.horsley on 2006-02-03
[QUOTE=Rubytuesday]Okay, apologies for the stupidity, but if someone can help spell out the below instructions, I'd be very grateful...

1.Smart Boot Manager is on the Breezy install CD, in the /install folder. Otherwise, you can  download it. (for more information about this,  click here.) 
[COLOR="Blue"]Do I need to open the Breezy CD on my main computer and clcik on this folder? [/COLOR]
[/QUOTE]Don't know. Look for the filenames rawrite.exe and sbootmgr.dsk as named below.> 
2.Now we need to make a boot floppy. To do this, use a utility called  rawwrite. (for more info about this,  click here.) 


3.First format the floppy. In windows, open dos prompt and type c:\> format a: 
[COLOR="Blue"]How do I open dos prompt? Is that the start-run-cmd line in Windows? Sorry...lifetime Mac user trying to work this out![/COLOR]
Yes. Start-run-cmd> 
4.Then use rawrite command: rawrite -f sbootmgr.dsk 
[COLOR="Blue"]I just type this in in the command line? [/COLOR]
Yes

Good luck.

---

