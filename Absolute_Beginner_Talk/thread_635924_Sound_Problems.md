---
title: "Sound Problems"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Ajay Ramaseshan on 2007-12-09
I am a new user to Ubuntu 7.04 and finding problems with the sound systems..
I have dual booted Windows Vista and Ubuntu 7.04 and whenever I restart my comp to go from Windows to Linux, I find that th sound gets muted,, even if the volume is set to max..

Also whenever I connect an external headphone in Ubuntu the sound just refuses to come from the headphone it always plays it from the internal speakers...

Could anyone give me a solution to this ??

---

### Post by Delvien on 2007-12-09
check out the options when you put this into a terminal 

```
 alsamixer 
```

Make sure nothing is muted.

---

### Post by staticvoid on 2007-12-09
in your sound perferences under "administration>preferences" ithnk, you can set it to control the PCM, which is both headphones and speakers. if you have an intel card do aslamixer and UNMUTE external amp.

or you can right click on the volume contro and add the switch for external and uncheck it.

check your BIOS and see what the sound gets automatially set at.


or just delete windows and only use Ubuntu. Or Kubuntu if your a power user. Once you get the sound working I mean ;).



sv

---

