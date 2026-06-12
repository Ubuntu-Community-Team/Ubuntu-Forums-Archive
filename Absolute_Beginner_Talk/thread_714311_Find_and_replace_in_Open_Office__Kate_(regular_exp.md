---
title: "Find and replace in Open Office / Kate (regular expression question)"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-03-03
I'm trying to replace Word with Open Office.  

What I want to know is, what is the regular expression for a  paragraph mark immediately followed by a character, or set of characters?  How do I show that one immediately follows the other?

Fore example:

[I]and that was the end of the paragraph.[paragraph mark]
[paragraph mark]
And now the new paragraph starts.[/I]

So, what is the regular express for:

[I] [paragraph mark]
And now[/I]

Thanks.

---

### Post by RequinB4 on 2008-03-03
Use the $ character to find a paragraph mark.  You must have regular expressions turned on.  You may use, for instance, randomstring$ to search for randomterm[paragraph mark].

Note that $randomterm will NOT work.  the ^randomtem regular expression will search for randomterm at the beginning of a paragraph, after the paragraph mark.  However, the found term will NOT include the paragraph mark.

---

### Post by Shiseiji on 2008-03-09
Thanks so much for this posting! I have been using OO off and on for years now, slowly making the transition from MS. The use of "$" for a paragraph marker isn't in the help and this was the 3rd listing or so on a Google. Do you happen to know the string for a hard return?

TIA

Ron

---

