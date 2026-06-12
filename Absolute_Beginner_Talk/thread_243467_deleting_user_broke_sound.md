---
title: "deleting user broke sound"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by thoffland on 2006-08-25
I'm on the 64bit Dapper LTS and had created an extra user for Samba file sharing. I deleted that user and now I dont have any sound. If I restore from backup my /etc folder, it reinstates the user, but I have sound again. I've tried reinstalling drivers, and have followed this thread: [Compresensive sound...]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+cards")but still cannot get it to work. 

If I click System > Preferences > Sound there is no sound card listed. If I right click on the speaker in the top right panel of Gnome, I get an error message. 

Has anyone had this problem? Any ideas on how to fix it?? 

Here's my system:
Dapper Drake 6.06 LTS
AMD 64 4400+ X2

Thanks for any help!

---

### Post by Metacarpal on 2006-08-25
I have a question: when you installed Ubuntu, did sound work out-of-the-box, or did you have to install a driver, configure, etc?  If you did, what user were you logged in as when you did it?

It's possible your driver or configuration files are stored in the user account's home folder...

---

### Post by thoffland on 2006-08-25
Yes, everything worked out of the box, I didn't do anything special when I installed. I do have onboard sound which I disabled in the bios to get the usb speakers to work.

I only created the other users to share files for other computers so I never logged in as them. I have usb speakers, and never had a problem until now. I could leave the user there, but I'd rather solve the problem and learn from it. 

I'm using the backup/restore utility listed in Automatix, and cannot view the folders by themselves without doing a restore... I dont think??

---

### Post by Metacarpal on 2006-08-25
Hm.  I have no idea what's causing this then.  And I don't use Automatix, so I don't really know much about their backup utility.

Anybody else?

---

### Post by thoffland on 2006-08-25
> **Metacarpal said:**
> Hm.  I have no idea what's causing this then.  And I don't use Automatix, so I don't really know much about their backup utility.

Anybody else?

Thanks for checking! I might have to do a restore again and compare the /etc files to see what the difference is.

---

### Post by thoffland on 2006-08-27
After restoring I was in the same boat... then I reinstalled Ubuntu and still no sound.. not even on the Live CD before install. I started checking the hardware and noticed that the light on my hub wasn't lit... tried a diff cable and voila... after rebooting I had sound. So... I put myself through all that for nothing really, but I guess I learned from it. 

Thanks again for the help.

---

### Post by Metacarpal on 2006-08-28
Glad you got it working again!

Nothing worse than when hardware goes quirky at the same time you make a software change!

---

