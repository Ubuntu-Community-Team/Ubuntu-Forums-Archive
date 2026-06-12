---
title: "041e:4038 creative Technology, Ltd"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by nixie21 on 2007-10-03
Is there no driver for this camera?

Thanks!

---

### Post by Lambert on 2007-10-04
> **nixie21 said:**
> Is there no driver for this camera?

Thanks!

Doesn't seem to be a lot about this device and linux.

Creative technology webcams with id of 041e:4034 work with the spca5xx driver. Not sure if this will work with your model or if it's even installed with ubuntu.

Hopefully this will help guide you in a search for something more.

```

sudo modinfo spca5xx

```

This command from terminal will give you information about the module.

If it says installed, the try 

```

sudo modprobe spca5xx

```

to see if it will load and bind to your webcam.

---

