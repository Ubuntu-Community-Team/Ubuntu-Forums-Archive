---
title: "KANOTIX help needed"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by haseowolf on 2008-04-03
Alright, I've searched the whole internet (okay, Google.com is not the WHOLE internet) but I'm looking for some help with some problems I'm having with KANOTIX.

My HDD, which is a Windows XP partition, is dying and I want to retrieve my data using KANOTIX, but I've mounted the drive as well as the drive that will be recieving the data, but I can't seem to get the option to read/write new data and I've tried to figure out this whole ntfs thing to get it to work.

How do I get my drive to allow me to copy the data and then paste it onto a new drive?

Any help in finding a solution will be GREATLY appreciated.

Thanks.

---

### Post by haseowolf on 2008-04-03
BUMP

Sorry, I just really need some help figuring this out.

---

### Post by kerry_s on 2008-04-03
you should be able to read & copy the ntfs drive, so i assume your talking mainly about the drive you want to write to.
what is it formated as?
how did you mount it?

---

### Post by haseowolf on 2008-04-03
Right click mount drive, its hda1, so I'm not sure how you mean by how it's formatted.

---

### Post by cotcot on 2008-04-03
Try ntfs-config.
[[COLOR="Red"]Here[/COLOR]]("http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html") is an instruction for feisty. I hope it works for any debian based OS.

---

### Post by haseowolf on 2008-04-03
I'm trying to find it, but it might be under another place than "System Tools" as I don't see that in the menu options.  Would this Feisty work better for what I am doing and should I try that OS?

Thank you so much.  I am off to bed and will check in on this tomorrow.  Again, thank you all!

---

### Post by kerry_s on 2008-04-03
> **haseowolf said:**
> Right click mount drive, its hda1, so I'm not sure how you mean by how it's formatted.

the drive you want to save to. 
hda1, that would be your drive with xp on it?

the drive your transferring to, needs to be able to be written to, that means it has to be fat or a linux format. if it's ntfs, you'll need those special tools.

---

### Post by cotcot on 2008-04-03
> **haseowolf said:**
> I'm trying to find it, but it might be under another place than "System Tools" as I don't see that in the menu options.  Would this Feisty work better for what I am doing and should I try that OS?

Thank you so much.  I am off to bed and will check in on this tomorrow.  Again, thank you all!

You can start it from terminal ```
ntfs-config
```

---

