---
title: "Reiser"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Smika on 2006-04-12
When i install Linux ubuntu it has the file systems ext3. I heard that reiser is the best file system. But can someone tell me why i should use reiser?

Thanks,

Smika

---

### Post by pbaehr on 2006-04-12
They're pretty similar. ReiserFS has a higher maximum volume size as well as a higher maximum file size so if your volume is going to be HUGE ReiserFS has some advantages.

For an pretty good comparison in features between every file system you can think of this document may help you:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

You'll have to be more tech saavy than me to understand parts of it, though.

---

### Post by Smika on 2006-04-12
Thanks for this information. It will helps me a lot and i hope other users too.

---

### Post by pbaehr on 2006-04-12
On the editorial side, I've been using ext3 for a while and never had any complaints. Though, I've never tried ReiserFS so take that for what it's worth.

---

### Post by steve.horsley on 2006-04-12
[QUOTE=pbaehr]On the editorial side, I've been using ext3 for a while and never had any complaints. Though, I've never tried ReiserFS so take that for what it's worth.[/QUOTE]
Equally, I have been using Reiser for years and never had any complaints.

I tried ext3 for a while, but I thought that fsck on reiser seemed faster - that's the only difference I could see. I stick with reiser purely because it's familiar and trusted to me (I began with SuSE which defaults to Reiser).

---

### Post by pbaehr on 2006-04-12
One article that I looked at did mention that Reiser was "fast and stable" but it didn't make it clear whether or not it was comparing it to ext3 or just praising it in general so I omitted that from my comment, but I'm not suprised that you mention it being faster on fsck.

---

