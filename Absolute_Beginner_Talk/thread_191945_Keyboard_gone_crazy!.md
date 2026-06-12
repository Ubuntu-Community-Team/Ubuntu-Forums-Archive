---
title: "Keyboard gone crazy!"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-06-08
My laptop keyboard has gone crazy. When I type something on it, it's like I hammered the keys.
Example: hello myyyyyyyyyyyyyyyyyy name is gardar how are yoooooooooooooooooou?

This is more likely to heppen when I type fast keyboard but also heppens when I type real slowly.

I'm on windows XP dualboot and this doesn't heppen on winxp

This can't get anymore annoying and it's taking me about forever to post this message.

Help please! :rolleyes:

---

### Post by mostwanted on 2006-06-08
Did you change anything in your xorg.conf file recently?

---

### Post by gardara on 2006-06-08
[QUOTE=mostwanted]Did you change anything in your xorg.conf file recently?[/QUOTE]

nope, I just did a fresh install lassssssssssssssssssst friddddddddddddddddday.

like you can see here: [http://ubuntuforums.org/showthread.php?t=186196](http://ubuntuforums.org/showthread.php?t=186196)

PS. Sorry for multtttttttttttttttttiple letters, don't have time to delete them all...

---

### Post by bruce89 on 2006-06-08
System>Preferences>Keyboard.  You can then change the repeat settings there.  It should look like this -

---

### Post by gardara on 2006-06-08
bruce89, all my settings are the same as yours, I tried going into Accessbility and turned off *enable repeat keys*. Then everything seems to work ok :)

---

### Post by bruce89 on 2006-06-08
[QUOTE=gardara]bruce89, all my settings are the same as yours, I tried going into Accessbility and turned off *enable repeat keys*. Then everything seems to work ok :)[/QUOTE]
That will be the problem then.

---

### Post by bierpullen on 2006-06-15
i have the same problem on my acer aspire 1522.
I use dapper since some time now.
I have this problem voor 5 weeks.



----------------------------------------
Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by tseliot on 2006-06-15
It's a bug.

A fix has been released today:
[https://launchpad.net/bugs/39315]("https://launchpad.net/bugs/39315")

---

### Post by gardara on 2006-06-16
[QUOTE=tseliot]It's a bug.

A fix has been released today:
[https://launchpad.net/bugs/39315]("https://launchpad.net/bugs/39315")[/QUOTE]


aah, good to hear it was fixed :)

---

### Post by matrooswolf on 2006-06-16
Aha! So this was a bug??
 
I thought I had a problem with my keyboard, and already spent a fortune on batteries, (and was planning to buy a new keyboard ...)

If its really fixed, this could save me a lot of money ;)

---

### Post by k225yt on 2006-06-16
I just solved that problem. People say there are 2 ways (more, actually):
1. Remove the plptools package. or
2. sudo rmmod acpi_sbs.
The 2nd way worked for me. I even recompiled my kernel without a support for smart battary (that is what that module does), and ...

Good luck:D 

PS [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)

---

### Post by bierpullen on 2006-06-17
good to hear it was fixed.:D :D :D :D 

sudo rmmod acpi_sbs worked for me.




----------------------------------------
Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php](http://www.antarctica-rbak.nl/ubuntu/acer_aspire.php)

---

### Post by ayoli on 2006-06-18
well, have the same keyboard pb on my toshiba sattelite L10.
removing acpi_sbs module seems to work for me, i type this message without letters skipped or repeated randomly, cool ...
BUT this is not really a good fix cause now i can't see my battery status anymore, and this is quite anoying since i've got a laptop and use it on battery sometimes.
Any ideas for a better fix ?

---

### Post by ayoli on 2006-06-18
ok this seems to fix the keyboard pb:
```

modprobe -r psmouse
modprobe psmouse rate=40
```

but this makes my synaptic touchpad loosing some of its functions (such as scrolling)

rah !! makes me mad ](*,)

edit: lol, changing psmouse rate doesnt fix the pb, just less pb.

---

