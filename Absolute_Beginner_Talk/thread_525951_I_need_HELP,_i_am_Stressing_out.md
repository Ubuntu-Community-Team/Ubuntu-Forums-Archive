---
title: "I need HELP, i am Stressing out"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zibeezibeehey on 2007-08-14
ok ive been on here all night trying to get answers and i think i finally messed things up. Ive wanted to move all of my files to my external hard drive. My window XP is corrupted and wont load so ive used ubuntu live cd for the past week. Now when i try to use the live cd to move my files to the external hard drive it wont work.

Ive been given lots of help that hasnt really gone anywhere. It just wont work. So what i wanted to do was to put ubuntu on my internal harddrve and then move the files over because it doesnt seem to work from the live cd for some reason.

Now I went into Gparted and some how i think i made my internal hard drive turn into an unallocated drive. Does this mean my drive is toast now, that it no longer has all my files on it or what. How can I bring it back to normal. It used to be a 40gig split into 2 with one being my files i want and the other being windows XP. PLEASE PLEASE PLEASE help, i am freaking out.

---

### Post by mikewhatever on 2007-08-14
If the partitions you had are  deleted, you probably can't get them back. Have you formatted them? Which guide have you used to install if any?

---

### Post by zibeezibeehey on 2007-08-14
I havent actually formatted anything yet al i accidently did was make my hard drives turn unallocated. Anyway of putting it back to the way it was?

---

### Post by amazingtaters on 2007-08-14
Ok so, uh, your partition went from being ntfs to unallocated? What did you do to make it that way (eg delete partition, try to change format, etc.)

Edit: If you've got GParted running, try hitting the undo button.

---

### Post by zibeezibeehey on 2007-08-14
no can do on the undo button i think what i accidently did was give it an msdos Disklabel and now it says unallocated 37.31GB thats it. See I was wondering if i can get it back because it couldnt have messed my whole hard drive up in a matter of seconds. Because I clicked the button then like 4 seconds later it said unallocated now it wants me to create new partition and format. What do I do to get my files back?

---

### Post by amazingtaters on 2007-08-14
If you haven't clicked apply you should be ok, because nothing you've done has been applied to the drive. If you have, well...

---

### Post by zibeezibeehey on 2007-08-14
well it already says unallocated and the only choice of button i have is NEW at the top. When I shut down and then put it a version of SLAX live cd it also doesnt show my hard drive because its unallocated but can i allocate it again without losing my files?

---

