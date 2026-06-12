---
title: "dd resume"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2008-03-25
i have been doing an ipod dd session and i managed to copy 44 out of the 60gb, but somehow the cable became loose :(

is there a way to resume the dd or should i start over?

---

### Post by ruy_lopez on 2008-03-25
> **nonewmsgs said:**
> i have been doing an ipod dd session and i managed to copy 44 out of the 60gb, but somehow the cable became loose :(

is there a way to resume the dd or should i start over?

You might need to start over. But first, you might want to install "dcfldd". dcfldd is the same as dd, but gives you a progress report.

You can try this:
```

dcfldd if=ipod of=cont_dump.dd ibs=1G skip=40

dcfldd if=44gb_file.dd of=new_dump.dd ibs=1G count=40
dcfldd if=cont_dump.dd of=new_dump.dd obs=1G seek=40

```

ibs: is input block size
obs: is output block size
count: number of blocks to read
skip: number of blocks to skip from input
seek: number of block to skip from output

This will skip 40Gb from the ipod. Then it will copy 40gb from the file you already dumped to a new file. Finally it will write the remainder, from the first command, on the end of the new file.

---

