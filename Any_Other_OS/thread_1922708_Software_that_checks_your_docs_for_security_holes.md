---
title: "Software that checks your docs for security holes"
date: 2012-02-09
forum: Any Other OS
---

### Post by bob-linux-user on 2012-02-09
Is there a software for Windows and Linux that inspects your documents for sensitive information? For example if I had a word processor document that held the information
"John Smith Bank Account number=1234 5678" then it would flag up a warning.

?

---

### Post by CharlesA on 2012-02-09
I doubt there is a program for doing that and if there was, I would be extremely leery of using it.

You would be better off looking thru your documents manually.

I know Textcrawler can do a mass find, but it won't automatically flag something as "sensitive"

---

### Post by ld.4lpha on 2012-02-19
If you have a collection of strings that you want to flag, it would be pretty easy to write a script that runs through a group of files and searches for each "flag string."  

If you just have one string in particular that you want to search for, grep in Linux will do, and Windows' find cmd searches file contents, I believe.

If you don't know which phrases you want to flag, then you'd probably need to come up with that list first as I don't think there is a pre-written tool for doing what you want.




LD

---

### Post by Dangertux on 2012-02-19
You can use a program like FOCA that extracts metadata and other crucial data from word documents, also I believe Maltego can do limited metadata parsing.

Hopefully this helps.

---

