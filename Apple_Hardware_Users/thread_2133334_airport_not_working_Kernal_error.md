---
title: "airport not working Kernal error?"
date: 2013-04-07
forum: Apple Hardware Users
---

### Post by Alaska Skier on 2013-04-07
hello world from the north :)

just recently installed ubuntu PPC 12.04 on an old iBook G4, its a slot loading modle with 512 MB of ram and a 1Ghz processor with airport card, the install went fine and it loads up and runs great, all besides the fact that i have no WiFi, this is not due to an airport card not being present (yes, it's underneath the keyboard) and its not faulty (it worked when i had OSX 10.4) when i boot  up after the regular lines of code it goes to the screen saying "ubuntu 12.04" and the little loading dots underneath, while this happens, some lines of red or sometimes orange and white lines of text appear saying that, and this is about what it said as i had barely enought time to read it before it went to the log in screen, "kernal has failed to" and says something along the lines of: load drivers or software or whatever the heck makes your airport card run and tells me to go to some website that it posts there that starts something like: wireless,kernal.org................, i know i am being pretty vague but i just need this to work, ill try and get to the website and post it here but i doubt ill be able to copy it all down in less than 5 reboots

kudos
A.S.

---

### Post by ronald577 on 2013-04-10
I don't think it will work in an Old ibook G4. But still try or you can just give a visit to the ibook gallery to get installed and know more about it.

---

### Post by michiganmac on 2013-04-10
> **Alaska Skier said:**
> hello world from the north :)

just recently installed ubuntu PPC 12.04 on an old iBook G4, its a slot loading modle with 512 MB of ram and a 1Ghz processor with airport card, the install went fine and it loads up and runs great, all besides the fact that i have no WiFi, this is not due to an airport card not being present (yes, it's underneath the keyboard) and its not faulty (it worked when i had OSX 10.4) when i boot  up after the regular lines of code it goes to the screen saying "ubuntu 12.04" and the little loading dots underneath, while this happens, some lines of red or sometimes orange and white lines of text appear saying that, and this is about what it said as i had barely enought time to read it before it went to the log in screen, "kernal has failed to" and says something along the lines of: load drivers or software or whatever the heck makes your airport card run and tells me to go to some website that it posts there that starts something like: wireless,kernal.org................, i know i am being pretty vague but i just need this to work, ill try and get to the website and post it here but i doubt ill be able to copy it all down in less than 5 reboots

kudos
A.S.

I have a similar iBook G4--12" 1.33GHz 1.5 GB Ram. This is what worked for me.

First, open LX terminal, type this and hit return:
[FONT=Lucida Grande]
[/FONT][FONT=Lucida Grande]sudo apt-get update && apt-cache search b43 [/FONT]
[FONT=Lucida Grande]
Wait for all the text to stop streaming in the window and you are returned to the prompt. Then type this and hit return:[/FONT]
[FONT=Lucida Grande]
[/FONT]
[FONT=Lucida Grande]sudo apt-get install firmware-b43-installer

[/FONT]
[FONT=Lucida Grande]You may have to reboot (I can't remember), but you should now have wireless. 

[/FONT]
[FONT=Lucida Grande]
[/FONT]
[FONT=Lucida Grande]
[/FONT]

---

