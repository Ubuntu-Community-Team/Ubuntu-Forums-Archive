---
title: "sort by name..."
date: 2009-12-07
forum: Assistive Technology &amp; Accessibility
---

### Post by breek on 2009-12-07
xubuntu 9.10

three files named as -> aaa, _boo and _Buu

thunar sort them "the best way"
*_boo _Buu aaa*
(that means it is case insensitive **BUT** keeps special characters)

other programs (gimp, firefox, ls, etc...) sort them like
*aaa _boo _Buu*
(that means it is case insensitive **and ignores special characters**)

i'd like to have everywhere a sorting method like the thunar one... but what can i do? a gconf settings? which one?

---

### Post by GraysonPeddie on 2009-12-08
As far as I've looked in [ls](http://unixhelp.ed.ac.uk/CGI/man-cgi?ls), there isn't a way to not ignore the underscore character, unless you can change the code for ls and compile it from source (or is ls part of the bash shell? ... few minutes later... Nah, guess not. :().

---

### Post by breek on 2009-12-08
depends from LC_COLLATE setting... seems that someone else [had the same issue](http://ubuntuforums.org/showthread.php?t=894734) and didn't find a solution ](*,) :(

---

