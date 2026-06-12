---
title: "Camera no longer working with ubuntu- no drivers?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-10-20
I upgraded to Gutsy the other day, now my camer, a Panasonic DMC-TZ3 is no longer detected when I connect it to transfer pictures. How can I fix this? is anyone else having this issue? The error message I get is:

"An error occurred in the io-library ('Unspecified error'): No error description available"

There are other panasonic camera models supported and when I was using Feisty, everything worked fine; I could open up the folders with my pics on it in the camera and transfer them.
What should I do?

Thanks!

---

### Post by mrcbldn on 2008-03-24
I had the same problem with a Canon Coolpix 5600; the message was:

```
"An error occurred in the io-library ('Unspecified error'): No error description available"
```

I resolved with **PTP** transfer mode setted to camera; it seems a problem with libgphoto2 libraries. :)

---

