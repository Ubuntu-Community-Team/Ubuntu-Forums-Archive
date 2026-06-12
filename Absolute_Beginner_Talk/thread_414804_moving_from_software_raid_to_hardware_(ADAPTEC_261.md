---
title: "moving from software raid to hardware (ADAPTEC 2610SA)"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by webjames on 2007-04-20
Hi, i have just purchased a ADAPTEC 2610SA raid controller

I have my home directory set up with mdadm software linux raid 5

My question is can i just plug my new raid card in and plug the hard drives in and it will pick up the linux raid5 set?

i'm not worried about Ubuntu accepting the changes, just my data on the raid as i am going to upgrade to feisty and have my raid5 set as my /home directory. (like it was before)

is this possible? if it doesn't work would i then be able to plug them back into the software raid set? how could i tell if it had worked? a live cd?

Thanks for any help, or pointers where i can look,

---

### Post by Nik_Doof on 2007-04-20
No, i dont think it'll work. The Adaptec card will do its own disc management which will be incompatible with lvm.

---

### Post by dan_linder on 2007-10-31
@webjames,

Just wondering how your Adaptec 2610sa worked you for you?  (I am pretty certain that the answer Nik_Doof provided was correct...)

Dan

---

### Post by webjames on 2007-11-01
I have been happy with my card. Performance wasn't really my main reason for getting it, like you i wanted something compatible with both Ubuntu and windows; the 2610sa is. The only thing that md-raid5 has over this card is the ability to expand the array. something which isn't possible from the BIOS on the card, although might be possible with the (windows) software.
i would say that if it wasn't for my x-system compatibility i would stick with mdm software raid.

---

