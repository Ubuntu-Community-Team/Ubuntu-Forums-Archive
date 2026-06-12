---
title: "No sound when playing 3GP"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2008-02-22
INo sound when playing 3GP ext. can someone help

---

### Post by luisromangz on 2008-02-22
ffmpeg can be compiled with or without amr audio codec support. For legal reasons, ubuntu's ffmpeg is compiled without amr support, and that's the audio format that 3gp uses. 

I usually transcodify 3gp files into mpeg using Mobile Media Converter, which includes it's own ffmpeg compiled with amr support. You can try that.

---

### Post by andrew.46 on 2008-02-25
Hi,

 You need to compile your application against amr. Directions for compiling amr itself here:

[http://ubuntuforums.org/showpost.php?p=4378414&postcount=195](http://ubuntuforums.org/showpost.php?p=4378414&postcount=195)

          Andrew

---

