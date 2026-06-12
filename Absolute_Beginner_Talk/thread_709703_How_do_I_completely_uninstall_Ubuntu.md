---
title: "How do I completely uninstall Ubuntu?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Bunnytard on 2008-02-27
I dual booted ubuntu with vista and I really don't want ubuntu anymore since I never use it. So I want a noob guide on how to uninstall ubuntu. Thanks for the help.

---

### Post by mikewhatever on 2008-02-27
Well, all you need to do is restore Vista's boot loader to the MBR and then delete Ubuntu's partition. Here's a guide [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good Luck.

---

### Post by Bunnytard on 2008-02-27
I don't get any of those things in the guide.

---

### Post by kool_kat_os on 2008-02-27
boot the windows partition and download MBRFIX 1 from download.com and then fix the mbr

EDIT: is ubuntu on a different harddrive or a different partition (dont do the mbr thing if its not on a different hd.)

---

### Post by kool_kat_os on 2008-02-27
NOTICE: DO NOT just delete the ubuntu partition or you wont be able to boot the windows one without reinstalling Ubuntu.

---

### Post by mikewhatever on 2008-02-27
> **Bunnytard said:**
> I don't get any of those things in the guide.

Err..., what?

---

### Post by Aurora@FleetBuzz on 2008-03-10
Before uninstalling Ubuntu, you should make sure that Vista boots naturally.  Here is a guide to restoring the MBR as it was.  You will need the Vista Installation CD to do this.
[http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)
> To perform this operation you will need a copy of your Windows Vista Installation DVD, if you do not have one, you can download a DVD off various torrent sites (ask Google, I claim no responsibility here).

Please not that there are always risks of corrupting your data when toying with the MBR (Master Boot Record) so please back up your data before attempting this.

   1. Insert your Windows Vista Install DVD and boot from it.
   2. After selecting your language options choose the &#8220;Repair your computer&#8221; option in the bottom left corner.
   3. Select your Windows Vista Installation and continue (note: my screenshot does not show an installed OS because there is none).
   4. Open a new Command Prompt window
   5. When command prompt is open, type the following commands (note: my screenshot shows an error as vista is not installed)
         1. Bootrec /fixboot
         2. Bootrec /fixmbr

The MBR/Boot Loader&#8217;s are now repaired, restart your computer and it should boot in to Vista where you can then delete the Linux partitions from the hard drive if you wish.

I recommend a re-boot to ensure that Vista is booting the way you want.  After that, you can safely delete the ubuntu partition using GParted or Vista's partitioner.  BEFORE you extend the vista partition to recover the lost space, I strongly recommend you do a defrag of the Vista partition.  I would not use GParted to extend the Vista partition; I recommend using the Vista partitioner.  Vista is somewhat touchy.

Good luck, but you shouldn't have any trouble.  This is very easy if you pay attention to each step in the process.

---

