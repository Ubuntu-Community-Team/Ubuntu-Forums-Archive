---
title: "my ubuntu won't start"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by adewale on 2007-04-27
plz help me am already panicking. ubuntu won't start and i have a large file on it it won't even load. plz someone help

---

### Post by AlexenderReez on 2007-04-27
you do know or detect any error ?

---

### Post by scrooge_74 on 2007-04-27
More details are needed.

It won't  boot? You can log in?

---

### Post by Bachstelze on 2007-04-27
We can't help without more information about what it does instead of starting...

---

### Post by whee on 2007-04-27
Could you give some more information? Does it lock up after login, or does it hang during boot-up/hardware initialization?

---

### Post by lamalex on 2007-04-27
step 1. calm down. it's very likely we can help you fix whatever is wrong or at very least get your file off. first. where does boot stop? start by turning off quiet in the boot flags:
at GRUB 1.5 hit esc, then e on the top entry, and remove the word quiet then boot. let us know where it stops.

-EDIT-
zomg you are all so fast

---

### Post by adewale on 2007-04-27
thanks am on mobile so my reply comes a little late i did remove quiet and it still hangs at boot. it doesn't load beyond the ubuntu logo

---

### Post by lamalex on 2007-04-27
read my previous post, take it out of quiet mode and see where it hangs. what text is displayed

---

### Post by adewale on 2007-04-27
i got the escape part and i saw the options but how do i remove quiet as i tried pressing d but still the same

---

### Post by lamalex on 2007-04-27
that's not a d, it's an e.

---

### Post by RomeReactor on 2007-04-27
Hi. You can also press ALT+F2 during boot to see the the messages.

---

### Post by adewale on 2007-04-27
it doesn't give any droop message but it doesn't go beyond reading files needed to boot

---

### Post by lamalex on 2007-04-27
try booting into recovery mode and see if you can get that. hit esc and pick recovery mode.

---

### Post by adewale on 2007-04-27
still the same with recovery. *Reading files needed to boot thanks hope having to reset won't corrupt my data

---

### Post by lamalex on 2007-04-27
do you have an alternate install cd? you could try using the recovery tool in that, and if you have a live cd I would go back up any data you need to a usb drive or something.

---

### Post by adewale on 2007-04-27
i don't haVe an alternate disc but i have dvd version and some live cd's hope that would do

---

### Post by lamalex on 2007-04-27
well if you're just going to reinstall then those will work, but the alternate cd has a function where it will just replace the system files with new ones to fix whatever got messed up. use the livecds to back up your data. there's probably more you can do to fix the problem but if we can't get into a shell then you've reached the end of my knowledge, this where I would use the alternate install cd to fix the sysfiles or just reinstall.

---

### Post by talex on 2007-05-01
I am also very new to Linux, as well as Ubuntu.  I have an older IBM compatible machine, which I installed 7.04 server edition on which will not boot.  The install process seemed perfect, no issues.  I did not partition the drive (yet), I have no other OS I want to run on this machine.  Again, install seemed fine, but when the install is finished and tells me to reboot in to Ubuntu, it will not.  I have checked the voracity of the files on the CD (used Infrarecorder to burn the images) and the CD seems good.  I tried to remove the "quiet" (d) from the first kernel, but I don't think it works.  Every time I go back to edit (e) that kernel, it has repopulated.  I also tried booting from the recover, does the same thing.  I also tried the command line process, it seems to find hd0, kernel /vmlinuz seems to work, initrd /initrd.img does not give any errors (although I wouldn't know what to look for), but still no boot.  Basically, it goes through it's bios check and says "Starting now..." very quickly, then goes back to the bios check, says "Starting now...", etc. in an endless loop.

Any thoughts would be greatly appreciated!

---

