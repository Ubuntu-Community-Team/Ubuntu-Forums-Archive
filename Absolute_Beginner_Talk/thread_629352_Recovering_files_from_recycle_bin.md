---
title: "Recovering files from recycle bin"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-02
I accidentally put the wrong document in the recycle bin and emptied trash before I realized that it was the wrong document, which I really need back... Is there an easy way to recover these files, after the trash has been removed??

---

### Post by skyjacker on 2007-12-02
> **fmbugdadi said:**
> I accidentally put the wrong document in the recycle bin and emptied trash before I realized that it was the wrong document, which I really need back... Is there an easy way to recover these files, after the trash has been removed?? As far as I know it's just like windows - once you empty the trash its gone.:(

---

### Post by fmbugdadi on 2007-12-02
Well, in Windows, the files can actually be recovered by going to a restore point earlier in time, so in reality windows does not "wipe" recycle bin files, it just makes the space available where they where. So I guess my question is; Does the linux recycle bin delete the files, or does it wipe them?

---

### Post by monte48lowes on 2007-12-02
It does not overwrite the file. It merely deletes the address to it. Try this:

```
lsof | grep *NAME OF YOUR FILE*
```

Mike

Read here for more information:

[http://www.linux.com/articles/58142?tid=47]("http://www.linux.com/articles/58142?tid=47")

---

### Post by rich.bradshaw on 2007-12-02
Generally you won't be able to recover the file.

---

### Post by monte48lowes on 2007-12-02
There is also 'photorec' which can recover every file it can find on the hard drive... lost a drive with family photos on it.... 300,000 files later.. I had them back.

Mike

---

