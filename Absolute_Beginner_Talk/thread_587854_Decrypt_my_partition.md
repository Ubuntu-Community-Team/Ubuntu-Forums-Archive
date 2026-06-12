---
title: "Decrypt my partition"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by pimarius on 2007-10-23
Hi!


I have a big problem with my computer. I was just doing my homework when I found some interesting commands on the web and I decided to try them without reading all the information about. So I used "dd if=/dev/urandom of=/dev/sda5" (/dev/sda5 is a ntfs partition) and after I saw that this command it's going to take a while I pressed CTRL+C to terminate it. The output was something like: 16Mb done. Since that moment I can not acces the files on that partion and I really need some documents from it. Please help me!

Thanks in advance!
Marius

---

### Post by realvz on 2007-10-23
where did you do this from???

i think you copied /dev/urandom contents over /dev/sda5....i think this is what the above command will do...

i am not sure though!!

---

### Post by hyper_ch on 2007-10-23
/dev/urandom is sort of a random generator and the dd command copies just from (if= --> input file) to (of= --> output file)

So you have overwritten the first 16 MB of the harddisk and rendered the data useless. Well, the data is still there but it's lacking the structure of (or something).

since that partition is ntfs you could try with some windows recovery tools to get your data back.

---

