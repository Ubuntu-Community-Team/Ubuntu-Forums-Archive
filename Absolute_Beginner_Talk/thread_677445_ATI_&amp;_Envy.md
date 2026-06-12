---
title: "ATI &amp; Envy"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Bri0 on 2008-01-24
How am I supposed to install ATI drivers in Envy when I already have the drivers from ATIs site downloaded on my desktop?

ati-driver-installer-8-01-x86.x86_64.run

Thanks

---

### Post by rune0077 on 2008-01-24
You can't. Envy will download the drivers by itself, then install what was downloaded, which can be a problem if you don't want the newest drivers. But that's how the program works.

---

### Post by Bri0 on 2008-01-24
Great, another 30min to down. :mad:

Is there at least a way to backup the downed driver for off-line install with Envy in case I need to reinstall the OS?

---

### Post by rune0077 on 2008-01-24
Not that I know of, but I suppose they must be there somewhere on your system. You can get them yourself here: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html). Envy always just downloads the latest drivers fitting your system (32 or 64 bit).

---

### Post by Bri0 on 2008-01-24
Envy downs it in /usr/share/envy

But if I give the folder permission, and add 'ati-driver-installer-8-01-x86.x86_64.run' in to it, then start up Envy and check Install ATI Drivers, it overwrites it and start downloading the driver from the beginning if online.

If offline it deletes 'ati-driver-installer-8-01-x86.x86_64.run' from the envy folder and I get this. Do I have to type something in?

[IMG]http://www.geocities.com/bri_cowl/envy1.jpg[/IMG]

---

### Post by rune0077 on 2008-01-25
It looks from your output like Envy insists on checking for the driver online, so I'm not sure you could do anything about it. Maybe you could fool it by renaming your file to the exact same name of the file Envy is looking for (ati-driver-installer-8-01-x86.x86_64.run), but really, that's just a wild guess from my part.

---

