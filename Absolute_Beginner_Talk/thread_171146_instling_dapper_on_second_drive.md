---
title: "instling dapper on second drive?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-05-06
i've recetly download the dapper live cd and i want to install it on my second hard drive. 1st drive is 120G sata and second is a 80G sata. my question is when i boot up will i be able to choose which drive to boot from without going into the bios every time?
also, the 80G drive is partitiones from windows. what has to be done there. do i need some fat32 partition for ubuntu or just one full ntfs partition 80G.
also i'm a total noob so is there anythng else i should know before i embark on this new journey???
thanks.

---

### Post by lemmy999 on 2006-05-06
When you install Dapper you will be able to specify where it installs. I would suggest that you format the 80Gb disk first and create some new linux partitions. Try using Partition magic or any similar utility. I'd suggest 5gb for Ubuntu, 1 gb for swap and whatever you like for home. 

The install will allow you to specify what goes on which partition. GRUB will also be installed, that will boot up evry time you boot your computer and will allow you to choose which OS you want.

---

### Post by e1ektrob0y on 2006-05-06
so i can't just install it on one partition like windows. do you mean 1G for linux os, (i don't know what swap is), and the rest for home (whats home?)

---

### Post by e1ektrob0y on 2006-05-06
or alternatively does anyone know of a guide that could help me (not a dual boot one, found that). cheers

---

### Post by joshrobinson on 2006-05-06
[QUOTE=e1ektrob0y]or alternatively does anyone know of a guide that could help me (not a dual boot one, found that). cheers[/QUOTE]

home is where your heart is :p  jk thats where all your personal files are, its like your documents folder in windows

i would do 10gig partition for the ubuntu install which would be ext3 file system
swap is ususaly 2x what you have as ram, but if you only have 256 then 1gig is fine as someone said above, its used as virtual ram, that files are cached to and swaped around

you can do the rest as your home folder, or to make it easier just do 1gig for swap and the rest as the install

---

### Post by e1ektrob0y on 2006-05-06
[QUOTE=joshrobinson]
or to make it easier just do 1gig for swap and the rest as the install[/QUOTE]

i think i'll take the simple route and make it 2gig for swap (i have 1gig of ram) and the rest for everything else. is it all NTFS?

---

### Post by joshrobinson on 2006-05-06
[QUOTE=e1ektrob0y]i think i'll take the simple route and make it 2gig for swap (i have 1gig of ram) and the rest for everything else. is it all NTFS?[/QUOTE]

yeah 2 gig of swap should be fine

and no on the ntfs part, thats a windows filesystem.. linux uses its own types of file systems

just boot the ubuntu cd, and when it gets to the partition editing, select partiton drive manually

look at the parititons on your second hard-drive and it should have a list of them, delete all the paritions off and then select, automatically parition the free space, and it should do all the work for you

just make sure that you are doing this to the correct drive
you dont want to lose everything on the other drive

---

### Post by e1ektrob0y on 2006-05-06
[QUOTE=joshrobinson]yeah 2 gig of swap should be fine

look at the parititons on your second hard-drive and it should have a list of them, delete all the paritions off and then select, automatically parition the free space, and it should do all the work for you
[/QUOTE]
so why would i need partition magic? can i just boot from the live cd, select install and just go from there. partitioning and so on............

---

### Post by joshrobinson on 2006-05-06
[QUOTE=e1ektrob0y]so why would i need partition magic? can i just boot from the live cd, select install and just go from there. partitioning and so on............[/QUOTE]

well do you have parition magic? i mean you dont have to have it or really need it.. but you can use it to delete all of the partitions off the second drive so it is all unformatted and un paritioned

then when you get into ubuntu you can just tell it to automatically parition the free space on that drive

but you can also delete all the parititions off the second drive right from the ubuntu cd

---

### Post by professor_chaos on 2006-05-06
[QUOTE=e1ektrob0y]i think i'll take the simple route and make it 2gig for swap (i have 1gig of ram) and the rest for everything else. is it all NTFS?[/QUOTE]


