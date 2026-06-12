---
title: "Wine sound error &quot;audio test not implemented yet&quot;"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ChenJianYi on 2007-06-01
I installed wine using Automatix2
When I was setting the wine configuration, it can't test sound and run the control panel at Sound Tab.
and when i started wine, appear an error message :

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

but when i was installing wine, it passed all the test.
what should i do to correct this error ?

thank you

---

### Post by aroch1 on 2007-06-01
After running ```
winecfg
``` on the Sound tab change one of the dropdown boxes (sorry...can't tell you which because I'm on my work computer) to emulation.  That got it working for me

---

### Post by ChenJianYi on 2007-06-01
it still didn't work for me.

---

### Post by kevinmedina on 2007-08-05
I'm having the exact same problem! Does anyone have any suggestions?

---

### Post by kevinmedina on 2007-08-05
:: bump ::

---

### Post by splintercellguy on 2007-08-05
The sound test isn't implemented...?

---

### Post by kevinmedina on 2007-08-05
When in the WineCFG and on the Audio Tab, clicking on test sound results in this message:

Audio test not implemented yet

When trying to install Star Wars Empire at War I immediately get the following error:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

---

### Post by kevinmedina on 2007-08-05
Sorry, but 

:: bump ::

---

### Post by kevinmedina on 2007-08-05
Any help or guidance would be greatly appreciate

---

### Post by Gabn on 2007-09-03
open winecfg 

go to audio tab select OSS Driver deselect ALSA driver 

under Hardware acceleration select emulated from the drop down list 

test sound button doesn't work on any wine system yet you need to go code it yourself :P

---

