---
title: "Delete partitions"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by airportlounge on 2008-01-22
My question is pretty simple, I'm sure, to the computer savvy linux user, but to a noob like me, I have been plagued with confusing vague instructions to delete partitions. This is my situation: I have messed around and effectively created a slew of useless partitions and though I managed to successfully dual boot xp and ubuntu, I can not help but wonder how I've messed up my HD. So simply put, I want to start over. I want to remove all partitions, fix the mbr (if thats needed), and install xp first this time (I heard its easier this way). I have whats calle an AISA drive that came prepartitioned with my lappy though so I don't know if I should delete this? In any event, is there anyone that can tell me how to merge all these partitions into one congruent ntfs drive so I can start from scratch and only have two partitions and not, say, 5? Any instruction will be greatly appreciated.

Cheers

---

### Post by skymera on 2008-01-22
so want to reformat drive, install windows, then reinstall ubuntu?
or keep ubuntu anf just reinstall windows?

---

### Post by airportlounge on 2008-01-22
I would like to completely wipe my drive of all partitions (I have backed up everything) and just have one big ntfs drive. From there I know what to do as far as resizing the partition through the gnome partition editor in the installation disc. Thanks for the prompt response!

What I mean is I would like to remove all logical, extended, swap and primary drives  ntfs and ext3, and revert my computer back to the ntfs drive it used to be...as well I have no idea what an aisa drive is, could anyone clarify that?

---

### Post by skymera on 2008-01-22
well i would boot the live CD and use Gparted from there.

in gparted you can delete partitions and reformat to NTFS for example.

or leave unformatted and do it all when installing XP.

anyway hope i helped i have to leave now.
Good luck

---

### Post by airportlounge on 2008-01-22
Thanks man, I was hoping to avoid gparted because it is sooooo slow but I think thats my only option. I should mention I do have Acronis disk director and an xp partition...would this be good? Skymera, a thanks is in order:) I understand if you have to leave. Can someone fill his spot and give me a hand? Will acronis work? Any ideas? ANYTHING that doesn't require gparted...:p

---

### Post by airportlounge on 2008-01-22
b to the u to the m to the p

---

### Post by housam on 2008-01-22
Use the Gparted tool on your live CD to rearrange your HD. You've to create at least 3 partitions : 
ntfs for win-xp
ext3 for ubuntu root ( / )
swap for ubuntu 1 GB

install win-xp first and then ubuntu , it will be easy that way.

---

### Post by airportlounge on 2008-01-22
Ah,ok thanks housam...I guess gparted is unavoidable :p will do, now if I can just back everything up...Take it easy folks and thanks for your help.

---

