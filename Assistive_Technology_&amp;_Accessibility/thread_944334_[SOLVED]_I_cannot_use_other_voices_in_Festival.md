---
title: "[SOLVED] I cannot use other voices in Festival"
date: 2008-10-11
forum: Assistive Technology &amp; Accessibility
---

### Post by darrelljon on 2008-10-11
I followed the installation instructions [here]("http://ubuntuforums.org/showthread.php?t=751169") but cannot use other voices in Festival 1.96. Can anyone help?
```
festival> (voice.list)
(us2_mbrola
 us3_mbrola
 us1_mbrola
 rab_diphone
 cmu_us_kal_com_hts
 nitech_us_rms_arctic_hts
 cstr_us_ked_timit_hts
 nitech_us_bdl_arctic_hts
 nitech_us_awb_arctic_hts
 nitech_us_clb_arctic_hts
 nitech_us_jmk_arctic_hts
 nitech_us_slt_arctic_hts)
festival> (voice_us2_mbrola)
SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
closing a file left open: /usr/share/festival/voices/english/us2_mbrola/festvox/us2_mbrola.scm
festival> (voice_nitech_us_rms_arctic_hts)
SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
closing a file left open: /usr/share/festival/voices/us/nitech_us_rms_arctic_hts/festvox/nitech_us_rms_arctic_lexicon.scm
closing a file left open: /usr/share/festival/voices/us/nitech_us_rms_arctic_hts/festvox/nitech_us_rms_arctic_hts.scm
festival>
```Could it be when I am unpacking them many succeed but I also get the following error?
```
./lib/voices/us/nitech_us_slt_arctic_hts/README
./lib/voices/us/nitech_us_slt_arctic_hts/COPYING
tar: lib: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
tar: mbrola_tmp: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

```

---

### Post by darrelljon on 2008-10-19
Okay I installed festlex-cmu and festlex-poslex and it worked.

---

