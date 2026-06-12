---
title: "xmms only works with root privileges: How to fix it ?"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-07
xmms only works with root privileges: How to fix it ?

I'd like users can also use xmms ... 

Is it possible ??

Thank you very much

(what is wrong/ what to do )


thank you very much

---

### Post by mlomker on 2005-10-07
Try this as an immediate test:

```

sudo chmod 666 /dev/dsp

```

Are your user accounts all members of the audio group?

---

### Post by patrick295767 on 2005-10-07
[QUOTE=mlomker]Try this as an immediate test:

```

sudo chmod 666 /dev/dsp

```

Are your user accounts all members of the audio group?[/QUOTE]


Thank you very much !!! 

I would have never thougth that even the dev could receive their chmod !!

Terribly Linux !!!
(great)

---

