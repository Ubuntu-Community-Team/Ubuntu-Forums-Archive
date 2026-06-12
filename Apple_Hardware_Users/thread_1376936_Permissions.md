---
title: "Permissions"
date: 2010-01-09
forum: Apple Hardware Users
---

### Post by tweee on 2010-01-09
Hi,
so I installed ubuntu on my macbook pro, and now I get the infamous "still waiting for root device" when booting mac os x.
I was hoping there would be an easy way to fix this, but I couldn't find any solutions that worked (macbook pros don't have a BIOS, or any drives that are easily removable).

Anyway, so I have ubuntu working, and I need some files from OS X before I would consider reinstalling, etc. So I mounted the drive, went to users, etc. and it says that "I don't have the permissions necessary to view the contents of ****".
I did chmod 777 /media/os x/Users/* but that led to "Could not access: No such file or directory" (there's a space between os and x, i think it counts it as two commands or something and I can't rename the drive, oh the irony)

So if someone can give me a way to give myself the permissions to access my files, or maybe just to copy over the whole hard drive to my main computer, or maybe somehow solve the "still waiting for root device", I would be very grateful.
Thanks in advance.

---

### Post by scouser73 on 2010-01-09
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by tweee on 2010-01-09
Hey, while setting the permissions, I get:

"The permissions could not be changed.

Sorry, could not change the permissions of 'os x': error setting permissions: Read-only file system"

the file system on that drive is "hfs+"
but still, thanks a lot for your help!

---

