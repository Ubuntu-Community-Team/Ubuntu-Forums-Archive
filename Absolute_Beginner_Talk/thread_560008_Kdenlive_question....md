---
title: "Kdenlive question..."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-09-25
What formats can you save the finished video to? Can you save to a universal format?

---

### Post by eggdeng on 2007-09-26
[http://www.kdenlive.org/features.php]("http://www.kdenlive.org/features.php") mentions mpeg, dv, vob, realvideo, flash, theora, wav, mp3, xvid, quicktime. Just about every player out there will reproduce mpeg 1 or 2.

---

### Post by mramsey on 2007-09-26
that is correct according to the kdenlive site.  when I use the app I don't  have yhe option to export to those formats.  the only option seem to be to burn a dvd. am I missing something?

---

### Post by eggdeng on 2007-09-26
I really don't know a lot about this but Kdenlive seems to use ffmpeg for exporting so ```
ffmpeg -formats
``` should tell you what file formats are supported. How did you install it? Maybe it doesn't know where ffmpeg is. Incidentally, I use Kino (from the repos) for editing.

---

### Post by mramsey on 2007-09-26
:oops: OK call me an idiot....I should have dug a little deeper before making my post.  I was selecting to export to DVD.  The correct one is export timeline (I think the name of that is a little misleading) Any thanks for the effort!

---

### Post by eggdeng on 2007-09-26
:lolflag: Happens to everyone.

---

### Post by theophiles on 2008-05-09
> **mramsey said:**
> :oops: OK call me an idiot....I should have dug a little deeper before making my post.  I was selecting to export to DVD.  The correct one is export timeline (I think the name of that is a little misleading) Any thanks for the effort!

Yes, the title IS misleading, but I feel honor bound to mention that the reason I didn't have to ask this question myself is because you did. Everyone's questions help everyone else and that is what I love about Ubuntu.

---

