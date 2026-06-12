---
title: "how to: 'increase' internal memory of android phone under ubuntu"
date: 2013-04-29
forum: Any Other OS
---

### Post by Claus7 on 2013-04-29
Hello,

in this simple guide I will state the steps taken in order to increase the internal memory of my (old) smartphone. This guide might also seem helpful for newer phones as well, since the needs surpass the capabilities even of these new phones. 
In order to accomplish this it is required to have:
[LIST]
[*]an sd card along with 
[*]a program called link2sd &
[*]a card reader
[/LIST]

Now, in order to "increase" the internal memory of the smartphone, this can be done (in general) with 2 different ways:
[LIST]
[*] use the program link2sd, so as to transfer **part** of the application to your sd card, while the rest lies to your internal memory
[*] use the program link2sd, so as to transfer almost in its entirety the application **to a specific partition** in your sd card
[/LIST]

In order for both solutions to work, you should have rooted your mobile phone. Otherwise, the only solution is to use the phone's capability to transfer part of the application to your sd card, which is much less efficient than the solutions proposed here, if not at all.

The first solution proposed here is the easiest of the two. You do not need to partition your sd card, just use it as it is and just choose which applications will be transferred to your sd card. Mind, that some system applications should not be transferred to the sd card, because will make the phone not to work properly (most probably you won't be allowed to do so even if you are root) for both ways. The 2nd solution will increase the amount of available internal memory more than the 1st one. The drawback is that in some cases you might have to re-link some of the applications.

In order to do the 2nd solution you should:
[LIST]
[*]take a backup of your sd card
mount your sd card to the ubu box (using a card reader), make all files and folders visible (even the hidden ones) and just copy them in a folder to your pc -> backup ready
[*]then use gparted in order to re-partition your sd card. Most probably, if everything goes well, you won't need the backup you have created, since, by resizing your sd card, this process won't wipe out your files. In order to open gparted in maverick go to: System->Administration->Gparted Partition Editor
So: 
i) unmount the sd card from gparted 
ii) if no other partitioning of the card has taken place, then select "Resize/Move" to the only partition available (don't mind if there is a minor unallocated space, just ignore it)
iii) resize the sd card's partition by subtracting the size your new partition will take (1GB resize is recommended for the majority of users)
iv) Now, you can crate a new partition, with the free space that was created that way
v) for froyo systems chose ext2 and no swap, for newer systems ext3/4 and 512MB swap might be ideal -*[COLOR="#000080"]REMEMBER[/COLOR]* this step-
vi) the partition type should be primary
vii) no label is needed for the new partition
viii) double check that you are satisfied, until you press the tick button on top, in order to proceed to resizing and creating the new partition
ix) wait a while, until all processed have been completed successfully
x) after the end of the process, just close gparted and remove your card from your computer (it was already unmounted)
[*] now insert back your sd card to your smartphone and open it
[*] start the application link2sd (some messages might appear about the version of the link2sd application, click ok)
[*] for the new partition, link2sd will ask you the type -*[COLOR="#000080"]REMEMBER[/COLOR]* to add the same type you have chosen in step v-
[*] restart phone
[*] chose link2sd again and, chose which applications will be linked to your sd card, following the guide and photos from here: [http://www.aroundandroid.com/tag/how-to-increase-android-phones-internal-memory-with-link2sd-app/](http://www.aroundandroid.com/tag/how-to-increase-android-phones-internal-memory-with-link2sd-app/) (read from under configuring link2sd and on) 
[/LIST]

Comments: 
In some cases it is better to: 1st install the application, then link it to your sd card, and then from the application's menu of your smart phone to transfer them to your sd card! That way you have freed most of the space. The way which will be better will depend on the application and by trial and error. 
This technique increases indirectly the internal memory of your smartphone, by using space from your sd card.

helpful links:
[http://forum.xda-developers.com/showthread.php?t=2125513](http://forum.xda-developers.com/showthread.php?t=2125513)
[http://forum.xda-developers.com/showthread.php?t=557590](http://forum.xda-developers.com/showthread.php?t=557590)
[http://www.roms-au.com/howtos/ext3/](http://www.roms-au.com/howtos/ext3/)
[http://androidcrazyness.blogspot.gr/2012/10/using-gparted-to-prepare-sd-card-for.html](http://androidcrazyness.blogspot.gr/2012/10/using-gparted-to-prepare-sd-card-for.html)

Regards!

---

