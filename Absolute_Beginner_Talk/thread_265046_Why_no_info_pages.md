---
title: "Why no info pages?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Charles Hand on 2006-09-25
I'm sure this must be posted somewhere, but I haven't found it. 

Why do ubuntu packages not come with info pages, nor do the info pages seem to be available from the official and community repositories?

Many man pages refer me to info, but info simply displays the man page.

---

### Post by caimex on 2006-09-25
Check the google pages ;)

---

### Post by Chandon on 2006-10-21
Well, this is a pretty lame post. Especially since it's the first thing that comes up in a google search looking for the answer to the question.

I tend to give out RTFM and JFGI answers myself, but "info" isn't exactly the most useful search term...

---

### Post by fatsheep on 2006-10-21
info pages work fine for me...  The are sometimes similar to the man pages but usually go into greater depth and explain more fully the usage of the program.  Can you give me an example of an info page that simply displays the man page?

---

### Post by CatKiller on 2006-10-22
I think that info displays the man page if an info page isn't available. It depends on whether that project's package includes the info documentation as well as the man pages.

And Chandon, I think caimex was suggesting that the OP used Google to find help **instead of** the info pages, rather than suggesting that the OP uses Google to find out why he doesn't have info documentation.

---

### Post by Charles Hand on 2006-10-26
> **CatKiller said:**
> I think that info displays the man page if an info page isn't available. It depends on whether that project's package includes the info documentation as well as the man pages.

And Chandon, I think caimex was suggesting that the OP used Google to find help **instead of** the info pages, rather than suggesting that the OP uses Google to find out why he doesn't have info documentation.

I can't seem to find any examples right now. The man pages I'm talking about are generally brief, and refer you to the info pages for more information. So presumably the packages have info pages because the man pages refer to them. But info displays the man page only, indicating that the package installed through the repo didn't include info pages.

In the old days, when you found a man page like that, you could actually get more information through info. Info was a command-line/keyboard interface using emacs key bindings, so it was extremely efficient when in command-line mode to open an info page, locate the information you wanted, and continue without shifting to a graphical environemnt and back again.

It is certainly true that virtually everything is on the web now, which would explain a decline in the use of info. Except in those cases where the man page is brief and explicitly refers to info. 

I was only asking whether there is another repo I should be using, or some procedure to get the info pages for packages which indicate that they have info pages.

I really don't need to be flamed or called an idiot or told to read the manual. I would prefer, if you want to convey such a message to me, that you simply don't.

---

### Post by skymt on 2006-10-26
Info manuals may be in the -doc package associated with a program.

---

### Post by berapp on 2006-11-09
I too, noticed the lack of info pages.  A good example is the info page for uniq.

On an old RedHat box I have "man uniq" says this:

NAME
       uniq - remove duplicate lines from a sorted file

SYNOPSIS
       uniq [OPTION]... [INPUT [OUTPUT]]

DESCRIPTION
       Discard all but one of successive identical lines from INPUT (or standard input), writing to OUTPUT (or standard output).

[...]
**truncated**

And "info uniq" says this:

`uniq': Uniquify files
======================

   `uniq' writes the unique lines in the given `input', or standard
input if nothing is given or for an INPUT name of `-'.  Synopsis:

     uniq [OPTION]... [INPUT [OUTPUT]]

   By default, `uniq' prints the unique lines in a sorted file, i.e.,
discards all but one of identical successive lines.  Optionally, it can
instead show only lines that appear exactly once, or lines that appear
more than once.

   The input must be sorted.  If your input is not sorted, perhaps you
want to use `sort -u'.
[...]
**truncated**

The info page is much more verbose.

However, on my Ubuntu systems, "info uniq" says that it is referring to the man page:
File: *manpages*,  Node: uniq,  Up: (dir)

I hope this helps, someone to help us.  I'd like to find the info pages.
And I have to agree, searching for "missing ubuntu info pages" in Google useless.

---

### Post by hovzio on 2008-03-05
Im not finding any info pages either.I know there are certain commands for which there are no info pages but im sure, there seem to be none available.the shell always offers me a man page even if i type "info info" ill get the same as with man info.im pretty new to linux and still have a lot to learn so im really not sure what the problem is.would appreciate any help.

---

