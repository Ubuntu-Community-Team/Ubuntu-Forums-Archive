---
title: "html printing problems"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2008-02-29
Though I can pretty well print out documents in pdf, while I try an html document, such as this page[http://web.usna.navy.mil/~wdj/tonybook/gpthry/node65.html]("http://web.usna.navy.mil/~wdj/tonybook/gpthry/node65.html"), the whole page is not printed out (this problem was not there a month ago); and in the special case, if I choose (in firefox) file>print>pages from 1 to 1, it gives only Theorem 11.3.3 and the print looks like deviated from the centre. In the print preview option, there is no indication of the problem, it occures only when I give the print command.

 Moreover, in my windows XP, html printing are done without problem, and in the print preview there is scale option as well, which I miss in Ubuntu.

What can be done?

Oh, by the way, I had an opera installed in Ubuntu, and that too had the same issue.

---

### Post by sauravbhaumik on 2008-02-29
Hello, isn't there anyone kind enough to help me out?

---

### Post by crf on 2008-03-01
hi, I tried to print it. But I got an error in ghostscript :-( it normally works well with text or images though.
I'm using firefox3 Beta.
Some printing things changed in this newer version of firefox. You may wish to try it. I think you may install it from synaptic, or you can download it from mozilla.org.

You can turn cups debug logging on using the cups web interface, or perhaps from the printing app in the system menu-->Administration. The log is in /var/log.

---

### Post by sauravbhaumik on 2008-03-01
I opened kpdf, and opened a pdf file in it, and then changed the printing properties in that and saved it. Since the printing has been almost normal. The only problem that sustains is that the upper margin is too less. By the way, the scale option in print preview doesn't work in Ubuntu, whether 100% or 30% the picture is the same.  And in WinXP, the print preview can produce print out, in Ubuntu, it can't ](*,)

---

### Post by crf on 2008-03-01
I tried printing to pdf, and it only printed the first page too.

---

