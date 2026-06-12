---
title: "mc file extensions question"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-13
i want to associate .html files so that, when being in MC and clicking on a html file it will automatically open in firefox. with this syntax 
> 
# html
regex/\.([hH][tT][mM][lL]?)$
        Open=firefox %f
        #Open=run-mailcap text/html:%f
        #Open=(if test -n "" && test -n "$DISPLAY"; then ( file://%d/%p &) 1>&2;
        View=%view firefox %f

it opens but only if a i have firefox allready running. if i don't have a firefox running, nothing happens and the page is not displayed. i guess the syntax is wrong in the "view"(the last one) line but where do i go wrong?

---

