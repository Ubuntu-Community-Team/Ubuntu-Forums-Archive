---
title: "dvd rom not working"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-02-14
Hello everybody!

I would like to know how to UNinstall a dvd rom in Kubuntu.

I went to system settings, and i tried deleting it,  but it does not go away.

That is the way im used to fix things (windoes) so I would like to hear a method to do an uninstall and then reboot the system and hopefully it will be detected and run like it did before.

I do not have details about the problem right now, but it was working, now its not.

Thank you all!!

---

### Post by gigaferz on 2007-02-14
when I try to use any cd or dvd it tells me
According to mtab, /dev/hdc is already mounted on /media/cdrom0
mount failed

---

### Post by gigaferz on 2007-02-15
ok, well

I unmounted it manually on the command line, but it was still not functioning.

And for some reason the on the gui, it was not  working either, after asking for the password, it never changed everything was grey.
Anyway iI found a thread, and after reading everything I camre with an idea 
I just edited   fstab  and changed the filesystem from ramf to iso.
saved the file and rebooted, it works better but still has some flaws,

I am running Kubuntu 6.06 on a P3 @ 800mhz with 320 ram (thats what Kinfo says) ita an old Gateway.

Just in case  somebody on the future mught need it, I found this thread by typing mtab on the search box.

here it is.== [http://www.ubuntuforums.org/showthread.php?t=343671&highlight=mtab](http://www.ubuntuforums.org/showthread.php?t=343671&highlight=mtab)

---

