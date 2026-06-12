---
title: "grep: changing color"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-02-05
By using the --color option it would highlight the search word.  But how do I change the color?

---

### Post by steve.horsley on 2007-02-05
According to man grep, you set the GREP_COLOR envorinment variabe. 
**export GREP_COLOR=34**

You can find the colour codes at the bottom of this page:
[http://www.termsys.demon.co.uk/vtansi.htm](http://www.termsys.demon.co.uk/vtansi.htm)
and you can combine attributes, e.g. red on cyan like this:
**export GREP_COLOR=31\;46**

---

