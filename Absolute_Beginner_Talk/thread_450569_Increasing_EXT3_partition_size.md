---
title: "Increasing EXT3 partition size"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-05-21
I have got to the stage now where i want to reduce my windows partition to the bare minuimum, basically as a safety net incase linux goes wrong. i think it is a good practice to have two OSs installed, just as a safety feature.

However, is there a decent gui partition tool in ubuntu? And, can i reduce the size of my NTFS partiton and increase the EXT3 partition in the same program? or will i have to reboot into windows, reduce it using some 3rd party program, and then enlarge the EXT3 partiton in linux?

Any help would be greatly appreciated. Andy.

---

### Post by taurus on 2007-05-21
You can use GParted LiveCD to do that, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

---

### Post by Inxsible on 2007-05-21
I haven't seen any other program that would compel me to use something other than GParted, to do what you need to do !

---

### Post by SuperAndy on 2007-05-21
cheers guys. downloading the iso now...

i wont be giving it a go untill a bit later... but hopefully, windows could be totally denatured :P

---

### Post by Sweet Mercury on 2007-05-21
> **taurus said:**
> You can use GParted LiveCD to do that, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Oh cool, thanks.

This was going to be my next issue that I needed to tackle (since I somehow read the partition sizer backwards when I installed Ubuntu (giving myself < 10GB for Ubuntu).

I'll be trying this momentarily and I'll give a complete progress report =).

---

### Post by Sweet Mercury on 2007-05-21
> **Sweet Mercury said:**
> Oh cool, thanks.

This was going to be my next issue that I needed to tackle (since I somehow read the partition sizer backwards when I installed Ubuntu (giving myself < 10GB for Ubuntu).

I'll be trying this momentarily and I'll give a complete progress report =).

Success!

My first attempt was unsuccessful—I had logged into the default option on the GParted Live CD, something went awry. My second attempt worked, though, after I logged into the second option on the CD.

Thanks for this utility!

Also, to the OP, when I rebooted windows it had to do it's check of the file system for integrity, so if your comp does something similar don't worry about it. Windows still works for me.

---

### Post by Sweet Mercury on 2007-05-21
One more issue. I don't know if it's because I had the partitioner copy all my data to another portion of the disk, but I lost my wireless interface (wireless module? not sure what it's properly called in Linux).

I had to re-enter the code
```
sudo modprobe ndiswrapper
```

to get it back.

Just a heads up.

---

