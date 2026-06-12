---
title: "K7 Kernel?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by caravel on 2006-10-20
I've seen mention of a K7 kernel but couldn't find it in synaptics. Should I do: "sudo apt-get install linux-k7" (I'm at work, hence why I haven't tried it yet)?

If I do install it will I see any great difference?  As yet I haven't really noticed much difference running the 686 kernel.  I have an old Athlon XP 2400+ (T-Bred B).

Regards

Caravel

---

### Post by CatKiller on 2006-10-20
I believe that linux-k7 is a metapackage whose sole purpose is to depend on the latest version of the appropriate K7 bits. So installing that should get you what you want. I'm surprised that you installed the 686 kernel, given that you don't have a 686 processor.

I haven't noticed much difference with the K7 kernel on my T-Bird, but I wasn't using the 386 kernel for very long.

---

### Post by Kateikyoushi on 2006-10-20
You won't notice anything by installing the k7 either.

---

### Post by SebMKd on 2006-10-20
I've used _386 kernel on my sempron based rig for over a month. I've tried for a few days _k7 and didn't notice any difference. I'm switching back to _386 (which I think would be better supported?!). 

However, I'd be curious to know what are the actual differences between the two? -- I'm pro AMD :cool: 

S.

---

### Post by angkor on 2006-10-20
> **SebMKd said:**
> However, I'd be curious to know what are the actual differences between the two? -- I'm pro AMD :cool: 
S.

Apart from the k7 being optimized for amd procs (didn't notice any difference), it detects more ram. When I used the standard i386 kernel it used only +/- 930MB of my ram. I have more than that and want a kernel that'll make full use of it. (I don't know if this is still the case, though, cause I haven't been running the i386 for about a year now.)

The i386 also didn't recognize the second core on my cpu, for that I also needed a K7 kernel.

---

### Post by Kateikyoushi on 2006-10-20
I remember I wrote about it a while ago now found that post. [Link]("http://ubuntuforums.org/showpost.php?p=1601016&postcount=4")

---

### Post by caravel on 2006-10-21
Well, due to the lack of a 786 kernel (except the K7 kernel that is), I installed the 686 because I presumed it to be closer to my CPU's architecture type than the 386 kernel?

---

### Post by Kateikyoushi on 2006-10-21
Yes the i686 matches your cpu the best.

---

### Post by caravel on 2006-10-21
I've installed the K7 kernel and all appears to be well.  I don't expect to notice the difference either.

---

### Post by az on 2006-10-21
> **Kateikyoushi said:**
> Yes the i686 matches your cpu the best.

No.  The k7 kernel best matches an Athlon.

My experience has been that there is a noticeable difference in performance when using a specialised kernel on older hardware.

---

### Post by Kateikyoushi on 2006-10-21
I am quite aware of that read my previous posts or the link, I meant if he has to choose whether use the i386 or the i686.

---

### Post by caravel on 2006-10-22
I've noticed that it boots quite a bit faster. :-k

---

### Post by 3rdalbum on 2006-10-22
I didn't notice a difference. Even the System Monitor on the 386 kernel told me I had 1.2 gigs of RAM, which is correct, but I never tried using it all before installing the k7 one.

---

