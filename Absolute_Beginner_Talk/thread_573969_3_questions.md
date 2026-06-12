---
title: "3 questions"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Eric Lee Elliott on 2007-10-12
Where can I find trouble shooting sequences?  For instance, sound system does not work, what is first command to test for what?  Second command?  Maybe a flow chart for testing when external HDD is not found?

Question 2, where is a command reference arranged so I can find command I need when I do not know name of command?  For instance, I have no idea how to find a command to ask what is screen resolution.  For instance, I have no idea how to find a command to ask what is current sound driver.

Question 3, how can I slow or pause boot process to see what is mounted, started, found or failed during boot?  How do I stop much of boot from being concealed?  Am I asking wrong question, should I find this info some other way?

Question 4 of 3,  Where is a description of script files or what is controlled by which script?

---

### Post by nest on 2007-10-12
1) [google]("http://www.google.com.ar").

2) [linuxcommand]("http://www.linuxcommand.org/") is a nice guide. guides of commands are everywhere on the net so...

---

### Post by overdrank on 2007-10-12
> **Eric Lee Elliott said:**
> Where can I find trouble shooting sequences?  For instance, sound system does not work, what is first command to test for what?  Second command?  Maybe a flow chart for testing when external HDD is not found?

Question 2, where is a command reference arranged so I can find command I need when I do not know name of command?  For instance, I have no idea how to find a command to ask what is screen resolution.  For instance, I have no idea how to find a command to ask what is current sound driver.

Question 3, how can I slow or pause boot process to see what is mounted, started, found or failed during boot?  How do I stop much of boot from being concealed?  Am I asking wrong question, should I find this info some other way?

Question 4 of 3,  Where is a description of script files or what is controlled by which script?

HI and hope this link will help with sound
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
For screen resolution this link will help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Good luck!

---

### Post by Midwest-Linux on 2007-10-12
Sound system does not work...

 If you just installed Ubuntu Linux, and the built in soundcard does not work....BUT the soundcard worked when you had windows. A newer soundcard added to the PCI slot should do the trick. I encountered this problem with the IBM 300 GL computer. It had a legacy soundcard, but Ubuntu could not detect it or find a driver for it. No matter what I did I could not fix it...I found another soundcard in a defunct computer that I had and added it to the computer and the sound issue was instantly solved...

---

### Post by hyper_ch on 2007-10-12
all of the booting process should be logged to /var/log/syslog

alternatively you can turn off the boot splash and then you will see the actual booting process.

---

