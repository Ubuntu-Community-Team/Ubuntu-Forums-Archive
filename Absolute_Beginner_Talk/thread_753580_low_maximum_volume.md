---
title: "low maximum volume"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-04-12
on my Toshiba Satellite, i am getting a low maximum volume then what I had before. I am running Gutsy Gibbon. It was working before but I think after I installed one of linux-image-* updates, the maximum volume went down.  Perhaps a configuration file was changed ?

Can someone help me with this?

---

### Post by Mark20 on 2008-04-13
What volume control program are you using?

Does your volume control have a setting with "PCM" written near it?  Changing the PCM helps my laptop get very very loud.

---

### Post by sayakb on 2008-04-13
Open a terminal and type: ```
alsamixer
``` Adjust all available controls there to get the best output.

---

