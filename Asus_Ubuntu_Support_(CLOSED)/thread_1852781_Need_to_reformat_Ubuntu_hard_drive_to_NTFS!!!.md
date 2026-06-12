---
title: "Need to reformat Ubuntu hard drive to NTFS!!!"
date: 2011-09-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dragonart18 on 2011-09-30
I just bought a Asus EEE Box 107 and am new to ubuntu, it does not have partitions so the whole hard drive is dedicated to Ububtu. How can I reformat the hard drive to NTFS? 
thanks. 

p.s. the eee box doesn't have a optical drive so i used the live boot for the newest ubuntu OS.

---

### Post by papibe on 2011-09-30
Welcome to the forums!

Have you installed Ubuntu on the machine already? If so, you can't format the drive while using the system. You would need to use Ubuntu Live, and then you can use 'Disk Utilities' to flat format the disk, or Gparted to create partitions and format them.

BTW, although Ubuntu can use NTFS, it can't be installed on an NTFS partition. May I ask why do you want to format the hard drive to ntfs?

Regards.

---

### Post by dragonart18 on 2011-09-30
Thanks, I already have the Unbutu installed, but I can't run a program (PPS streaming?)
on it, I plan to use this small pc for media only. I installed the Ubuntu using the usb as the pc had no optical drive...so i did use ubuntu live, but now i want to use windows 7. sorry, ubuntu didn't work out for me. Now the problem is reformating the drive to NTFS so windows can recognize it. Any help?

---

### Post by papibe on 2011-09-30
A little more specific than my previous post:
[LIST]
[*]Boot into the installation Ubuntu USB that you made for installing Ubuntu.
[*]Instead of installing, go Live by choosing the 'Try Ubuntu' option.
[*]Once you are inside the desktop, go to 'Disk Utilities'.
[*]Select your hard drive on the left.
[*]One of the options in the right will be 'Format Drive'.
[/LIST]
I hope it's a little clear now,
Regards.

---

### Post by dragonart18 on 2011-09-30
thanks, I'm up to the last step but the format options are "master boot record", guid partition table" ,"don't partition" and "apple partition app". Which one should i choose if i want to get rid of ubuntu for windows? thanks again for the help ^_^


EDIT: i found NTFS in Format Volume, is that where i go?

---

### Post by papibe on 2011-10-01
"master boot record" should work.

Regards.

---

### Post by dragonart18 on 2011-10-01
so in that does it auto format the drive to NTFS? what about the volume where i see NTFS?

---

### Post by papibe on 2011-10-01
Format to ntfs would be my first option though.

---

### Post by dragonart18 on 2011-10-01
thank you so much! you have been a great help! sadly Ubuntu didn't work out for me in the end it's nice to know i have other options, who knows i might give Ubuntu another try in the future! Take care and once again, thanks! ):P

---

### Post by kurt18947 on 2011-10-01
It's quite possible to run more than one operating system on a machine. Ubuntu is going through some relatively rapid changes right now so someone unfamiliar might well have a bumpy ride. There are other desktop environments if that was an issue for you. KDE, Xubuntu and Lubuntu are all quite usable.

---

### Post by jackyboy633 on 2011-10-02
If you're using a nettop for general browsing and email, Jolicloud will be good for you.

---

