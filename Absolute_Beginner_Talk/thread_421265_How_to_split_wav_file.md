---
title: "How to split wav file?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by elexhobby on 2007-04-24
Hi,

I'm using Ubuntu Dapper. Can somebody please tell me any free software to split an audio wav file?
Thanks.

---

### Post by vanadium on 2007-04-24
In Windows I would have known my way with fast command tools for this, but until then, you can use Audacity. Audacity is a powerfull, multi-track audio editor but quite easy to use.

* First install Audacity using System - Administration - Synaptic
* Load Audacity, then Project - Omport audio - select your WAV
* Now place labels where you want to split the file: place the cursor, press Ctrl+b, optionally type a name for the label. The labels appear on a separate track as small red flags. Do also place a label at the very beginning of the file!
* Now File - Export multiple. In the dialog, set "Split files based on labels" and for "name" check "Numbering consecutively (unless you named your labels). then press Export.

---

### Post by revertex on 2007-05-19
if you have a cue file, you can split pretty easy with cuetools and wavsplit.

use "cuebreakpoints cuefile.cue" to read the tacks length, the use  "wavsplit bigwavefile.wav time1 time2 time3 ..." to split.

---

### Post by luzdegas on 2007-07-08
Hi.
I've tried this solution, and actually works. The problem is that the splitted wav files do not have the appropriate names, they are named as "file1.wav", "file2.wav", etc. Is there a way to preserve the names specified in the cue file?

Thanks,

---

### Post by revertex on 2007-07-08
use easytag to rename, it can read names from a file

---

