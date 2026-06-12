---
title: "How to mount a network hard drive?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by jonboy99 on 2007-07-06
Hi folks, sorry for the numpty question.

I want to know how to mount a NAS (it's a synology 207) [http://www.overclockers.co.uk/showproduct.php?prodid=HD-007-SY](http://www.overclockers.co.uk/showproduct.php?prodid=HD-007-SY)


I have it working fine in windows, and mapped to a drive letter - the included software set it up in seconds.

Not sure how to do it in ubuntu (dapper).

The NAS has the IP addy 192.168.1.16 and the shared folder on it is called NETfolder

Any ideas?   I'd also like to automount it at boot, but can probably figure that out on my own if I know the mount command.

Cheers peeps
Jon

---

### Post by jonboy99 on 2007-07-06
OK, i've figured out in windows I jsut need to map a drive letter to \\192.168.1.16\NETfolder - is there an equivalent way to do this using the mount command in linux?

---

### Post by devmnky on 2007-07-07
You may want to try searching for how to mount a samba share.  Try looking at this thread and el_poderoso's post [here]("http://ubuntuforums.org/showpost.php?p=2980469&postcount=4").

Hope that helps.

---

