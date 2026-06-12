---
title: "Install Ubuntu w/ my new computer. HELP PLEASE..."
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by chinx21 on 2007-06-13
Hi there! I have a new computer with the ff. specs:

•INTEL CELERON 331 2.66 GHZ
• A96MP-C2D MOTHERBOARD
• 64 MB INTEGRATED GRAPHICS PORT
• 256 DDR2 667 MEMORY
• 80 GB WESTERN DIGITAL HARD DISC
• 15” MONITOR 
• CDRW/DVD COMBO 

I already install Windows XP on it but I want to install Feisty Fawn.
I want to use Feisty Fawn when surfing on the Internet and XP only when doing reports on its Office Applications. I want to easily use any of the two OS anytime I want without rebooting my computer and able to access all files in my hard disk using any of the two. Would it be possible?

Thanks in advance!:D

---

### Post by Inxsible on 2007-06-13
yes you can install Feisty on your machine. You will need ntfs-3g to write to ntfs drives from Linux and FS driver in windows to read and write to ext3 partitions.

---

### Post by chinx21 on 2007-06-14
Whew! Answer so fast...Thanks! I have additional question. I requested free CD but it will took time before I'll receive it so now, I'm planning to download it to the Ubuntu site but I don't know what should I select on the following?

 Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
 
 64bit AMD and Intel computers
 
 Sun UltraSPARC based

What is the difference between alternate desktop CD and Live CD? Which of the two is advisable to use?;)

---

### Post by Inxsible on 2007-06-14
You should select the 32 bit i386 version. Alternate CD's are also install CD's but they do no have a graphical installation procedure. Everything is text based. They are used by people who have trouble configuring their graphics processor with the liveCD. You should first try with the liveCD, and if for some reason, it gives you problems, then you should go for the alternate one

---

### Post by Gmbrdilos on 2007-06-14
alternate cd is a text based installer, while the live CD is a live demo of the operating system plus the installer.
with low RAM I'd suggest you go with alternate.

---

### Post by chinx21 on 2007-06-14
Thanks guys! :D

Which of the ff. should I download?

  ubuntu-7.04-desktop-i386.iso            15-Apr-2007 14:52  698M  Desktop CD for PC (Intel x86) computers (standard download)

  ubuntu-7.04-desktop-i386.iso.torrent    19-Apr-2007 07:53   27K  Desktop CD for PC (Intel x86) computers (BitTorrent download)

  ubuntu-7.04-desktop-i386.list           15-Apr-2007 14:52   14K  Desktop CD for PC (Intel x86) computers (file listing)

  ubuntu-7.04-desktop-i386.manifest       15-Apr-2007 13:05   31K  Desktop CD for PC (Intel x86) computers (contents of live filesystem)

Is it ok to attach the downloaded file in an e-mail? and  then download it again when I open my e-mail and then burn it. Will the file works?

---

### Post by Gmbrdilos on 2007-06-14
first one

---

### Post by Inxsible on 2007-06-14
> **chinx21 said:**
> Thanks guys! :D

Which of the ff. should I download?

  ubuntu-7.04-desktop-i386.iso            15-Apr-2007 14:52  698M  Desktop CD for PC (Intel x86) computers (standard download)

  ubuntu-7.04-desktop-i386.iso.torrent    19-Apr-2007 07:53   27K  Desktop CD for PC (Intel x86) computers (BitTorrent download)

  ubuntu-7.04-desktop-i386.list           15-Apr-2007 14:52   14K  Desktop CD for PC (Intel x86) computers (file listing)

  ubuntu-7.04-desktop-i386.manifest       15-Apr-2007 13:05   31K  Desktop CD for PC (Intel x86) computers (contents of live filesystem)

Is it ok to attach the downloaded file in an e-mail? and  then download it again when I open my e-mail and then burn it. Will the file works?

I dont think any email program will allow a 698 MB attachment. You will be better off downloading on the machine where you have a cd burner.

---

### Post by chinx21 on 2007-06-14
Thanks guys! i'm downloading Fesity Fawn right now. After I check it through the MD5SUM and burned it successfully. Are there things I need to do in my computer before I start installing it? If yes, what are they?

---

### Post by Ptero-4 on 2007-12-12
You might need to set your BIOS boot sequence to look in your DVD/CDRW drive first (look for the words CDROM in the BIOS screen) and then the HD, floppy drive (if you have) and netboot. Or alternativelly press a key (generally esc or f12) at boot to bring a boot menu (it's better b/c you won't need to fiddle with the BIOS and also b/c it only looks in the selected media during that session so it won't make slow boots later checking your combo drive before booting).

---

