---
title: "how do I set a devices drive letter so it won't change?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-26
Hi, is there a way to set the drive letter like in windows? Like if my external appears to be conflicting and changing drive letters, can I set it from sde to sdg or something higher?

---

### Post by aktiwers on 2008-03-26
Im not sure on this, but maybe pysdm can do this for you?
```
sudo apt-get install pysdm
``````
sudo pysdm
```

Edit: Or wouldn't creating a new mountpoint also do it? Just create a folder inside /media/ called the name you like and change fstab mount point to that folder.
But I guess the tool above does what you want too.

---

### Post by iansane on 2008-03-26
hmmm... buggy. It's calling my sda sdb and has another seperate listing for sdb. Not sure I want to use it if it's buggy. I'm already nervous cause I'm using 8.04 server AMD64  with desktop installed. Don't want to push my luck till I see if I can find some more apps or solutions for this but thanks :-)

---

### Post by nick_h on 2008-03-26
Linux doesn't use drive letters in the same way as Windows does.  Most users should just be concerned with where a filesystem is mounted and not what it is referred to in the /dev hierarchy.

I suggest that you don't worry about the device letter.  In the /etc/fstab file the filesystems can be referenced by there UUID or LABEL.  In this way if the letter changes then it will not matter.

---

### Post by iansane on 2008-03-27
well it matters if it is mounting differently everytime and you have a program set to look for it in a certain place. This is actually for someone else and I told them to make an fstab entry that stops it from automounting. This is a lot of hassel to have to open a terminal and type in the mount commands but it works if you need to have control over where it mounts. I know it doesn't handle letters the same. It used dev and 3 letters instead of one but there should be a way to set which 3rd letter is assigned.

---

### Post by iansane on 2008-03-27
why do people who don't know the answer always come back with something like that. "most users should or should not be concerned with something". Just cause were noobs doesn't mean we couldn't benifit from knowing how things work.

---

### Post by LeoSolaris on 2008-03-27
I think this may be something Linux, or at least Ubuntu does, random assigning of drive locations for hot swapped drives. It hasn't actually mattered to me yet, since I am one of those typical users that nick spoke of, but it always did make me a little curious.

Just out of curiosity, what program are you running that needs the drive to be put in the same location and name?

I am planning on building my first home server, and while I doubt I will need hot swapping USB drives, it may happen, and I may need that program...   maybe.

Leo

---

### Post by iansane on 2008-03-27
Actually I was asking because someone else was having trouble with a usb removeable and some music program that looked to the drive for the music library. He said everytime he had to copy all of the music to the right folder and delete the wrong folder. I didn't really understand his problem but it seems like a legitimate question to me. 

Sorry if I sounded like a jerk Nick. I just get frustrated and I know there's got to be a way. I'll either get it figured out or someone will tell me, or I'll forget about it till it comes up in some other issue.

---

### Post by smartboyathome on 2008-03-27
See [here]("https://help.ubuntu.com/community/RenameUSBDrive"). Should work with hard drives too. :)

---

### Post by iansane on 2008-03-27
Great! thanks smartyboyathome. I think this is exactly what the other guy needs. I also found this.

[http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/](http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/)

which is a little more complex looking but tells different ways to label it by its serial number. 

It may be more complex but in essence, this is like changing the drive letter. I just didn't ask the right question

Thanks again

---

### Post by nick_h on 2008-03-27
> Just cause were noobs doesn't mean we couldn't benifit from knowing how things work.
I agree, it is interesting and sometimes useful to know how things work.

What I was trying to say was that even experienced users mainly work from a mount point for day-to-day work.  The /dev hierarachy is more used for system administration tasks.

smartboyathome's post suggests using the volume LABEL as I suggested.  Even in the link you gave one of the posts suggests: "A simpler way is to use UUID or LABEL mounting."

The udev rules are certainly worth looking at for your situation.

---

### Post by stchman on 2008-03-27
> **iansane said:**
> Actually I was asking because someone else was having trouble with a usb removeable and some music program that looked to the drive for the music library. He said everytime he had to copy all of the music to the right folder and delete the wrong folder. I didn't really understand his problem but it seems like a legitimate question to me. 

Sorry if I sounded like a jerk Nick. I just get frustrated and I know there's got to be a way. I'll either get it figured out or someone will tell me, or I'll forget about it till it comes up in some other issue.

Mounting partitions is actually pretty easy.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Your partitions are labeled sda1, sda2, etc.  These never change unless you change the physical arrangment of the drives in your PC.  I recommend just mounting them in your /media folder as they will appear as an icon on your desktop.

---

