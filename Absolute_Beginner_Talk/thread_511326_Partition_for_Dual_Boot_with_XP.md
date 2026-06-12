---
title: "Partition for Dual Boot with XP"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Sk1ppy on 2007-07-27
I'm in Ubuntu now and I clicked the install icon. Now I'm on Step 4 of 7 which is to partition my  disc. I have 3 Choices:

Guided - use entire disk (and under it it has the choice: SCISI3 (0,0,0) (sda) - 80.0 GB ATA (A bunch of letters and numbers))

Guided - Use the largest continuous free space

Manual 

Which should I choose for a dual boot?

---

### Post by marco123 on 2007-07-27
The second one, "Use largest continuous free space."

---

### Post by Sk1ppy on 2007-07-27
It says the free space is too small it be automatically partitioned. :(

---

### Post by davidjmayo on 2007-07-27
[COLOR="Red"]DO NOT SELECT THE OPTION[/COLOR] "use entire disk" as this will overwrite=wipe out your windows

Hope this isn't too late

Can you give details of you HD. How much space does windows currently use?

---

### Post by Sk1ppy on 2007-07-27
When I do manual this is what it shows.

[IMG]http://img.photobucket.com/albums/v423/Dragonslash102/Screenshot-1.png[/IMG]

---

### Post by davidjmayo on 2007-07-27
sorry you have to stop here for now

ubuntu likes 10GB +1Gb more swap =11Gb for the install (example my install takes up 3Gb without data)
You need to go back to windows and move some stuff around to make space. you only have 8MB free..no where near enough.
 Be careful, what are the fat partitions? one is probably  a recovery partition for your windows unless you have a windows cd. DO NOT MESS WITH THEM IF YOU DON'T KNOW WHAT THEY ARE

your ntfs partition will need to be made smaller to make room for ubuntu.
after you make space post back and get some advice on how to continue unless you know how to partition


Take your time. There is no need to rush into ubuntu and regret things later.  Another day or two won't make any difference.

EDIT if you are going to partition BACK UP you data first

---

### Post by Sk1ppy on 2007-07-27
I'm not entirely sure how to make the ntfs partition smaller...

---

### Post by AceofSpades19 on 2007-07-27
open up gparted and drag the ntfs parition to make it smaller

---

### Post by Sk1ppy on 2007-07-28
Alright so I finally got my ntfs partition smaller so i have about 17.5 gigs of free space. I chose the second choice when it asked for how i want to partition (Largest continuous free space). Now, before I click the install it says its going to format Partitions #5 and #6. Is this what it should say?

---

### Post by Sk1ppy on 2007-07-28
Bump, Because I'm so close...

---

### Post by exoace on 2007-07-28
hey guys, i'm tryign this out for the 1st time myself. and i'm in a similar situation. where i have 45gb free (tried installing XP, cause my old ubuntu cd wasn't working; so got 7.04 and now its loaded and in the install screen :)
but i selected:

"use largest continuous free space" and now step 7 of 7 it says:
"the following partitions are going to be formatted:
 partition #3 of IDE1 master (hda) as ext3
 partition #7 of IDE1 master (hda) as swap "

and i'm concerned cause my master hardrive has 3 partitions... the other 2 i need,
but the 1st one (45gb) is totally free and set aside for an O.S ... i also have a secondary HD of 80GB.
i just don't want it to touch anything in the other partitions... i don't care if the 45gb section gets wiped.

so when it says "partition #3 or #7... is that just a "name" assigned to my primary 45gb partition? 

thanks for any help 

- i didnt' want to start a new thread cause this one seems to also pertain to my situation :p

---

### Post by Nevis on 2007-07-28
It's hard to say 'yes' or 'no' since no-one here knows what partitions your Windows drives are. However, have you read this page?
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

If you can't determine your Windows partitions after reading htis post again and maybe someone can help sort it out. Good luck, it's worth the change!

---

