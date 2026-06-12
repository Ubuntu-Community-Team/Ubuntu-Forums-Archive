---
title: "Switching from XP - driver and program related question"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Rosette on 2005-12-10
Hi! i downloaded and tried the Live CD of Ubuntu (latest version) and loved it, so I'm switching over from XP Pro. I have an ATi X800PE graphics card... are there drivers availiable for this card under Linux? (the OS recognised all my other hardware perfectly). Another question, my storage hard drives are formatted under Windows NTFS format... will I need to alter this? I can't seem to access the drives in Linux, even though it knows they're there. I assumed that is to do with the NTFS format. Final question: Will I be able to play World of Warcraft in Ubuntu through an emulation program or somesuch? Help in this area would be helpful... if I can't play WoW under it then I probably won't switch.

Thanks for your time.

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=Rosette]Hi! i downloaded and tried the Live CD of Ubuntu (latest version) and loved it, so I'm switching over from XP Pro. I have an ATi X800PE graphics card... are there drivers availiable for this card under Linux? (the OS recognised all my other hardware perfectly). Another question, my storage hard drives are formatted under Windows NTFS format... will I need to alter this? I can't seem to access the drives in Linux, even though it knows they're there. I assumed that is to do with the NTFS format. Final question: Will I be able to play World of Warcraft in Ubuntu through an emulation program or somesuch? Help in this area would be helpful... if I can't play WoW under it then I probably won't switch.

Thanks for your time.[/QUOTE]

It is only possible to read from NTFS from Ubuntu.  If you want to save data there as well, you will need a different type of partition.  Many people who dual boot use FAT32 since both Windows and Ubuntu can read/write it.  If you aren't dual booting, it is better to just set up some ext3 partitions.

---

### Post by rickmans on 2005-12-10
For playing Wow you could use wine. It will take some time probaly but it can work ;).

---

### Post by Rackerz on 2005-12-10
[QUOTE=Rosette]Hi! i downloaded and tried the Live CD of Ubuntu (latest version) and loved it, so I'm switching over from XP Pro. I have an ATi X800PE graphics card... are there drivers availiable for this card under Linux? (the OS recognised all my other hardware perfectly). Another question, my storage hard drives are formatted under Windows NTFS format... will I need to alter this? I can't seem to access the drives in Linux, even though it knows they're there. I assumed that is to do with the NTFS format. Final question: Will I be able to play World of Warcraft in Ubuntu through an emulation program or somesuch? Help in this area would be helpful... if I can't play WoW under it then I probably won't switch.

Thanks for your time.[/QUOTE]

•There are drivers avaliable, but you shouldn't need them as they come pre-installed. 
• Linux can read NTFS drives but it cannot write to them (yet). So you can take files off your NTFS drives but you can't put files on them. 
• The reason you can't access the drives is because of a setting in /etc/fstab/ which can be fixed easily after installing. After that you can access the drive with no troubles at all. 
• Yes you can play WoW using Wine (i think) there's a tutorial in the Ubuntu Gaming section. It works very well from what i've heard.

Hope i've helped!

---

### Post by Rosette on 2005-12-10
Thanks for the quick replies :)

"•There are drivers avaliable, but you shouldn't need them as they come pre-installed."

I'm having trouble with my screen resolution, I can't get it higher than 1024x768, even though my monitor supports higher resolutions. Is that a graphics card issue? That was my initial assumption, but if it is installing drivers anyway then maybe it's another issue. 

 "• The reason you can't access the drives is because of a setting in /etc/fstab/ which can be fixed easily after installing. After that you can access the drive with no troubles at all."

Okay, something to poke around with then, as long as I know I can get to my por-....uhh coursework ;) 

"• Yes you can play WoW using Wine (i think) there's a tutorial in the Ubuntu Gaming section. It works very well from what i've heard."

Awesome. That's me converted then. I'll have a look at the tutorial.

---

