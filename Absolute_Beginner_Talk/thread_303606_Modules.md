---
title: "Modules ?"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Talon2 on 2006-11-20
I'd like to understand more about modules but can't seem to find a source that doesn't assume I've ran Linux from the beginning.

What modules are included in a new Edgy install?

Where are they located?

What filename extention do they use, if any?

Do I need to do a compilation if I don't find the module I'm looking for?

Is there a list of all modules that are included in the current kernel?

---

### Post by Talon2 on 2006-11-20
bump

---

### Post by deanlinkous on 2006-11-20
google **linux modules**

install modconf and run it from command line and take a look at the modules

---

### Post by Talon2 on 2006-11-20
> **deanlinkous said:**
> google **linux modules**

install modconf and run it from command line and take a look at the modules

I've now tried modcong.  Here is what it tells me:

WARNING: Error inserting videodev (/lib/modules/2.6.15-27-386/kernel/drivers/media/video/videodev.ko): Operation not permitted
FATAL: Error inserting radio_aimslab (/lib/modules/2.6.15-27-386/kernel/drivers/media/radio/radio-aimslab.ko): Operation not permitted

Installation failed.
---

I have no idea what this msg is telling me.

---

### Post by furiousV on 2006-11-20
> **Talon2 said:**
> I've now tried modcong.  Here is what it tells me:

WARNING: Error inserting videodev (/lib/modules/2.6.15-27-386/kernel/drivers/media/video/videodev.ko): Operation not permitted
FATAL: Error inserting radio_aimslab (/lib/modules/2.6.15-27-386/kernel/drivers/media/radio/radio-aimslab.ko): Operation not permitted

Installation failed.
---

I have no idea what this msg is telling me.

Run the command again, with **sudo** infront of it.

```

sudo modconf

```

Just be careful what you do :)

Also try **lsmod** . . . again you might have to **sudo** that.

---

### Post by Talon2 on 2006-11-20
[QUOTE=furiousV;1785756]Run the command again, with **sudo** infront of it.

```

sudo modconf

```


Thanks furiousV.  sudo modconf worked.

Whew.  I've got to say that getting this card working was painful.  Googling just doesn't work well sometimes.  There is so much info out there and so much of it is either dated or different on different distros or is simply confusing.

---

