---
title: "Backing Up Files"
date: 2007-12-22
forum: Apple Intel Users
---

### Post by memoIhad on 2007-12-22
Hello!

I'm new to Ubuntu, and I am still learning, so bear with me. I have a laptop, and for some reason (virus or similar) when the laptop opens, it says "error loading operating system" (I had windows XP). However, instead of reformatting and installing Windows, I want to install Ubuntu. My only problem is that I don't want to lose all my files, I know there is a "Preview" mode for  Ubuntu, I went into it, to see if I can access my hard drive through that, but I found nothing. I'm wondering if there is a way that I can access my hard drive and backup the documents on my computer before formatting?? Or can I install Ubuntu without reformatting??

Thanks in advance!:)

---

### Post by jflaker on 2007-12-22
> **memoIhad said:**
> Hello!

I'm new to Ubuntu, and I am still learning, so bear with me. I have a laptop, and for some reason (virus or similar) when the laptop opens, it says "error loading operating system" (I had windows XP). However, instead of reformatting and installing Windows, I want to install Ubuntu. My only problem is that I don't want to lose all my files, I know there is a "Preview" mode for  Ubuntu, I went into it, to see if I can access my hard drive through that, but I found nothing. I'm wondering if there is a way that I can access my hard drive and backup the documents on my computer before formatting?? Or can I install Ubuntu without reformatting??

Thanks in advance!:)

The LiveCD is a preview.  It does nothing to your hard disk until you go through the install routine...You should be able to access your hard disk from the livecd.

backup your user (c:\documents and settings\YourUserName) folder and all things below it to an external location.  You should be able to open all files with the exception of Outlook PST (your email file).  There are ways around this as I did this.

Once you saved your data and if you want to restore your email, let me know...I have done this by installing XP in VirtualBox, setting up Outllook only, opening the data file in outlook......Connecting outlook to IMAP gmail and moved all my mail to gmail.  Once back in Ubuntu, connect to IMAP gmail and pull your email back to your system or just leave it on gmail.

---

### Post by memoIhad on 2007-12-22
Thanks for the quick reply. My problem is that I can't access my computer without Ubuntu. When I load up the computer without the Ubuntu CD in it, it says "error loading operating system". which of course means my operating system (Windows XP) will not work until I re-install and format (I'm guessing this happened after a virus my computer got). What I want to know is if I install Ubuntu, will it erase all files on my computer? Or if there is someway I can backup my files.

---

### Post by Zaff on 2007-12-23
You can probably acces your files throught the Places->Home menu. Once the navigator is launched you should see icons on the left representing hard drives (grey triangles). if you double click the hard drive it should "mount" it and you should be able to read your data from it.

Otherwise here's what you can do providing you have enough free space.

Download the Gparted Live CD and burn it and then start your computer with it the same way you started your ubuntu live cd.
Gparted will allow you to resize your partitions and create new ones. I'm guessing you only have one partition on your disk as most windows install are made that way. So you can resize that partition which will create an empty part of the disk.

Once that's done you can start the ubuntu live cd again and launch the install process. At some point it should ask you if you want to install ubuntu on the whole disk, on the largest free space (what you just created) or if you want to do custom partitionning. If you feel comfortable enough I would advise to custom the partitionning and create seaparate partitions for / and /home. Otherwise just select "largest free space" and it will install ubuntu on there without touching any of your data...

Your Ubuntu partition should be at least 10G if you want to avoid space problems later (although technically it can work with less).

Anyway, Hope you can get all your data back. Good luck.

---

### Post by memoIhad on 2007-12-23
Thanks for the reply. Ok, I'll try what you told me, it doesn't sound all that complicated. I'll post back with the results, THANKS AGAIN!

---

