---
title: "Question about GRUB, reinstallation of Windows."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-11-26
Alright, I have Ubuntu installed on one drive (hdb1), and Windows on the other (hda1). I've been having issues with Windows (surprise, surprise!), and I want to reformat my C: (hda1) drive. 

If I do this, will GRUB (or whatever it's called) still allow me to boot in Ubuntu, or will the re-installation of Windows override that?

---

### Post by venkatmangudi on 2006-11-26
Where is GRUB located? Will you be using your Windoze install CD to reformat?

---

### Post by theknave on 2006-11-26
I don't know where GRUB is located :S.

Yes, I'd be using the Windows XP cd to reformat.

---

### Post by turbojugend_gr on 2006-11-26
Yes Grub will be messed up if you re-install windows (Windows will write over MBR, thus erasing GRUB), but go on reinstalling windows and then follow [this SIMPLE guide]("http://doc.gwos.org/index.php/Restore_Grub") to get GRUB up and running again. So simple.

Cheers, TJ.

EDIT: Of course check the guide first, just in case (I don't think that's likely anyway) you think you can't follow it. It is very simple though.

---

### Post by vtel57 on 2006-11-26
If your GRUB is on hdb (most likely), then reformatting hda won't affect it. However, you'll have to make sure that your BIOS is set to boot hdb first. When/if you reinstall Windows on hda, physically disconnect power and IDE cables from your hdb drive or else Windows will insist on corrupting the MBR on that drive during its installation on hda. I don't know why Windows does this, but it does, so be careful. You can later add a Windows entry to your Ubuntu GRUB so that you can choose which OS to boot to at start up.

---

### Post by theknave on 2006-11-26
Sounds easy! Thanks!

---

### Post by turbojugend_gr on 2006-11-26
> **vtel57 said:**
> If your GRUB is on hdb (most likely), then reformatting hda won't affect it. However, you'll have to make sure that your BIOS is set to boot hdb first. When/if you reinstall Windows on hda, physically disconnect power and IDE cables from your hdb drive or else Windows will insist on corrupting the MBR on that drive during its installation on hda. I don't know why Windows does this, but it does, so be careful. You can later add a Windows entry to your Ubuntu GRUB so that you can choose which OS to boot to at start up.

What you say is not false (though it can create problems sometimes, as GRUB may be confusd by the MBR table on windows drive), but the thing is that creating a GRUB entry will take a new user nuts, as it needs someone else to make it for him, and the user must provide all hard drive info to him. While using the Live CD to restore GRUB won't take the user more than 5 mins (since no data is to be installed-apart from GRUB's bytes).

BTW windoz is a facist OS (lol), it is "taught" it's the only system on any PC so it should over-write the booting drive's MBR, physically removing the latter while installing windows, will fool windoz into thinking it's drive is the booting one. Anyway the bottom line is a newcomer should be given the easiest to follow advice.

Best Regards, TJ.

---

### Post by vtel57 on 2006-11-26
> **turbojugend_gr said:**
> 
BTW windoz is a facist OS (lol), it is "taught" it's the only system on any PC so it should over-write the booting drive's MBR...

Heh! How true! :mrgreen:

---

### Post by buddie on 2006-11-26
> **turbojugend_gr said:**
> Yes Grub will be messed up if you re-install windows (Windows will write over MBR, thus erasing GRUB), but go on reinstalling windows and then follow [this SIMPLE guide]("http://doc.gwos.org/index.php/Restore_Grub") to get GRUB up and running again. So simple.

Cheers, TJ.

EDIT: Of course check the guide first, just in case (I don't think that's likely anyway) you think you can't follow it. It is very simple though.

pardon me if i'm wrong, but i don't think this method works for edgy. because it wont let you pass through unless you format the root (/). there's this thing called[ super grub disk ]("http://ubuntuforums.org/newreply.php?do=newreply&p=1811501"). personally i haven't try it yet. but it looks good ;)

---

