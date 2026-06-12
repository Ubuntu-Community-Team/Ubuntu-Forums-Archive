---
title: "how can I make iconv write output to the same file?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-08-15
I have several files, wich I want to convert with iconv. Can I make iconv write output to the same file? Or at least make it write output to a non-created before file?

---

### Post by Hospadar on 2007-08-15
What exactly do you want to do? do you want to convert and concatenate a group of text files in one sweep? If that's the case, you could do something like ```
iconv [arguments] [files]
cat [files] >> concat_file.txt 
```
If you want to also see the output of cat, do:
```
cat [files] concat_file.txt | tee concat_file.txt 
```

If you want to pipe the output to a file that already exists without overwriting the file (appends output to the end of the file) you could do something like```
iconv [arguments] >> output_file.txt
```
the double angle brackets prevent file overwrite.

These output files don't need to be created ahead of time

---

### Post by netimen on 2007-08-15
No, I want to convert a file and write the output to the same file. So if I have 1.txt in cp1251 I want to get 1.txt in UTF-8. If I simple type

```
iconv -f cp1251 -t UTF-8 1.txt -o 1.txt 
```

I get 'permission deined'. Also I get this if I type

```
iconv -f cp1251 -t UTF-8 1.txt -o 2.txt 
```

and 2.txt doesn't already exist.

---

