---
title: "What does this error mean for rar files"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Black Mage on 2007-11-29
I'm trying to extra this mkv from a rar and I  get this message:

```

john@devin-laptop:~/Desktop$ rar e cor.movie.karas.revelation.part3.rar

RAR 3.70 beta 1   Copyright (c) 1993-2007 Alexander Roshal   8 Jan 2007
Shareware version         Type RAR -? for help


Extracting from cor.movie.karas.revelation.part3.rar

WARNING: You need to start extraction from a previous volume to unpack cor.movie.karas.revelation/cor.movie.karas.part2.the.revelation.[D99E0879].mkv
No files to extract
john@devin-laptop:~/Desktop$ 


```

And I don't no what it means by previous volume.

---

### Post by popch on 2007-11-29
It looks to me as if the contents of the archive was spread over several rar files, and that you started rar not with the first one. Speculation: given the name of the archive, you started with part 3.

If you have received that rar file from someone, ask for the other parts of the multi-part archive.

---

### Post by PriceChild on 2007-11-29
I'd agree with that diagnosis popch... given **it tells you in the error message**.

*moves thread to support area*

---

### Post by quandary on 2007-11-29
> **Black Mage said:**
> 
.movie.

> 
revelation
> 
.part3.rar
Downloading movies from the internet may be illegal in your contry, so i wouldn't post that in this way here...

You need to start rar from *.part1.rar

To find part 1 to 4 try:
*link removed*
 
it's link nr 3 BTW...

---

