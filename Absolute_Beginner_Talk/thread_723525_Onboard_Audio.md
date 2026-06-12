---
title: "Onboard Audio"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-13
this is a reoccurring topic i know and i have searched everywhere for a fix.  I just installed Ubuntu 7.10 on an eMachines T4060 and the onboard audio dos not work.  
alsamixer doesn't work:
```

titan@dungeon:~$ sudo alsamixer
[sudo] password for titan:

alsamixer: function snd_ctl_open failed for default: No such device
titan@dungeon:~$ 

```

and clicking on the little speaker gives me this error:
```

No volume control GStreamer plugins and/or devices found.

```

any suggestions?

---

### Post by StOoZ on 2008-03-13
can you paste this : 
"lspci | grep audio"
in the terminal and paste the outcome here ?
I would like to see the type of the audio chip.

---

### Post by The Titan on 2008-03-13
um... Did i do something wrong or is this normal?

```

titan@dungeon:~$ lspci | grep audio
titan@dungeon:~$ 

```

either way, i appreciate your response?

---

### Post by The Titan on 2008-03-13
Anyone?? bump...

---

