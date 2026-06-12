---
title: "Resolving Windows booting issues"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Enigmaman on 2008-02-02
OK, this is getting desperate now!

I'm getting a message 'Error loading operating system' when I try to Dual Boot.

Windows XP is still there. I cannot install Ubuntu BTW as the Live cd has a damaged file.

How can I resolve this please? Bearing in mind that I cannot install to the hard disk at present.

Are there.are boot managers I can use - maybe from USB drive or something?

Then how do I get to boot straight into Windows from the hard disk again?       

Installing  Linux has been a bad experience so far but I am willing to give it one last shot  - but need to sort this out asap.:confused:

TIA...

---

### Post by bwhite82 on 2008-02-02
To fix your Windows booting problem simply insert your Windows install disk, make it goto a console (been a while, can't remember exactly how) then issue the command fixmbr

---

### Post by dstew on 2008-02-02
Yes, you use the Windows Recovery console on the Windows CD. See [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by Enigmaman on 2008-02-02
That simple?

Thankyou - I will try this.

---

### Post by Enigmaman on 2008-02-03
Tried fixmbr - didn't work.

 It asked me which installation to go to, and not knowing what this meant, I hit '1'; and Enter.

I then entered the command at the c:<Windows prompt (i think).

Ant more suggestions please? :(:confused:

---

### Post by bwhite82 on 2008-02-03
how many installations do you have? you did the command: fixmbr from the prompt? (c:/) and it didn't work? There is another one to try as well: fixboot . If you have more than one installation, try both of them. Cheers.

---

### Post by Enigmaman on 2008-02-03
I tried both commands from the c:\ prompt. 

It said it had writtena new boot sector but iti is still not booting into Windows:confused:

---

### Post by dstew on 2008-02-03
You have to be sure the BIOS is set to boot the drive that you did fixmbr to, and that drive has to be your WIndows drive. If you do fixmbr to the Ubuntu partition, it won't boot properly. Did you read the [Microsoft page]("http://support.microsoft.com/kb/314058") about fixmbr?

---

### Post by Enigmaman on 2008-02-04
Thanks - I did that. It  seems from the Windows NGs that i ned to create a floppy with a load of commands writtento it. :confused:

---

### Post by oedha on 2008-02-04
no.....just like soldierboy said
boot from windows installation cd......
choose recovery mode....
usually....choose 1
then you'll be asked for administrator password ( you have this right ? )
then...from c:\windows...type fixmbr
then fix boot
just follow their simple command
then restart your computer.......from the harddisk...remove the cd

~E~

---

