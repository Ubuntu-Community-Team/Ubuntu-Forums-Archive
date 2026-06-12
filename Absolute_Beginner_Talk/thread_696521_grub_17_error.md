---
title: "grub 17 error"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by montyfunk on 2008-02-14
Bit of a problem, i am getting this grub 17 error after it loads grub 1.5- i deleted a partition so i could use it for xp as i need more space than i allocated for games. I tried extending the first partition so the end point was at least the same.
i cant load up either xp or ubuntu. I can use the xp recovery but dont know what to do from there. i can use the ubuntu cd to load the os but also dont know what to do from there.
so it was
partition 1 - xp, part 2, part 3- ubuntu, part 4- swap, part 5 then unpartitioned space
now it is
partition 1 - xp, part 2- ubuntu, part 3- swap, part 4 then unpartitioned space
I tried some kind of terminal thing where i said where the grub file it said in hd(0,2) so i went into a grub thing and said find the grub in hd(0,2)

I also tried going from the xp recovery console but i dont have a scoobie how to work that.

I have been using ubuntu for years but the reason i have is because it just worked so i dont actually know how to do stuff on it.

Its all fairly new so I wouldnt mind reinstalling ubuntu but xp as always is a ballache to set up so i dont want to reinstall that.

---

### Post by oedha on 2008-02-14
mmm....how bout restore the GRUB
or...
first...boot with xp cd...then choose recovery mode....type 1 then type adm password...after that fixmbr and then fixboot
reboot
check is your windows ok....
if yes...you have to restore your grub......you can search about it here...:)

---

### Post by oedha on 2008-02-14
and here is for GRUB....
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)
:)

---

### Post by StGeorge on 2008-02-14
See
[http://ubuntuforums.org/showthread.php?t=24113&page=17](http://ubuntuforums.org/showthread.php?t=24113&page=17)
You will want to call it (hd0,3).
A second hard drive is called hd1.
If your ubuntu is at the beginning of the drive it is called (hd1,1).
Re install and look for the advanced tab right at the end.
__________________

---

### Post by antoz on 2008-02-14
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

If you need to reinstall grub the above link offers good info, there is a lot to read but Hermann's instructions work if followed properly, Hope this helps, A

---

