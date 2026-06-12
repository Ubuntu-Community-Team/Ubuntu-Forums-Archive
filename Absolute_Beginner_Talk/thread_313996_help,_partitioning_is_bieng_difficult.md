---
title: "help, partitioning is bieng difficult"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by madhatter434343 on 2006-12-06
I am **very new** to ubuntu, I installed it a couple of nights ago (on my computer that also has windows XP) and I messed around for a couple of hours and then decided that i wanted to play some WoW, so i restarted the computer and loaded up windows but instead of loading how it should, it began my system recovery screen and if i tried to go back to boot my windows account it would just reload the system recovery. so i recovered my computer and it deleted ubuntu(edgy) so i reinstalled it. well the first time i ran through the install(before i did a system recovery) i chose to automatically partition 50% of the hardrive because i did not really know what i was doing. well now that i am attempting to reinstall edgy when i get to the partitioning drives section i am only given the option of eraseing my whole hardrive(which i don't want to do because i want to duel boot) or manually partitioning my hardrive, well i read on another thread that i had to defrag my windows hardrive several times, which i did, but nothing happened when i attempted to reinstall ubuntu. i don't know a whole lot about partitioning drives and the guides i looked at were very complicated, please help and sorry if it seems as if i am nine.

---

### Post by mscclr3 on 2006-12-06
Guessing someone else will have replied by the time I type this but

a.) Don't worry about a lack of knowledge, that's why the forums are here, we all have to start out somewhere.

b.)Partitioning really isn't a big deal... If you click to do a manual partition you should see a list of what partitions are on your drive, I have a feeling that when you did the system recovery it used your whole drive.  If not let us know what the screen looks like after you select manual partition so we can guide you further.

Assuming I've correct that the system restore used your whole drive, you first will have to resize the windows partition (right click on the colored bar and resize it to half the total size if you want to do 50/50)

---

### Post by madhatter434343 on 2006-12-06
it says that i have 3 partitions and 1 extended(with a "Linux swap" under it and 1 unallocated. two of the partitions are 88 and 89 gigs free. so after clicking manually partitionate i should just click next?

---

### Post by mscclr3 on 2006-12-06
No, you have to delete the old linux partitions and make new ones 

You'll need a "/" and a swap (size is debatable for swap), but personally I have a "/" (10 gigs), swap (2 gigs), and a "/home" (60 gigs)

Having a separate home partition allows easier upgrades or reinstalls.

Increase the "/home" as you see fit, that is where you'll store your documents... it sounds like you have alot of room so you may as well use it.

Now that I reread this I realize I never told you how to make the partition
Right click on the unallocated space (the same way that you delete except click new). Specify size and click ok.  Then you should be able to specify what each partition is for (or you may have to click next, I'm blanking on the specifics a bit at the moment)

---

### Post by madhatter434343 on 2006-12-06
how do i know which partitions are linux and which are not?

---

### Post by mscclr3 on 2006-12-06
Your ubuntu partitions will be ext3 (for the /) and linux swap for the swap ... you don't want to touch the ntfs partition... this is listed under filesystem in the partition editor (what filesystem each one is I mean)

You also don't want to touch any kind of fat partition so that's ntfs and fat that we don't touch

---

### Post by madhatter434343 on 2006-12-06
so change the ext3 to ten gigs or so and thats it leave the remaining fat32(5.81 gigs) the three unallocated, ntfs(78gigs), and the extended and linux swap at 1.42 gigs, and the ext at ten gigs and leave it as that?

---

### Post by mscclr3 on 2006-12-06
if you click next, it will tell you if it works or not... if you don't have the correct partitions specified it will say something along those lines.  It sounds right but, without seeing it I can't be 100% sure of it.

---

### Post by madhatter434343 on 2006-12-06
okay, i will try it right now

---

### Post by madhatter434343 on 2006-12-06
the installer froze at the last step...

---

### Post by mscclr3 on 2006-12-06
Can you be more specific about what "last step" is?
I haven't done a straight install in awhile, did upgrades from dapper to edgy and now to feisty so I don't remember for sure.

---

### Post by madhatter434343 on 2006-12-06
The step in which it tells you what you are installing and asks for final verification, shortly after that froze, ubuntu froze altogether and i had to reboot

---

### Post by mscclr3 on 2006-12-06
I would say try it again, or you can try the alternative install cd

Can you list the specs (what hardware you have and that type of thing) of your system to see if anything sticks out to anyone.  

Let me just make sure I communicated what I think you shoudl do with the partitions, delete everything except for fat or ntfs partitions

Next make a / partition of whatever size using ext3
Make a /home partition also using ext3
make a swap partition

I would suggest leaving some space unused, somepeople that dual boot make a fat partition to share documents in between xp and linux, might be something you want to do.  But that isn't a concern for right  now.

---

### Post by madhatter434343 on 2006-12-06
i figured it out perfectly and everything is working great, thank you ALOT for the help i would be ubuntu-less without you heh. now for my next project figure out how to get files from my windows partition(music) over to linux

---

### Post by mscclr3 on 2006-12-06
not a problem, glad I could help

---

