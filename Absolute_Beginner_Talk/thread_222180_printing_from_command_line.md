---
title: "printing from command line"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-07-24
I wastrying to print documents (pdf, ps or other formats) using the lpr command; I can't do so in Dapper. I used to be able to do so in Breezy. Am I missing something?

When I issue the command

```
lpr filename
```

I get the following error message

lpr: Error - no default destination available.

Any ideas to fix this?

---

### Post by s_h_a_d_o_w_s on 2006-07-24
I think you have to setup a printer in System -> Administration -> Printing

---

### Post by aam-aadmi on 2006-07-24
I have already setup the printer. I can print if I DO NOT use the command line and lpr. For instance, I can print pdf and ps files by opening them and using file  -> print. But I cannot print using the lpr command. I just cannot figure out why.

I read a thread where they had discussed similar problems with relation to Adobe 7.0. I followed the advice and changed mu printing command from /usr/bin/lp to lpr -PPRINTERNAME. By doing this, I am able to print using file -> print. But, I cannot print using lpr.

Any ideas?

---

### Post by ProjectGod on 2006-07-24
hiya... i'm on a windows so i can't give very detailed answers.

hmm try this at the command prompt

lpr [tab] [tab]

tap the tab key twice... you'll get a list of lpr commands that can help you set the default printer.

or you can try

**apropos printer**

and use the utility to set the default printer.

---

### Post by archie.bentonjr on 2006-11-08
I just encountered this problem myself on Edgy... 
the solution is to start up the cups server via your internet browser
(type in the address [http://localhost:631/](http://localhost:631/)) and set your printer up.
I had actually set my printer up via the ubuntu interface and it was
working fine as long as I was in the gui. But... command line printing
was NOT working until I did the cups thing. Interesting. Hope this isn't
too late to help someone else looking for this info via the forum.

---

