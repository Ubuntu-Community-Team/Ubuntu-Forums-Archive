---
title: "Thunderbird cross-platform XP"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by matrixunloaded on 2008-04-03
This may be the wrong forum, and if so, I apologize.I am a newbie.

I have managed to get my system up with Ubuntu on Sata1 and XP on Sata 2. I am using Mozilla Thunderbird because it works on both platforms.  Since I can read and write from Ubuntu to the NTFS partition under XP, is it possible to have a common data file resident on the NTFS partition and use it from THunderbird in Ubuntu?

Many thanks!

---

### Post by forrestcupp on 2008-04-03
I don't think so.  It uses a different way of storing things.  The best you'll be able to do is set up the same account on both OS's and export your contacts from one to import into the other.  It is the same situation with Firefox.  I wish they would set them up so we could do that.

---

### Post by Het Irv on 2008-04-03
You would have to auto-mount your NTFS partiton on boot, and change the permissions to read/write.  Then you should be able to just change the Ubuntu's version of Thunderbird to look at / store e-mails in XP's folder.

You also may want to copy the current contents of the Ubuntu folder and move them over.
btw, I don't know the exact steps\, but a few searches in the forums should get you on the right track.


EDIT: oh...well, if they store them differently then my idea doesn't work.

---

### Post by kellemes on 2008-04-03
> **matrixunloaded said:**
> This may be the wrong forum, and if so, I apologize.I am a newbie.

I have managed to get my system up with Ubuntu on Sata1 and XP on Sata 2. I am using Mozilla Thunderbird because it works on both platforms.  Since I can read and write from Ubuntu to the NTFS partition under XP, is it possible to have a common data file resident on the NTFS partition and use it from THunderbird in Ubuntu?

Many thanks!

Easy.. doing this for ages.

First option..
See to it your Windows partition is mounted
Start the Thunderbird Profilemanager from Linux like so.. "thunderbird -profilemanager" and create a profile (or use the default one) that points to the profilefolder on Windows.. to be found here (%APPDATA%\Mozilla\thunderbird\Profiles\xxxxxxxx.default)

Second option.. this is how I have it setup..
Create a seperate partition to use as sharedisk, I have it partitioned as FAT32.
Copy the profilefolder to the shared disk and point the profile you created (thunderbird -profilemanager) to this folder, you can do this from Linux **and** from Windows just as well.

Default location of Profilefolder on XP = %APPDATA%\Mozilla\thunderbird\Profiles\xxxxxxxx.default
Default location of Profilefolder on Ubuntu = /home/<username>/.mozilla/thunderbird/xxxxxxxx.default

You can do the same thing with firefox..

More info about the profile folders.. [http://kb.mozillazine.org/Profile_folder_-_Thunderbird]("http://kb.mozillazine.org/Profile_folder_-_Thunderbird")

---

### Post by Tristam Green on 2008-04-03
You could also look into your mail's options and see if it has IMAP support, but that's only if you're concerned with having a copy of your mail available in Windows and Linux.  As for themes and such, that's more along the lines of kellemes's post.

I can understand the want to only have a single profile though :-)

---

### Post by forrestcupp on 2008-04-03
> **kellemes said:**
> Easy.. doing this for ages.


Sweet!  I'm glad I was wrong.  I'll have to try that out.

---

### Post by forrestcupp on 2008-04-03
Well, I pointed my Linux profile to my Windows folder, and it didn't pick up the account that I had already created in Windows.  I had to create a new account in that profile folder.  So I really don't see how that will allow me to share the same account with Thunderbird in Windows.  Any tips for me?

---

### Post by privaterolf on 2008-04-03
> **forrestcupp said:**
> Well, I pointed my Linux profile to my Windows folder, and it didn't pick up the account that I had already created in Windows.  I had to create a new account in that profile folder.  So I really don't see how that will allow me to share the same account with Thunderbird in Windows.  Any tips for me?

I've heard you can use a shared directory, accessible by both Ubuntu and Windows (with special free software) to view ext3 partitions (Linux/Ubuntu).

I'll find the link, as I'm going to try that out tonight.

I formatted part of my hard drive as 

/home

Which you can set up in Windows to be shared.

---

### Post by rsambuca on 2008-04-03
> **forrestcupp said:**
> Well, I pointed my Linux profile to my Windows folder, and it didn't pick up the account that I had already created in Windows.  I had to create a new account in that profile folder.  So I really don't see how that will allow me to share the same account with Thunderbird in Windows.  Any tips for me?

I am afraid you must be doing something wrong, because if they are both pointed to the same profile, you should be using just the one profile.  Open up the Thunderbird profile manager in both OS's to make sure.

---

### Post by rsambuca on 2008-04-03
> **privaterolf said:**
> I've heard you can use a shared directory, accessible by both Ubuntu and Windows (with special free software) to view ext3 partitions (Linux/Ubuntu).

I'll find the link, as I'm going to try that out tonight.

I formatted part of my hard drive as 

/home

Which you can set up in Windows to be shared.

You can use the [fs-driver]("http://www.fs-driver.org/") for windows to access the ext2/3 drives.

---

### Post by kellemes on 2008-04-04
> **forrestcupp said:**
> Well, I pointed my Linux profile to my Windows folder, and it didn't pick up the account that I had already created in Windows.  I had to create a new account in that profile folder.  So I really don't see how that will allow me to share the same account with Thunderbird in Windows.  Any tips for me?

Not really.. it should work.
From Linux I simply create a profile pointing to the folder created by TB-Windows and I share it all.

---

