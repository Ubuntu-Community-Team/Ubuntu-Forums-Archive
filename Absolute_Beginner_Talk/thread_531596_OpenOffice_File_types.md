---
title: "OpenOffice File types?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by charlie9090 on 2007-08-21
Hi all...I've only heard of Ubuntu a few weeks ago so please bear with me if (& I probably will) I sound stupid. I installed Ubuntu a couple of days ago with the intention of using the spreadsheet facility, as the estimation sheets I have for my work has been designed for use with OO. I'd like to have a setup for my work completely seperate from windows that nobody else can access or accidentally destroy, so I thought i'd give this a try!
What I've done is install a 2nd HDD (80gb) dedicated to Ubuntu, installed Ubuntu with no problems. I love the way this os acts & would like to learn more. 

MY PROBLEM: I have files I've been using with OO under windows xp with an .ods extension. When I reboot to Ubuntu & open these files they open with 'read only' in the title bar? After some editing of the file I try to create a new folder (say 'UBN files') & save onto an existing external HDD, but am unable to even create a folder? What I'd like is to be able to edit these spreadsheets from both OS's & save to the one location...is this possible? Do I need to create another partition on the external HDD with something other than NTFS?

I hope I haven't carried on too much here for my 1st post...any help would be greatly appreciated. 

Charlie.

---

### Post by Jimmyfj on 2007-08-21
What you need for your external NTS drive is NTFS Configutation Tool. You'll find that in:

Programs/Add/Remove/System tools - Just install the program and enable read and write access

---

### Post by AceofSpades19 on 2007-08-21
unless you install the ntfs-3g package NTFS is read only

---

### Post by toidi on 2007-08-21
I had a similar prob writing to my original ntfs drive. I blagged this from somewhere and it sorted it all out.

Open up a terminal/konsole and follow these steps. 

Step 1: Install NTFS-config
sudo apt-get install ntfs-config

Step 2: Open NTFS configuration tool
sudo ntfs-config

Step 3: Enable writing
Tick the check box to enable write support for internal device. However, if you want to write to a external hard drive, you also select external option. Then, you click on button "Ok" to confirm and enjoy it.

Hope this helps..

---

