---
title: "Are all program installations Modular?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Wiebelhaus on 2007-11-21
Alittle back story before I get to the question that may be pertinent.

I customized my GDM splash and log in and totally screwed it up , so I had to reinstall after trying many methods of fixing it , Ubuntu was installed on a secondary drive with a Flux install on the main drive for testing purposes , So in order to retain my data and other stuff , I installed ubuntu on that primary drive , I was successfully able to copy my heavily customized and tweaked ./cxoffice folder to the new installation and install crossover and everything worked perfectly.

My question , should I be able to do this with heavily customized Liferea , Pidgin (god , that name still makes me cringe) , Evolution etc. ? Mind you I cannot log into the installation to use any form of the programs backup functionality.

So is it truly modular in the sense that I can drop those folders into their new locations without messing this new install up? Like liferea for example , the ideal recovery would go like this , Install it , it setups links and program local in ./liferea could I take my heavily modded ./liferea folder from the secondary drive in ```
sudo nautilus
```and drop it into the proper location on the primary drive , reboot and use it as it was before I killed the original install?

Thanks.

---

### Post by p_quarles on 2007-11-21
You're just talking about replacing the default .liferea directory in your home directory with the one from your previous installation? Yes, you can do that. I do similar things every time I reinstall. The files in the /home directory are the user settings, so they can almost always be easily ported.

By the way, it's a bad idea to to run any graphical program using "sudo." Try this one instead:
```
gksudo nautilus
```

---

### Post by Wiebelhaus on 2007-11-21
> **p_quarles said:**
> You're just talking about replacing the default .liferea directory in your home directory with the one from your previous installation? Yes, you can do that. I do similar things every time I reinstall. The files in the /home directory are the user settings, so they can almost always be easily ported.

By the way, it's a bad idea to to run any graphical program using "sudo." Try this one instead:
```
gksudo nautilus
```

Thanks for the confirmation!

---

