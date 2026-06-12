---
title: "sed - bib file, reorder names"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by stilllikepine on 2007-04-17
Hello,
I am having trouble with my bibtex file.
When I downloaded entries from medline they were formatted like: 
Author         = {J. T. Blackburn and B. L. Riemann and J. B. Myers and S. M. Lephart}
However for apacite style to work they need to be like:
Author         = {Blackburn, J. T., and Riemann, B. L. etc}

I am trying to use sed to reorganize the author names

I got as far as this:
sed "s/^\([A-Z]\. \), \([A-Z]\. \), \([A-Z][A-Za-z]*\)/\3 \1 \2/" test.txt

but there seems to be an error

Any help would be appreciated.

James

---

### Post by leibowitz on 2007-04-29
I must say I never used sed before. But I did use regexp. AFAIK you need to transform the (1) to (2), is that right.

(1) Author = {J. T. Blackburn and B. L. Riemann and J. B. Myers and S. M. Lephart}
(2) Author = {Blackburn, J. T., and Riemann, B. L., and Myers, J. B., and Lephart, S. M.}

But what you pasted isn't reflecting that situation.
> sed "s/^\([A-Z]\. \)[COLOR="Red"],[/COLOR] \([A-Z]\. \)[COLOR="Red"],[/COLOR] \([A-Z][A-Za-z]*\)/\3 \1 \2/" test.txt


Try with something more like the following.
> sed "s/^\([A-Z]\.\) \([A-Z]\.\) \([a-Z]*\)/\3, \1 \2/" test.txt

Note: it works only for the first name when I try it. Don't know if it's possible to replace multiple strings in the same line with sed.

---

