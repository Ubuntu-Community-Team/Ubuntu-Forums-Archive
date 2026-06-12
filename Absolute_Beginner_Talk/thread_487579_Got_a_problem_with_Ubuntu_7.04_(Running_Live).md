---
title: "Got a problem with Ubuntu 7.04 (Running Live)"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Tygra on 2007-06-29
Hey.. Just received Ubuntu 7.04 from my lecturer to work on my project at home. I've run the CD but i have'nt really got any where? I don't wish to install Ubuntu, just to run the live CD bit. I've also tried restarting my comp but still nothing.. Any help gladfully accepted. Be kind i am a newbire lol.

Cheers, Scott :)

---

### Post by Seisen on 2007-06-29
Did you set your bios to boot the cd first instead of the harddrive that could be the problem.

---

### Post by whizbaby on 2007-06-29
Hello and welcome to ubuntu.
Could you try to be somewhat bit more 'verbose'? That means, if you have a problem, try to put some useful information with it, like

-do you have enabled boot from CD in your BIOS?
-which install cd did you use?
-what hardware do you have?
-what exactly did happen, where does it hang, what do you see?

---

### Post by overdrank on 2007-06-29
> **Tygra said:**
> Hey.. Just received Ubuntu 7.04 from my lecturer to work on my project at home. I've run the CD but i have'nt really got any where? I don't wish to install Ubuntu, just to run the live CD bit. I've also tried restarting my comp but still nothing.. Any help gladfully accepted. Be kind i am a newbire lol.

Cheers, Scott :)

Hi & welcome, when you boot your system do you get the options to run or install ubuntu screen or does the system boot straight to windows? If so make sure you bios is set to boot to cd first and then this will let you run the live cd.

---

### Post by Tomosaur on 2007-06-29
What's the problem, exactly? Are you getting an error message, or is the CD just not booting at all (ie, it just goes straight to Windows, or whatever your current operating system is?).

If the computer is simply not noticing the CD at all, then it sounds like your BIOS is set to boot from hard drive first. Restart your machine, and look very closely. You should see something which say 'Hit del to enter setup'. The actual key you need to press may be different, but it's normally the del key, or F2. Just keep hitting that key until you get to to the BIOS setup screen (you will know when you're there). Now you need to find your boot options. Just look around until you find something like "Boot Order" or "Boot Devices" or something like that. If I'm correct, the device set to boot first will be your hard drive. Use the instructions on screen to change the first device to be your CD ROM drive. Normally it's just a matter of highlighting first line in the list, hitting enter, and then selecting your CD drive, but different computers have different setup screens so it's impossible to say for sure. Once it's done, find the button to press to 'Save and exit'. It's very important that you save the setup, because your machine will reboot once you exit. If all goes well, your machine should boot the Cd drive first, notice the Ubuntu CD, and start to boot Ubuntu.

Alternatively, some machines have a 'quick select' option. On mine, I just hit the escape key during boot up, and a little box pops up from which I can select the device to boot from. Not all machines have this, however.

If these methods don't work, then it could be that the CD he's given you is blank. Is it an official Ubuntu CD (ie, with Ubuntu artwork on it), or is it one he's burned himself? If it's one he's burned himself, then in Windows, put the CD in the drive, go to My Computer, right click the CD, and select 'Explore'. Let us know what's on it and we'll see what we can do :)

---

### Post by Tygra on 2007-06-29
Cheers lads.. Ye it was a fact that my BIOS looking in my hard drive first so i had to change it to CD Drive. Thanks again for your help, much apreciated.

---

### Post by whizbaby on 2007-06-29
> **Tygra said:**
> Cheers lads.. Ye it was a fact that my BIOS looking in my hard drive first so i had to change it to CD Drive. Thanks again for your help, much apreciated.
ROTFL yeh were good :)

---

