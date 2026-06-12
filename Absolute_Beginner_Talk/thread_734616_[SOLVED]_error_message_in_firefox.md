---
title: "[SOLVED] error message in firefox"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-24
Since installing the 64 bit Gutsy, Firefox is showing me this error when I try to bookmark a page

XML Parsing Error: not well-formed
Location: chrome://browser/content/bookmarks/addBookmark2.xul
Line Number 1, Column 9:       </treeitem>
--------^

Anyone able to help me with resolving this one?

---

### Post by scragar on 2008-03-24
who was it I told that having firefox store bookmarks as xml would come back to haunt them?

run
```
cat ~/.mozilla/firefox/profiles.ini
```
and note the  last line( something like:
```
Path=d8xx9y0e.default
```
find that folder in ~/.mozilla/firefox/ and post the contents of your bookmarks.html file in that folder.

---

### Post by munkyeetr on 2008-03-24
If you read this post: [http://ubuntuforums.org/archive/index.php/t-21999.html](http://ubuntuforums.org/archive/index.php/t-21999.html)

It says to remove the following file from your firefox configuration: 

~/.mozilla/firefox/*/XUL.mfasl

This should fix your problem and the file will be automatically recreated next time you open firefox.

---

### Post by tropdoug on 2008-03-25
Thanks guys, 

I deleted that file 'XUL.mfasl' and that fixed the issue. 

so problem seems to be solved much obliged

---

