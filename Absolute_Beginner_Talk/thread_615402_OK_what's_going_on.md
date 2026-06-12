---
title: "OK what's going on?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jpsimm on 2007-11-17
Hi everyone,

Guess what?   I just installed the 64bit version of 7.10 to replace my 64bit version of 7.06 and discovered now that I cannot download very many programs.  In fact just about everything except games is off limits to me now for some strange reason.  

When I select an application for downloading which I had used in 7.06, on the same computer which has not been modified, I now get a message in the application description window which says the program is not oK with my CPU which is an Athelon Sempron 64bit and that I cannot download it.  

Are these false messages or what?  I tried for Thunderbird Mail because I prefer it to Evolution and cannot get it.  What gives????

Will an Ubuntu Egghead please explain this?

Thanks,

jpsimm:confused:

---

### Post by PmDematagoda on 2007-11-17
Please post the output of:-
```

cat /etc/apt/sources.list

```

---

### Post by Martje_001 on 2007-11-17
After an
```
sudo apt-get update
```
can you download?

---

