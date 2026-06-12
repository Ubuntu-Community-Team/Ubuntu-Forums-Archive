---
title: "can't boot back to window"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-28
it say ntldr is missing press 
ctrl+alt+del to restart restart a lot of time not working
it used to be able to boot into window xp until like 15 min ago
try restarting a lot times still no goal don't work to delete and reinstall window xp and linux 
because i am using linux to download some stuff in the window drive 
i can still accress to window drive in linux and keep the download

---

### Post by Trebaruna on 2007-07-28
What you might consider is using the windows CD and press some key or other when it boots (I cannot remember) to get into the "Recovery Console" which is a command line environment where you can administer certain treatments to your windows install.

Type 'fixboot', enter, 'fixmbr', enter. (no quotes in actual commands).
This should get you windows. Yay!
The only thing left now is to reinstall the GRUB mbr, and for that you can find a howto [here]("http://www.sorgonet.com/linux/grubrestore/").

That should get you back on the road, I hope.

---

### Post by zerobinary on 2007-07-28
ok my plan is finish my download first 
then burn it with gnomebaker not sure will it work 
and burn it with thoggen(convert the video ogm to dvd)
not sure thoggen can burn ogm video into dvd i mean video dvd suggestion plz

---

### Post by zerobinary on 2007-07-29
help plz the thing in window patition just black out 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-7.png[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-14.png[/IMG]

---

### Post by zerobinary on 2007-07-29
thoggen can't even sense the empty dvd

---

### Post by zerobinary on 2007-07-29
is there any burning ogm tools i need to burn ogm in linux 
i have ogm rip but didn't seems to recognize the window files

---

### Post by armandh on 2007-07-29
here is a lot of info
[http://technet.microsoft.com/en-us/windowsvista/aa905126.aspx](http://technet.microsoft.com/en-us/windowsvista/aa905126.aspx)


of course be fore starting any thing like this you backed up all those important files....right?

I have had no end of problems getting the boot loader out of the Hdd
having a partitioning program running on a spare computer did not get it all
finaly putting the Hdd as master on the primary ide  line and booting a 98 start up disk from the floppy
at the A prompt type  fdisk /mbr
finally the 0 sector got cleaned [I think] and I could reload whatever

---

### Post by zerobinary on 2007-07-29
the problem is i can't back up right now 
still downloading files into it wit h linux torrent a 10gb ones and is almost there

---

### Post by zerobinary on 2007-07-30
plz help

---

