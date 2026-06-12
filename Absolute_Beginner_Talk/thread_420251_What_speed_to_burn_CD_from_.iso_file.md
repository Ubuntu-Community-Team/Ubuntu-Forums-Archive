---
title: "What speed to burn CD from .iso file?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-04-23
I'm using Dapper with k3b ( 0.12.14-0ubuntu7 ) to burn a CD from a Feisty .iso file.

From what I have read, I should do it slowly however, when I try to set it to run at 4x, it switches back to a much faster speed.

Is there a better program I could use than k3b, or am I doing something wrong?

---

### Post by Outrunner on 2007-04-23
I'm not sure if this is possible, but maybe you're CD doesn't support such a low speed. I know I tried to burn a DVD once and I couldn't because the speed was too low. Try x6 or x8

---

### Post by tonyr1988 on 2007-04-23
I'm not positive, but I remember reading something somewhere about some writing drives having a minimum speed that they can burn at. If that's the case, then there's nothing you can really do.

I'd say set it at 4x, let it burn, and run it and see if it works correctly.

---

### Post by mahy on 2007-04-23
Does the resulting CD work? If yes, then there's no need to worry...

---

### Post by aysiu on 2007-04-23
I've always burnt ISOs from K3B at 4x and have had no switching of speeds.

I'm inclined to agree with Outrunner on this--maybe your burner doesn't support such a low speed... or maybe the CD itself doesn't.

---

### Post by crav on 2007-04-23
My laptop's burner maxes at 24x and I've never had a problem with any burn, I wouldn't think you would either.

A 56x burner I had in a tower sometime back did mess up fairly often however. It seems to me as long as your not at a speed that's absolutely excessive, you shouldn't have a problem.

---

### Post by n3tfury on 2007-04-23
> **mahy said:**
> Does the resulting CD work? If yes, then there's no need to worry...

he's got reasons to worry.

---

### Post by L Campbell on 2007-04-23
> **mahy said:**
> Does the resulting CD work? If yes, then there's no need to worry...

Thanks for your interest.

It hasn't worked yet, so what I am trying to do is to see whether I could have made a 'not so good' CD.

Also, there could be a fault with my computer but I'd like to minimize the chance of errors on the CD before I tear into the computer.

---

### Post by earobinson on 2007-04-23
you should be able to test the cd when you put it in (its like the third option or something) thats assuming you get that far

---

### Post by aysiu on 2007-04-23
> **L Campbell said:**
> Thanks for your interest.

It hasn't worked yet, so what I am trying to do is to see whether I could have made a 'not so good' CD.

Also, there could be a fault with my computer but I'd like to minimize the chance of errors on the CD before I tear into the computer.
Do a checksum on the ISO to see if it was corrupted during download:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_check_MD5_checksum_of_files](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_check_MD5_checksum_of_files)

If it was corrupted during download, burning at a slower speed won't help.

---

### Post by L Campbell on 2007-04-23
> **aysiu said:**
> Do a checksum on the ISO to see if it was corrupted during download:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_check_MD5_checksum_of_files](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_check_MD5_checksum_of_files)

If it was corrupted during download, burning at a slower speed won't help.

Thanks, for that link.

I did run ck5sum and it came up with the number it was supposed to.  Also, it seems like k3b ran ck5sum again before burning the CD, so maybe it IS something wrong with my computer.

---

