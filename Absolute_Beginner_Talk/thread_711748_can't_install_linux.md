---
title: "can't install linux"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by jimmy311 on 2008-03-01
hi. i'm completely new to linux. i partitioned my hard drive and was going to try to install kubuntu. i was going through the installation. when i got to the partion options i chose manual. it then went to the next step where you choose the mounting point. i select the partition i want to use and hit next. it then spits out the error that there is no file structure defined? something like that anyway. i know i'm just missing something simple.. if anyone has any idea of what i'm doing wrong i would appreciate help.

---

### Post by brijith on 2008-03-01
What os do you have in other partition...... ?

---

### Post by jimmy311 on 2008-03-01
its an empty partition i just made it with disk director. i'm using xp right now. and the file system on the partition is ntfs. i assume you have to format it and change the file system? it seemed like the installer for kubuntu could do that, there was a check box for format and you could edit the partition from the installation. but it wouldn't go past that point

---

### Post by yaknowwat on 2008-03-01
when given options choose "use largest continuous free space"
This will use the empty space you want it to use.

---

### Post by jimmy311 on 2008-03-01
ok i'll try that. thanks

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-01
just reformat the partion in ext3 but dont for get about a swap partion
and i would sujest makeing a /home partion as well
just use gparted
system > administration > partion editor
you can figure it out from there

---

### Post by yaknowwat on 2008-03-01
> **<<joe>> said:**
> just reformat the partion in ext3 but dont for get about a swap partion
and i would sujest makeing a /home partion as well
just use gparted
system > administration > partion editor
you can figure it out from there

what i just suggested to him should do that using the empty space and he wont have to worry about it much.

---

### Post by brijith on 2008-03-01
I can suggest you a way out of this. Of course it's my personal opinion.

          First all you boot in to Xp and then right click on the My computer. From the drop down menu select Manage. In the window you can see a section for disc management. Select the partition where you are intended to install Ubuntu and delete it by selecting delete from the drop down option on right clicking it.
 (Be care full while doing this operation. Make sure that you are deleting the the right partition. because once you delete a partition it is difficult to Undo it) Now the deleted partition will appear in green it means it is a free space.

         Now reboot you system and start from Ubuntu CD. When you are asked about  partitioning please  select "[COLOR="Sienna"]use existing free space[/COLOR]" (Again, Be care full what you are selecting, there may have some option to erase entire disk). Once you select the "[COLOR="Sienna"]use existing free space[/COLOR]" option all partitioning will be done automatically.Mount point and swap will allocated accordingly.

         This is how I do Installation of any Linux Distribution.  

         Keep Your eyes open while doing the above mentioned things. A small mistake may led to data lose

---

### Post by jimmy311 on 2008-03-01
i got it to work. thanks for the replies. i didn't want to fool with it too much without some guidance cause i didn't want to delete my windows partition. thanks again

---

