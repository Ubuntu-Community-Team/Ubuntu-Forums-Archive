---
title: "very irritated grub error"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-10-14
ok so i have a desktop and i have three partitions one for xp one for vista and one for linux. I try to go install my linux and i get an error at the very end it says "executing 'grub-install(hd1' Failed" this is a fatal error. I originally got it with hd0 and then thought change it to one maybe it fix it but no. So wut should i do i really want this linux to work

---

### Post by jaygo on 2007-10-14
> **metzy85 said:**
> ok so i have a desktop and i have three[*]Test your hard drives. I'd recommend using any utilities provided by the manufacturer or just use Seagate's Sea Tools, which works with any brand. Run the long tests and see if it finds any defects. Replace drives as necessary. Try installing Linux again.
 partitions one for xp one for vista and one for linux. I try to go install my linux and i get an error at the very end it says "executing 'grub-install(hd1' Failed" this is a fatal error.

I had the same error during installation yesterday. In my case, it was due to bad hardware. In your case, it could be a number of things. I would try the following, in order, until you get it to install correctly:
[LIST=1]
[*]Boot into XP & run chkdsk. Format the linux partition. Try installing Linux again.
[*]Test your RAM. Test only one stick at a time, boot from the liveCD & run memtest for at least 12 hours. If there are *any* errors on any sticks, then replace or remove the bad ram. Try installing Linux again.
[/LIST]

If those don't work, post here again and we'll see what we can do.

---

### Post by thelocust on 2007-10-14
How do you have your partitions set up? Also get the Super GRUB disk and try to install it that way.

---

### Post by metzy85 on 2007-10-14
Ok so i reformated the hard drive and windows like 2 hours before install linux so like pretty sure there are no errors. As for my partitions i have two hard drives both 80 gb (no raid just stock hard drives on WD and other MAxtor) on i jsut have my games and stuff on and the other i run my os off of. The primary one (which has the os's) Is 80gb i have two 34gb partitions and one 14gb. The rwi 34gb ones have xp and vista home premuim. The other 14gb ons i want to have linux on it. 

Where do i get a super grub disk. Wut exactly is the difference.

---

### Post by metzy85 on 2007-10-14
well i go it to work all i had todo was change the format from ext 3 to ext 2 format. now there is a new issue.  I have an error 11 unrecognized device string. when i go to the os choise for xp. then if i select vista i get os choice menu with xp and choose that one and i can get to xp. SO how can i get to xp on the first os choice menu

---

### Post by jaygo on 2007-10-15
I believe you want to edit the menu.lst file. It's the list that GRUB uses to boot from.

[Read about it here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu") ... scroll up & down for more about grub. Let us know how it works out.

By the way, when you installed ubuntu from the CD, did you choose to partition the drive manually or guided?

---

### Post by metzy85 on 2007-10-15
manually because i installed it last which was bad planning should have done it first would have been much easier

---

### Post by jaygo on 2007-10-16
maybe ... I've heard that vista is even more picky than xp as far as wanting to be the first OS on the drive.

I just picked up on something. It sounds like you're first choosing Vista from the GRUB boot menu, then it's taking you to a Vista boot manager which lets you choose between vista & XP. Is that correct?

---

### Post by metzy85 on 2007-10-16
exactly i see a first boot menu with the linux and vista and the other operating system chaioce i choose that i get a string 17 error. But if i choose vista takes me to its boot loader.

---

### Post by jaygo on 2007-10-18
> **metzy85 said:**
> exactly i see a first boot menu with the linux and vista and the other operating system chaioce i choose that i get a string 17 error. But if i choose vista takes me to its boot loader.

So when you choose the ubuntu option you're getting a string 17 error. I'm not much of a GRUB expert so I'd suggest searching the forums for threads about GRUB & Vista.

GL

---

### Post by metzy85 on 2007-10-20
ok thanks man for ur help

---

