---
title: "Acrobat Reader and Firefox"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by neo.patrix on 2007-06-13
Hello,

I had installed Acrobat Reader 7.0.9, it used to work well with Edgy but somehow it does not work with Feisty. but anyways that is not my problem.

The problem is when I had installed , I had configured firefox to use Acrobat Reader for opening online PDFs. Firefox is still looking for Acroread eventhough I have uninstalled it. Whenever I try to open online PDF, firefox throws an error message saying it cannot find acrobat reader on path.

I have no clue how to modify Firefox configuration to use some other document reader other than acroread. 

Thanks in advance.

---

### Post by moffa on 2007-06-13
```
 sudo rm /usr/lib/firefox/plugins/nppdf.so 
``` should remove the acrobat reader plugin for firefox

---

### Post by neo.patrix on 2007-06-13
Thanks for replying, but I figured out my exact problem and solution . 

I had already deleted that plugin but that does not solve the problem b'cuz even after deletion of .so ,  firefox trys to open PDFs with Acrobat Reader

So I needed to configrue firefox to use different application to open PDFs. The solution is so simple, but I could not see it. It is just EDIT-->PREFERENCES and changing some settings.

---

### Post by hyper_ch on 2007-06-13
May I ask why you did install acrobat reader? Ubuntu and Xubuntu come with Evince and Kubuntu with some other pdf reader :)

---

### Post by neo.patrix on 2007-06-13
Because i was accustomed to use it windows...but then i realized that i don't really need it. Linuxification, i suppose...:lolflag:

---

