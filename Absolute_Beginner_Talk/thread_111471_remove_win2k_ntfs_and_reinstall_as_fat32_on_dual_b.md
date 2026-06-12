---
title: "remove win2k ntfs and reinstall as fat32 on dual boot?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by jockjunior on 2006-01-02
HI all.
 I have win2k on 1st drive 5gig and Ubuntu on 2nd drive 20gig. I have copied grub onto a floppy and I can boot using it. Now, can I remove win2k and reformat the drive as fat32 so its accessible from Ubuntu and then re install win2k and  copy back grub to the mbr of my harddrive? Or alternatively just delete win2k altogether and just reformat the drive as fat32 without putting an OS on it ? 

thanks

Jock

please ignore this thread . re posted with better title explanation

---

### Post by jockjunior on 2006-01-02
HI all.
 I have win2k on 1st drive 5gig and Ubuntu on 2nd drive 20gig. I have copied grub onto a floppy and I can boot using it. Now, can I remove win2k and reformat the drive as fat32 so its accessible from Ubuntu and then re install win2k and  copy back grub to the mbr of my harddrive? Or alternatively just delete win2k altogether and just reformat the drive as fat32 without putting an OS on it ? 

thanks

Jock

---

### Post by jockjunior on 2006-01-02
HI all.
 I have win2k on 1st drive 5gig and Ubuntu on 2nd drive 20gig. I have copied grub onto a floppy and I can boot using it. Now, can I remove win2k and reformat the drive as fat32 so its accessible from Ubuntu and then re install win2k and  copy back grub to the mbr of my harddrive? Or alternatively just delete win2k altogether and just reformat the drive as fat32 without putting an OS on it ? 

thanks

Jock

---

### Post by vasudevank on 2006-01-02
what do you want to know? You are just saying that i could do this or this, Do you want to know which is better

---

### Post by jockjunior on 2006-01-02
Hi, 
yes I want to reinstall it as fat 32 so I can access it from ubuntu or if I delete it all together and go windowless  and just have an empty fat32 drive can I use grub to access ubuntu

jock

---

### Post by vasudevank on 2006-01-02
you can access ubuntu even if windows is corrupted. The only time you couldn't get into anything is if ubuntu root is corrupted, since that is where everything grub resides

---

### Post by az on 2006-01-02
[QUOTE=jockjunior]can I remove win2k and reformat the drive as fat32 so its accessible from Ubuntu and then re install win2k and  copy back grub to the mbr of my harddrive?[/QUOTE]

Yes.

Boot into ubuntu and run

sudo grub-install /dev/hda

(assuming that is the correct device....)

[QUOTE=jockjunior]
 Or alternatively just delete win2k altogether and just reformat the drive as fat32 without putting an OS on it ? 
[/QUOTE]


Why not?  In that case, then why fat32?

---

### Post by jockjunior on 2006-01-02
Thanks for reply,
       fat32 just came to mind thats all . It doesnt matter which as long as its not ntfs.

thanks again

jock

---

### Post by jockjunior on 2006-01-02
Thanks for that info
sorry for delay in reply I got called away

now plucking up courage to dump windows:D 


jock

---

### Post by vasudevank on 2006-01-02
theres not much courage required if you have interenet with linux, because it kicks windoze's as*

---

### Post by ubuntu_demon on 2006-01-02
jockjunior I merged your three threads. Please don't start multiple threads with the same topic.

have fun on the forums and good luck with your problems and a happy new year to everyone :)

---

### Post by jockjunior on 2006-01-03
Apologies for multiiple posting . I was trying to explain myself better and got myself confused with what I had posted.

jock

---

