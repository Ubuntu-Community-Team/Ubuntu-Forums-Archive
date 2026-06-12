---
title: "No sound"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Usheen on 2008-04-17
Hello Linux Community, great to be here!

I recently bought Genius SP-F200 speakers for my Vaio laptop. My hard drive is partitioned: they work fine through Windows Vista, but no sound through Linux. How do I go about configuring sound through these speakers with Ubuntu?

Thanks

---

### Post by warbread on 2008-04-18
The speakers shouldn't matter.  Do you have sound coming out of your built in speakers?  What about when  you plug anything else into the headphones jack?

---

### Post by Tews on 2008-04-18
This is how I fixed the same problem for my Vaio..

```


gksudo gedit /etc/modprobe.d/alsa-base
```

And in the last line of the file, add this line:
```


options snd-hda-intel model=vaio position_fix=0
```

Make SURE that you have the latest version of ALSA installed
Follow the instructiions in this guide .. its very quick a simple..
[http://http://ubuntuforums.org/showpost.php?p=4298 894&postcount=24]("http://http://ubuntuforums.org/showpost.php?p=4298 894&postcount=24")

---

### Post by Usheen on 2008-04-19
Thanx Tews!

the link you posted is broken; i guess u wanted to point me towards the latest version of ALSA?

So i get the file open via the terminal, then add this..
> 
options snd-hda-intel model=vaio position_fix=0


on a new line? or continue from the last code?

then do i save the file, close it, then sound should be coming through speakers?

or is there anything else still to do? 

total newbie :)

---

### Post by Usheen on 2008-04-19
> **warbread said:**
> The speakers shouldn't matter.  Do you have sound coming out of your built in speakers?  What about when  you plug anything else into the headphones jack?

Yep, built-in speakers are fine. Headfones jack is fine coz speakers clicked when i tried them through vista

---

### Post by Usheen on 2008-05-04
Aw what happened guys n gals? Before youz rushed to help and i got responses in minutes, but now nothin in two weeks!

---

