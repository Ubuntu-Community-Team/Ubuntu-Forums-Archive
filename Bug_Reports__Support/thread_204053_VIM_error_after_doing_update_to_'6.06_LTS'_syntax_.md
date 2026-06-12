---
title: "VIM error after doing update to '6.06 LTS' syntax coloring fails"
date: 2006-06-26
forum: Bug Reports / Support
---

### Post by movil on 2006-06-26
Just did the upgrade to  '6.06 LTS' which is excellent and I wanted to thank all the people behind ubuntu to make such a great operative system and GUI.

I always use vi for my programing needs, after the upgrade it seems to loose all syntax coloring functionality, here is the error:
[COLOR="Red"]
Error detected while processing /usr/share/vim/vim64/syntax/syntax.vim:
line   42:
E216: No such group or event: filetypedetect BufRead[/COLOR]

To reproduce it:
vi anyfile.txt

and in the vi command type   :syntax on

Does anybody know how to solve this ?

---

### Post by ape on 2006-06-26
Look at this thread:

  [http://www.ubuntuforums.org/showthread.php?t=161862]("http://www.ubuntuforums.org/showthread.php?t=161862")

---

