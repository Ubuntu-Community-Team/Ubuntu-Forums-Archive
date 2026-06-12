---
title: "Help Needed Please, system screwed"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Gary.M on 2007-06-25
I've been running Kubuntu for several weeks, thinking to move away from WinXP.

All has been running fine, and I have the system configured and productive.

This morning when I started up and logged in I got a message:

Error KDE Panel

"The process for the trash protocol died unexpectedly"


I cannot delete files, if I open say Kedit, or Open Office and try to save a file the app locks solid. Open Office locks the machine when I do this and the only way out is the power button.

Suddenly my install has become unusable.

Has anyone got some pointers?

Thanks...

---

### Post by alan_daniel on 2007-06-25
May seem obvious, but have you tried rebooting?

---

### Post by Gary.M on 2007-06-25
> **alan_daniel said:**
> May seem obvious, but have you tried rebooting?

Oh yes, multiple times. Also renamed the trash folder incase there was a problem. At reboot it was recreated empty. Same error though. Started in recovery mode and did fsck on the home partition. Clean.

The only thought I have is that during the last session yesterday I did a lot of file / folder reorganisation on a couple of partitions on the system. Maybe there was something that went wrong in that process....

I'm lost for ideas...

---

### Post by alan_daniel on 2007-06-25
What did you move in the reorganization? Was it something other than in /home?

---

### Post by Gary.M on 2007-06-25
> **alan_daniel said:**
> What did you move in the reorganization? Was it something other than in /home?

Only documents and files on a shared Ext3 partition that I created for storage of docs between WinXP and Kubuntu. It is mounted to a folder in my home partition, which itself is on a separate partition to my root.

---

### Post by Gary.M on 2007-06-25
OK, I may have recovered the situation.

As it was a KDE error I installed the ubuntu (Gnome) desktop

In there I used a file manager to test creating and deleting some files and folders in home

Created some text files and saved OK.

All seemed OK.

There was some problem opening location "home" from the ubuntu bar. That was a worry.

Then I couldn't logout from the ubuntu desktop. nothing happened at all when clicking on the exit icon.

Opened a terminal and did sudo reboot

Signed back in after boot to KDE session. No trash can error message. Trash can was there with all of yesterday's deleted stuff (even though I earlier had manually deleted that folder??) I was able to empty trash. Now all works OK.

Something may have got screwed with the home folder trash system???

I almost thought I was going back to Windows   :-(

---

### Post by Gary.M on 2007-06-30
Well disregard what I wrote. The problem has come back, and so far I haven't been able to fix it...

---

### Post by ruza on 2007-06-30
The only thing that sounds reasonable is that you changed the path to trash folder to some folder that you have no privileges of using. That explaines that deleting of trash folder did not delete any item in thash. Try checking that out.

---

### Post by Gary.M on 2007-06-30
> **ruza said:**
> The only thing that sounds reasonable is that you changed the path to trash folder to some folder that you have no privileges of using. That explaines that deleting of trash folder did not delete any item in thash. Try checking that out.

I wish it was that easy... but no, no changes were made. All OK prior to shutdown, error present after restart. Refer to thread below to avoid thread duplication...

[http://ubuntuforums.org/showthread.php?t=488395]("http://ubuntuforums.org/showthread.php?t=488395")

---

