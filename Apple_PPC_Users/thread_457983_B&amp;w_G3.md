---
title: "B&amp;w G3"
date: 2007-05-29
forum: Apple PPC Users
---

### Post by flat4 on 2007-05-29
I tried to install from a live cd and it would not work. So I downloaded the alt version and was able to install with no problems. When it rebooted and tried to load X could not start. Something to do with my ATI card. 

My opinion is not ready for me to use on my Mac, if I have to reconfigure files is not worth it. So I reinstall my OS X. On a pc would not hesitate to install and know that its going to boot and work.

:)

---

### Post by EuroCity on 2007-05-29
It should work to install also with the Desktop CD if you type

```
live video=ofonly
```

at the boot prompt.

If you want to use the system you just installed, you could try to edit */etc/yaboot.conf* (for example, by switching to a console with ctrl-alt-f2):

```
sudo nano /etc/yaboot.conf
```

... and modifying it to have

```
quiet splash video=ofonly
```

in one of the last lines (under "Linux", etc.); then, reboot.

BTW, it's really very strange that some ATI cards don't work in Feisty: never happened with previous stable releases!

---

### Post by flat4 on 2007-05-29
Well , I went ahead an reloaded OS X, already. I will try to test it again later but need that machine to render video, slowly but it will render it.

:p

---

### Post by DaDave on 2007-05-29
> **flat4 said:**
> I tried to install from a live cd and it would not work. So I downloaded the alt version and was able to install with no problems. When it rebooted and tried to load X could not start. Something to do with my ATI card. 

My opinion is not ready for me to use on my Mac, if I have to reconfigure files is not worth it. So I reinstall my OS X. On a pc would not hesitate to install and know that its going to boot and work.

:)

Which G3 do you have?

---

### Post by flat4 on 2007-05-29
Blue and White, 400MHZ 120gb and 800 something ram

---

### Post by DaDave on 2007-05-29
> **flat4 said:**
> Blue and White, 400MHZ 120gb and 800 something ram

Thanks. I'm trying to track common problems among the different G3's.

---

### Post by flat4 on 2007-05-29
your welcome

---

