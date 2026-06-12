---
title: "How do I open .run files?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Orixyu on 2006-06-11
Im just wondering how I open .run files?

I've downloaded the radeon 9.25.18-x86_64 drivers, and Im trying to open them, but It seems I cant?

So I decided to skip that, and install some stuff from the Synaptic Package Manager, I found the drivers on there, so I installed them from this location.

How do I get up display information ect? Dont tell me it's all terminal... :-k

---

### Post by loell on 2006-06-11
i thought it can be double clicked in any filemanager you're in. ie nautilus, konqeuror, thunar.

 in any case you can always execute it in the terminal by ./filename.run

---

### Post by taurus on 2006-06-11
And before you run in from a terminal, make sure you have an executable permission first...
```

chmod 755 filename.run
./filename.run

```

---

### Post by Orixyu on 2006-06-11
Okay, I've got it working. It seems the .run file must be in the Home Folder in order for the terminal to work. Interesting...

Is there anyway to make .run files run just by double clicking them, perhaps scripting so that it excutes in terminal, and chmods the file to 755?

Cheers.

---

### Post by taurus on 2006-06-11
Actually, filename.run can be anywhere as long as it's in your path.  And once you have changed the permission, the permission will stay the same so no need to change it everytime you want to run it.

---

