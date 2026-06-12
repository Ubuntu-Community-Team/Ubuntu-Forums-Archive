---
title: "extracting ecm images"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-08-13
hey i just gownloaded parasite eve, except the cd image was comprressed into this format i had never seen before, with the extension .ecm it also came with some sort of ecm extractor, but its a DOS script. is there any way i can extract this with a linux system? (ps it also came with a c sourcefile of the extractor, can i use that in any way?)

---

### Post by Carlos Yoshio on 2007-12-29
here is what i did:

first i renamed the "unecm.exe" to "unecm.bin" and then i checked the box "Allow executing file as program".

them i put the .ecm file in the same path of unecem.bin file, opened a term and

```

./unecm.bin FILE_NAME.ecm FILE_NAME

```

that was it!

---

