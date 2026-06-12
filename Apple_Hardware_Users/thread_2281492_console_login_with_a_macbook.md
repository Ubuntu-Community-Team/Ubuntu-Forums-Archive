---
title: "console login with a macbook"
date: 2015-06-07
forum: Apple Hardware Users
---

### Post by alfred10 on 2015-06-07
Hi everyone!):P
I have a Macbook mid 2009 and I decided to install Ubuntu along with Lion OS. Everything was just fine until I noticed it had a generic video driver and the airport was not working because it had no driver either so I proceeded to install those drivers. The setup asked me to restart and I restarted. After restart I have the login screen infinite loop bug. 
Ok, I found a few options for fixing it but those options involve to log into console pressing Ctrl+Alt+F1 to F6. The thing is I don't know how to achieve this since Macbooks doesn't have an Alt key. I tried different combinations using option, command, ctrl and fn with F1 to F6 but no luck so far. So I bet you guessed it but the question is, how do I enter in the console login?:confused::confused::confused:

---

### Post by ajgreeny on 2015-06-07
I am not aware of what differences there may be between grub in a "normal" PC and a mac, or even if you see a grub menu in a mac system, but if you do get a grub menu, use Enter with the boot item you use highlighted then use cursor keys to get to the line with "quiet splash" near the end.  Delete the words "quiet splash" and type "text", then Ctrl+X to boot.

That should boot you to a tty text command line system with no GUI running and allow you to do what is needed.  It will boot to text mode for that single boot only, and will then revert to normal GUI boot  next time.

If macs do not use grub I'm afraid I can not help, so just ignore this and wait for the next person to help you.

---

### Post by este.el.paz on 2015-06-09
@alfred:

If AJG's advice hasn't worked out, then, on my 09 MBPro the "option" key is the "alt" key.  On my MBPro I believe that I have to also use the fn + ctrl + alt + F1 - F (+) to get to the TTY.  One thing is you do have to be booted in linux to get to the TTY; follwing AJs idea, if you get to the GRUB window there should be "recovery" mode to choose from.

e..

---

