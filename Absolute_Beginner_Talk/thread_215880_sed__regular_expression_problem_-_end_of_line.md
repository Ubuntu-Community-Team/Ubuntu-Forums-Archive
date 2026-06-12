---
title: "sed / regular expression problem - end of line"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by andb on 2006-07-14
This has me pulling my hair out...

sed '/2$/p' filename.txt

should display all lines ending with 2, according to every reference Ive encountered. Why though, isnt it? The regular expression is finding nothing. Am I missing something simple here? Does sed now use different regular expressions?
Thanks in advance for help!

the actual command Im trying to run is:
sed 's/^\([a-z]*\) \([0-9]\{1,2\}$\)/\2,\1/' filename.txt
without the $ for the end of line, it works fine, with it, my fields are not reversed...

---

### Post by Paerez on 2006-07-14
try:
sed '/2(.)$/p' filename.txt
maybe there is some whitespace. I know windows sometimes puts a ^M in (at least thats what it shows in vim). Also try opening the file in vim to see if there are weird line ending chars in the file, like ^M.

---

