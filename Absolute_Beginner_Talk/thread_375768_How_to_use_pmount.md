---
title: "How to use pmount ???"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-03-04
My usb hdd does no longer automounts at startup as it has always done before. There are no entries in my /etc/pmount.allow file which seems to be the problem.
However, I would appreciate some advice on what exactly do I need t enter here.
Also, anything else I need to do to get this drive to automount?
Thanks
Paul

---

### Post by jvc26 on 2007-03-04
[http://doc.gwos.org/index.php/Understanding_fstab#pmount](http://doc.gwos.org/index.php/Understanding_fstab#pmount) May well help.
Il

---

### Post by PaulFXH on 2007-03-04
Thanks Illuvator
Yes, it did help but it didn't resolve my problem.
I put the three devices that I want to automount into /etc/pmount.allow (ie. /dev/sdax where x =1, 5 or 7) but none of these automounted on reboot.
However, using 
```
pmount /dev/sda1
```
works fine.

So, I'm still puzzled, perplexed and generally confustigated on this one.
In particular, I have these questions:

1) Why does the "other" partition (ext3) on the usb drive invariably mount at startup even though it is not mentioned in either /etc/fstab or /etc/pmount.allow ??

2) What do I need to do to get the three ntfs partitions to automount at startup ??

Thanks for any help
Paul

---

### Post by Drakkor on 2007-03-04
Don't know if this will help, Paul , but I have 3 ntfs partitions automounted with read/write capabilites, did this awhile ago though. Here's my fstab and drive structures. :)
Here's a link for the fuse read/write dealie:  [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)    I  think it's supposed to be experimental, but I haven't had any problems with it !

---

### Post by PaulFXH on 2007-03-04
Thanks for the suggestion, Drakkor but I had actually tried that very thing just yesterday without success (the only difference being that I changed the locale from US to IE because of where I am). I'm not sure if the fact that it works for you but not for me is related to my partitions being all on removable media.

Nevertheless, I don't believe I should need to resort to new, experimental procedures to get back to where I was as this automount has worked for me for about 9 months without problems.

Also, hotplugging cannot be reliant on something in /etc/fstab. Indeed, just today I plugged in the "problematic" usb drive into our other computer which does not, and never had any external drives and the new usb drive was mounted immediately without anything showing up in /etc/fstab.

Best wishes
Paul

---

### Post by PaulFXH on 2007-03-04
Well, I finally got this solved by using this [article]("http://https://help.ubuntu.com/community/AutomaticallyMountPartitions").
I used the first method which involves downloading a small script and running it just once. Thereafter all ntfs partitions are mounted at bootup and icons appear on the desktop.
Furthermore, I can once again eject ALL partitions on the external drive (3*ntfs, 1*ext-3) just by ejecting any one of the four icons.
Note that the script refused to install first time around as it complained of me already having lines relevant to the partitions concerned in /etc/fstab. While this is true, they were all commented out. Strange.
So, things are back where they were. What I can't understand is why I never had to run this script before and yet all (including ntfs partitions) volumes always mounted at boot time..
Even our new computer, to which I just hooked up an external drive for the first time today, mounted the partitions without batting an eyelid.

---

### Post by Drakkor on 2007-03-04
LOL :)  Cool , glad it worked out , it usually does after some work,lol :)

---

### Post by OzzyFrank on 2008-03-17
The article link above is wrong, so here is the proper one:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Cheers

---

