---
title: "soundconvertor not working"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-01-27
i need to convert some wavs into mp3 or ogg, however when i add the wav files to the list, it throws me a generic error (see screenshot). how can i fix this?

---

### Post by blueridgedog on 2008-01-27
Perhaps you could try it from the command line and see if there is a more descriptive error:

```
cd /to/path/with/your/files
lame mywav.wav mymp3.mp3
```

lame will encode a new file based on the input file.   In the example above the wav file is called mywav.wav and the mp3 is called mymp3.mp3.

---

### Post by rkakkar on 2008-01-27
it says "warning: corrupt or unsupported wave format"

will try it on my windows machine and check if it converts there...

---

