---
title: "bash filename pattern syntax reference"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by qns8dn3 on 2008-03-31
Is there a comprehensive reference about filename matching patterns syntax? 

Examples
```
echo *.gif
echo [ab]c.gif
echo abc?e.gif
```

Bash manpage is long and i don't know which keyword i should search for.

---

### Post by hyper_ch on 2008-03-31
that's regex what you're looking for...

---

### Post by qns8dn3 on 2008-03-31
Its syntax is not precisely regex that I know.

'a*' matches all filenames that beggins with a. But in regex, 'a*' means 0 or more repetition of 'a'.

---

### Post by mcduck on 2008-03-31
This is what you are looking for:
[http://www.tuxfiles.org/linuxhelp/wildcards.html]("http://www.tuxfiles.org/linuxhelp/wildcards.html")

(first page I got when googling for "bash wildcard")

---

