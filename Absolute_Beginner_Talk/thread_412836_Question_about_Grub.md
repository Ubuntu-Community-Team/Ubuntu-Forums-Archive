---
title: "Question about Grub"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-04-18
I've read up on the GRUB boot loader and I have a few questions about it. I've been using an NT GUI based boot loader for about a month and a half since I have been a windows user for more than 15 years and just started dual booting. I am however getting annoyed by it, it takes more than 45 seconds to boot into it just to select my os, so tommorow when I get my copy of Feisty I'm planning on repartitioning my drives and at the same time installing GRUB to my MBR. 

1) I would like to know however, is there a way to make GRUB wait more than two seconds before automatically booting into Linux? 

2) On the same vein of thought is there a way to make GRUB automatically boot into the selector and wait?

Hope someone can help, thanks in advance. :)

---

### Post by sargeras on 2007-04-18
If you edit the file "/boot/grub/menu.lst" you can change the timout.  Mine is on line 19 so check around there.  

Regards

---

### Post by BoneKracker on 2007-04-18
Yes and yes.

You can have it wait for any predefined period of time before booting the default.  You can also have it just wait and not boot any default.

I know the documentation is painfully dispersed and difficult to comprehend.  Be comforted to know that:
[LIST]
[*]the default installer will set up grub for you
[*]if you tell it to "add other operating systems" it detects, it will add an entry for Windows (which will chainload the nt bootloader).
[*]there is a script from debian included that will be automatically set up to automatically keep the bootloader configuration updated
[*]you will easily be able to fine-tune the delay by editing a single number in a single file (/boot/grub/menu.lst)
[*]you can password-protect selected bootloader menu options with an encrypted password
[/LIST]

There are lots of posts in these forums about GRUB.

---

### Post by Patrick K on 2007-04-18
Here is some info I found help.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by earobinson on 2007-04-18
> **sargeras said:**
> If you edit the file "/boot/grub/menu.lst" you can change the timout.  Mine is on line 19 so check around there.  

Regards
This should do it!

---

### Post by starcraft.man on 2007-04-18
Thanks, that's all very helpful. I just glanced over your link Patrick and that was very helpful (and bookmarked) thanks all. Someone should sticky that GRUB page from patrick for future reference... might save people from creating future threads.

---

