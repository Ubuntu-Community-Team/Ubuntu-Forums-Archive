---
title: "Some major and minor problems"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-11-29
Just installed Ubuntu. Getting used to this wonderful OS. But here are some problems that needs to be solved.

Major ones:

After logging in, when the QUIT button is pressed for the first time the system freezes for approximately one minute (50 seconds to be precise). Then, the dialog box appears without "HIBERNATE" & "SUSPEND" option. The interesting thing is that it happens only the very first time I try to quit after logging in and the time interval of the freeze is constant i.e. 50 seconds.  I don't mind the missing options but please suggest some ways to overcome this freeze?

The next time when the QUIT button is pressed, the dialog box appears promptly with all the options. But this time when I click on "SUSPEND", system goes to standby mode and when I try to login back the login screen doesn't show up. The processor LED burns continuously indicating that some process is taking place but the system never seems to recover. I've to restart the system to login again. The "HIBERNATE" option works fine. I can do without the "SUSPEND" option but curious to know why this happens and the solution? 

After I switched on the system this morning, I got this message before the login screen appeared:

"/dev/hda2 was mounted 22 times without being checked.
Force Check /dev/hda2 ================================================= |39%"

dev/hda2 happens to be the partition created for Ubuntu.
After the check was over, I was directed to the login screen and logged in. When I tried to QUIT, there was NO freeze, but the dialog box appeared only after 50 seconds and that too without the "HIBERNATE" and "SUSPEND" options. This has been the pattern after this morning. 


Minor ones:

Not able to enable "Extra" or "Normal" Visual Effects in Appearance Preferences for desktop. "The composite extension is not available" is what I get when I try to apply "Extra" visual effects. What is this composite extension? I use a 15" VGA monitor and a restricted video driver.

Not able to play DVD discs. Able to play the .VOB files individually (but without video), so not able to use the menus and other features of the DVD. Any solution?

Not able to play video files in M Player.

---

### Post by philinux on 2007-11-29
click the link on gutsy known bugs

---

### Post by Bheegerji on 2007-11-29
Error opening/initializing the selected video_out (-vo) device." is the message that I get when i try to play video files in M Player.

---

### Post by Bheegerji on 2007-11-29
> **philinux said:**
> click the link on gutsy known bugs


Couldn't find any work arounds.

---

### Post by Bheegerji on 2007-12-02
For the GUI problem, check [here]("http://ubuntuforums.org/showthread.php?t=628540&page=1").

For MPlayer non-functionality, check [here]("http://ubuntuforums.org/showthread.php?t=627148").

For enabling the desktop effects, check [here]("http://ubuntuforums.org/showthread.php?t=628540&page=1")

I think I hadn't enabled the restricted ATI accelerated graphics driver. After enabling it, I was able to play dvd files.

Still have the Suspend/Hibernate problem. Any workarounds?

---

