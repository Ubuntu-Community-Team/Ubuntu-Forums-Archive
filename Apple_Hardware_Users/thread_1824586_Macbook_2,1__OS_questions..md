---
title: "Macbook 2,1  OS questions."
date: 2011-08-14
forum: Apple Hardware Users
---

### Post by PyroXFire on 2011-08-14
I'm truely sorry to everyone has answered any of the questions and things discussed here but i couldn't find clear answers from google sadly. 

i have a macbook 2,1 not that it truely matters. anyways i  took out the orginal 160GB drive and replaced it with a  250GB but before i did that i have OSX and win7 dual installed on the 160GB and i have ubuntu on the 250GB

now OSX boots beatifuly via usb and thats great but now im out of luck booting my win7. i would like to try avoiding reinstalling and setting up any of the OS. so is there anyways to take the 250GB out and make the preinstalled ubuntu run via usb? or is there an easy way i can move the win7 partition onto the 250GB next to ubuntu and get grub it pick it up and boot it? i thank everyone for there help and time.

---

### Post by crook17 on 2011-08-14
Copying the partition across is easy, you can use gparted form a Ubuntu live cd

Once copied across simply run
```
sudo update-grub
```

let us know how u go

---

### Post by PyroXFire on 2011-08-14
oh thank you. im always still abit confused when it comes to grub lol and im always scared to mess with it. im about to try this out. will my mac osx install disc work too? (i have it closer on hand) just resize the ubuntu partioton and copy the windows part. into the new blank part. then boot into ubuntu and update grub?

---

### Post by crook17 on 2011-08-14
Thats ok, remember google is your friend :)

Not sure what you mean by "will my mac osx install disc work too?". If you mean can you use gparted on OSX then no you will want to use ubuntu for that.

i'm assuming that you want to copy "clone" the disks with much larger install partitions, am i correct? -- clonzilla might be a better option.

---

### Post by PyroXFire on 2011-08-14
Oh i ment my snow leapord install disc it boots a live cd mac osx and has a disk utility. and yeah sorta. i just want to have all 3 OS'es aviable for use easily but at the same time i have alot of data and i dont really want to fit all three on just one of the drive i pray i can get a bigger one sometime but im going to aim for osx being usb on the 160 then just have windows and ubuntu share the 250GB

---

### Post by crook17 on 2011-08-14
In my opinion you are better off leaving the 160gb drive in the computer and use the 256 as a external drive with all your data, that way you will have better preforming Os's.

However if i understand correctly you wish to
1.boot OSX of the 160gb drive via usb 
2.Use the 256gb drive internally for storing data and booting Ubuntu and Windows.

You will need;
1.Your computer
2.Ubuntu Live cd
3.the 2 hard drives
4.Windows repair disk
5.Internet connection

To do this simply;
1.Install the 256gb drive internally
2.Plug the 160gb drive in via usb
3.boot of a live Ubuntu cd
4.open gparted
5.select the Ubuntu/swap partitions and copy them to the 256gb drive
6.select the Windows partition and copy across to the 256gb drive
7.arrange partitions on the 256gb drive if necessary
8.apply all the changes(this could take a very long time)
9.insert the Windows repair disk and allow it to repair the MBR to update all the required files.
10.boot up the Ubuntu live cd and follow this guide 
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

let me know how you go if you are unsure about anything let me know or Google it, be sure to report your findings back here so that others with this problem may find this thread of use

---

### Post by PyroXFire on 2011-08-15
yeah there where problems gparted wont read the patitions on the 160GB i dont know why it shows up as unknown even the windows (is it because i installed windows via bootcamp maybe? ) and when i tried to use macs disk ultily it acted like it was working then at the last second gave me a error saying the partition didnt exist (when i was telling it to make a new one -.- ) and now the 250GB wont boot.. so for now i put the 160 back it and just said screw it formatted the 250GB for now and ill wait till i get a bigger hard drive to boot all three.

also you mentioned the 160GB would make my OS faster ? im guessing as will all apple things the hard drive is high qauilty unlike the 250GB i pulled from a seagate usb hard drive lol
but then when i buy a new hard drive what kind should i get to make sure there isnt a slow down?

---

### Post by crook17 on 2011-08-16
> yeah there where problems gparted wont read the patitions on the 160GB i dont know why it shows up as unknown even the windows (is it because i installed windows via bootcamp maybe? )

thats strange, the only thing i can think of is put the 160 drive in and shut the computer down correctly boot into the live cd and see how you go.


> when i tried to use macs disk ultily it acted like it was working then at the last second gave me a error saying the partition didnt exist (when i was telling it to make a new one -.- )

again not sure, maybe the computer didn't successfully shut down, this would explain gparted's behavior


> the 250GB wont boot.. so for now i put the 160 back it and just said screw it formatted the 250GB for now and ill wait till i get a bigger hard drive to boot all three.

thats because there would be no MBR on the drive


> also you mentioned the 160GB would make my OS faster ? im guessing as will all apple things the hard drive is high qauilty unlike the 250GB i pulled from a seagate usb hard drive lol

what i meant was usb has a data transfer rate of 40MB/s. Sata 3GB/s (rough figures).The 160 drive has your OS's working on it by trying to boot the drive from usb instead of sata you disk R/W speed is dramatically reduced.
[http://www.tomshardware.com/forum/174836-32-sata-transfer-rate](http://www.tomshardware.com/forum/174836-32-sata-transfer-rate)

> but then when i buy a new hard drive what kind should i get to make sure there isnt a slow down?

i'm no expert on hard disk drives but this may help

[http://compreviews.about.com/od/storage/a/HDBuyersPt1.htm](http://compreviews.about.com/od/storage/a/HDBuyersPt1.htm)

---

