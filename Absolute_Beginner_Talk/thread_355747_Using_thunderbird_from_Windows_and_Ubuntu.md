---
title: "Using thunderbird from Windows and Ubuntu"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-07
Hi

I have a dual boot Ubuntu and Windows XP home setup.

I would like to use thunderbird from either my WinXP or my Ubuntu setup (with emails downloaded / deleted from whichever OS available in the other) 

Can I do this, and if so how?

Thanks

---

### Post by steve.horsley on 2007-02-07
Yes you can.

Find your profile directory - ~/.mozilla-thunderbird/default on Linux or somewhere under documents and settings under windoze. Copy to a shared drive.

Start **thunderbird -ProfileManager ** and this lets you specify your profile directory (inthe default folder you copied).

This is roughly right. I forget the exact directory names you have to select, but a little experimenting will get you there. I've done it a couple of times, and it was painless enough that this is all I remember of it.

---

### Post by crane on 2007-02-07
Not sure how possible this would be. Have you checked the setting in both windows and linux to see if different directories can be used. In linux all configs are saved in a hidden file in you home directory called .thunderbird in windows it's in a hidden file called C:\Documents and Settings\(user_name)\Application Data\Thunderbird. I'm not sure how to change these settings.

---

### Post by kebes on 2007-02-07
Yes on my work computer I dual-boot and they share a single thunderbird install. It works without trouble. There are multiple ways of doing it. The end result is simply that your profile folder has to be on a shared drive, and then you have to update thunderbird in Windows and Ubuntu to use that profile location.

In thunderbird, you can go Tools > Account Settings, and then update the "Local directory" field.

However I found it even easier to just use a symlink on the Linux side (using the command "ln -s") so that the default profile there points to the folder where the Windows version of thunderbird was storing the profile. (Which I have on a shared fat32 partition.)

---

### Post by ubername on 2007-02-12
> **kebes said:**
> Yes on my work computer I dual-boot and they share a single thunderbird install. It works without trouble. There are multiple ways of doing it. The end result is simply that your profile folder has to be on a shared drive, and then you have to update thunderbird in Windows and Ubuntu to use that profile location.

In thunderbird, you can go Tools > Account Settings, and then update the "Local directory" field.

However I found it even easier to just use a symlink on the Linux side (using the command "ln -s") so that the default profile there points to the folder where the Windows version of thunderbird was storing the profile. (Which I have on a shared fat32 partition.)

Thanks, all done.

---

