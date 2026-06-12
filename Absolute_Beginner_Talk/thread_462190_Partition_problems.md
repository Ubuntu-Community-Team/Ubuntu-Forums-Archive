---
title: "Partition problems"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by toontastic on 2007-06-02
After letting Ubuntu taking over the install itself it seems to have made a bit of a mess of my partitons, I've attached an image to show you.

is there a way to extend sda4 into the unallocated space as I keep running out of space.

Thanks.

---

### Post by locke.dragon on 2007-06-02
i'm guessing that the huge partition is for a windows install right?  and if so, is it full?  or empty?  i can't tell from the screenie.

---

### Post by toontastic on 2007-06-02
yep the huge one is a windows one, the unallocated one was a Ubuntu install which went wrong, I thought I had copied over it with this install but I hadn't which means it's now unallocated and my install has only 120mb left which isn't good :)

---

### Post by toontastic on 2007-06-02
I'm also not sure why I have two linux-swap partitions

---

### Post by locke.dragon on 2007-06-02
could you boot into windows, defragment your hard drive, and then post another gparted screenshot?  the current screenshot shows an error in the ntfs partition.  and just in case it's not clear, unallocated means blank.  there's nothing there.  and while your at it, download a copy of the gparted live cd.  you're gonna need it in a bit.  here's a link.  just download and burn it like you did for the ubuntu live cd.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by toontastic on 2007-06-03
I know it's blank I made it blank :) It did have a previous install of Ubuntu that went wrong I just deleted it after I installed the new one. All I really want to do is expand my current install of Ubuntu (which is about 2gb) and make it the full 20gb. I might jut reinstall though if it's easier.

---

### Post by toontastic on 2007-06-03
Here is the screenshot without the Windows error. Looking at it I can't do anything with /dec/sda3, 5 and 6 so I guess I can't just delete them all and start again can I ?

---

### Post by ca.kushagra on 2007-06-03
why dont you take a back up of your data and then mess with the hard disk. Also please do try reloading window and then create partitions again while installing windows...Create not more than  3 partitions from windows. When you use gparted create a swap partition also so that u are able to install ubuntu fast.

---

### Post by locke.dragon on 2007-06-03
ok.  here's what you do.  shrink the windows partition to about where i marked on my version of the screenshot.  then delete the three that i circled.  if you can't do it in the ubuntu live cd, you'll have to use the gparted live cd (same thing minus the ubuntu environment.  don't be scared by all the numbers and stuff that flash on the screen at first, just wait until the text stops scrolling and answer the question it asks, and withing minutes youll have a simple GUI running with gparted ready to go.)

once you delete and shrink the partitions successfully, go back into the ubuntu live cd and his install in largest contiguous space and just let it do it's thing.  that should install without problems.  :)  let me know if there's anything else you need.  ;)

[IMG]http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-5.png[/IMG]

---

### Post by locke.dragon on 2007-06-03
don't listen to ca.kushagra.  he's trying to get you to do it the hard way.

---

### Post by toontastic on 2007-06-03
That was a heck of a lot quicker than I thought it would be. All done and Linux is on a nice big partition now. Once I'm happy with it I may even dump Windows completely. Thanks for the help.

---

### Post by locke.dragon on 2007-06-03
glad i could help!  :D

---