First off, the live cd is not an installable medium. (someone correct me if I'm wrong here). You need the install cd. Not the live cd.

Second. Partition Magic NOT needed here. During the installation you can choose which drive to partition. You can choose 2gb for swap, but you probably dont need it. If anyone uses swap, they  have pennies in their bank account and cant afford today cheap memory. If any of my processes ever go to swap, I will run to compusa and buy more memory. Anyway, you can choose any amount of swap space and during the installation you will simply choose the drive that you wish to install ubuntu (probably hdb, should show up as 80GB).

---

### Post by e1ektrob0y on 2006-05-06
yeah i have it. i understand now. i have partition magic cause i was going to setup a dual boot but i decided to go with this option cause it seems easier and just better. thanks, i'll give it a go and hopefully i'l be posting back here in a few hours with a success story............cheers

---

### Post by joshrobinson on 2006-05-06
[QUOTE=professor_chaos]First off, the live cd is not an installable medium. (someone correct me if I'm wrong here). You need the install cd. Not the live cd.
[/QUOTE]

when you boot the live cd there is a "install to hard-drive" icon right on the desktop

---

### Post by joshrobinson on 2006-05-06
[QUOTE=e1ektrob0y]yeah i have it. i understand now. i have partition magic cause i was going to setup a dual boot but i decided to go with this option cause it seems easier and just better. thanks, i'll give it a go and hopefully i'l be posting back here in a few hours with a success story............cheers[/QUOTE]

hope everything works out :razz:

---

### Post by e1ektrob0y on 2006-05-06
[QUOTE=professor_chaos]First off, the live cd is not an installable medium. (someone correct me if I'm wrong here). You need the install cd. Not the live cd.
 (probably hdb, should show up as 80GB).[/QUOTE]
i have a cd which i downloaded from this website and when i boot into ubuntu up the top under tools or admin or whatever it is the is a program called install. i think the download comes with the option to install

---

### Post by joshrobinson on 2006-05-06
[QUOTE=e1ektrob0y]i have a cd which i downloaded from this website and when i boot into ubuntu up the top under tools or admin or whatever it is the is a program called install. i think the download comes with the option to install[/QUOTE]

yeah i replied the same thing to him.. the live cd has an installer.. its a gui installer too not text based like the install cd..

he might not of ever used a live cd tho, i never did till recently to test hardware on a laptop

---

### Post by professor_chaos on 2006-05-06
[QUOTE=joshrobinson]when you boot the live cd there is a "install to hard-drive" icon right on the desktop[/QUOTE]

Thank you josh, I never tried that? Why is there a live cd and an install cd?

---

### Post by joshrobinson on 2006-05-06
[QUOTE=professor_chaos]Thank you josh, I never tried that? Why is there a live cd and an install cd?[/QUOTE]

honestly, i have no clue lol
its a gui installer on the live cd, and a text based installer on the install cd.. weird stuff!

maybe the install cd is just for us advanced people with linux and ubuntu, and the live cd is an easier to use version

---

### Post by professor_chaos on 2006-05-06
[QUOTE=joshrobinson]honestly, i have no clue lol
its a gui installer on the live cd, and a text based installer on the install cd.. weird stuff!

maybe the install cd is just for us advanced people with linux and ubuntu, and the live cd is an easier to use version[/QUOTE]

That boggles my mind. 
I guess I will recommed the live cd installer to new users from now on.

---

### Post by e1ektrob0y on 2006-05-06
[QUOTE=joshrobinson]
maybe the install cd is just for us advanced people with linux and ubuntu, and the live cd is an easier to use version[/QUOTE]
thank god for that!!

---

### Post by joshrobinson on 2006-05-06
[QUOTE=e1ektrob0y]thank god for that!![/QUOTE]

well let me and chaos know how the install goes, neither of us have used the live cd to install.. hopefully it goes well

---

### Post by confused57 on 2006-05-06
If possible, I'd try to use the Dapper Beta2 install cd instead of the livecd:

[http://www.ubuntuforums.org/showthread.php?t=170975](http://www.ubuntuforums.org/showthread.php?t=170975)

You might want to browse through the "Dapper Development" section to see what kind of luck people have had installing from the Dapper livecd.  I'm not familiar with SATA drives, but think they'll show up as sda & sdb during the installation process.  During the install, you should have an option of where to install Grub, which should probably be the hd(one with windows?) you have selected in bios to boot to.  I'd definitely do some research, and wait a little for someone to post who might have experience with your situation...unless you're willing to experiment.

Whoops...just read all the replies, guess we'll know in a couple of hours, sorry.

---

### Post by e1ektrob0y on 2006-05-06
ok so where do i install grub? on my linux drive or the windows drive. now i'm confused............

---

### Post by e1ektrob0y on 2006-05-06
well dapper installed succesfully!! *woot* the live cd pretty much did everything for me. it was real easy. i can imagine setting up a dual boot would be harder but...........all i had to do was select which hard drive to install to. too easy! and grub installed by itself and works great.

---

### Post by confused57 on 2006-05-06
Great job, you're definitely more adventurous than I would have been starting out.

---

### Post by joshrobinson on 2006-05-06
thats good that you got it installed, does all of your hardware work fine?

---

### Post by e1ektrob0y on 2006-05-06
seems to all work so far. i installed the latest nvidia drivers (i think) from synaptic but i really don't know what i'm doing yet. all the files look foreign and i'm still thinking in windows mode. trying to find equivalents for windows and stuff. but its all gone off without a hitch so far.

---

