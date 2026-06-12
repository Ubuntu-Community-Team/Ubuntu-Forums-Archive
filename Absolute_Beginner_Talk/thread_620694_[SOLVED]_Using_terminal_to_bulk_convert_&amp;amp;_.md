---
title: "[SOLVED] Using terminal to bulk convert &amp;amp; rename"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2007-11-22
So I have several videos that I want to convert through the command line on ffmpeg. They are in flv format, I want to convert them to .avi.

I know the command to convert flv to avi through ffmpeg is:

```
ffmpeg -i video.flv video.avi
```

How would I change the code to make it convert about five or six videos from flv to avi, and keep the same filename? Thanks.

---

### Post by PeterJS on 2007-11-22
> **akiratheoni said:**
> So I have several videos that I want to convert through the command line on ffmpeg. They are in flv format, I want to convert them to .avi.

I know the command to convert flv to avi through ffmpeg is:

```
ffmpeg -i video.flv video.avi
```

How would I change the code to make it convert about five or six videos from flv to avi, and keep the same filename? Thanks.

Ask and ye shall receive, I assumed that they're all in the same directory.

```

#!/bin/bash
FLVS=`ls *.flv`

for INFILE in $FLVS
do
	BASE=${INFILE%.*}
	ffmpeg -i $BASE.flv $BASE.avi
done

```

---

### Post by akiratheoni on 2007-11-23
> **PeterJS said:**
> Ask and ye shall receive, I assumed that they're all in the same directory.

```

#!/bin/bash
FLVS=`ls *.flv`

for INFILE in $FLVS
do
	BASE=${INFILE%.*}
	ffmpeg -i $BASE.flv $BASE.avi
done

```

Haha, thanks! Works perfectly.

---

