---
title: "Audio Issues"
date: 2008-01-23
forum: Apple PPC Users
---

### Post by keiranevans on 2008-01-23
My second post of the day.

I also have an issue with sound.

I haven't heard a thing from my machine. I have tried playing an audio CD through Amarok, but im getting an error saying "audio output unavailable; The device is busy.

Does anybody have any ideas?

Oh and while im at it, i also have to type in Modprobe ide-core to get the machine to boot, i have read the wiki and found the solution but i dont understand how to resolve this.

Im desperate for help on the matters, it's driving me crazy!

---

### Post by Twiggy003 on 2008-02-08
sudo modprobe snd_powermac


Simply enter that command, should sort it out.

---

### Post by stream303 on 2008-02-08
> **keiranevans said:**
> Oh and while im at it, i also have to type in Modprobe ide-core to get the machine to boot, i have read the wiki and found the solution but i dont understand how to resolve this.

If you are wanting to make this permanent, you need to edit as root the modules file and add ide-core to it and then update the initramfs.

```
Post install

Once you have installed add the line

ide-core

to /etc/initramfs-tools/modules and run

sudo update-initramfs -u
```

To edit this file from a terminal, you could issue
```
sudo nano /etc/initramfs-tools/modules
```

or for a more graphical way:
```
gksudo gedit /etc/initramfs-tools/modules
```

---

