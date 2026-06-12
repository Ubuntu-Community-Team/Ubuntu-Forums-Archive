---
title: "surfing robot"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by pandanuma on 2007-08-06
looking for a web crawling program that would imitate the average persons surfing habits.

perhaps with the ability to be 'trained' to surf like you do.
it would be interesting to set it loose and see where it goes.

otherwise, I am looking for a basic web robot that I could instruct to do my searches. (not looking for web search 'service providers')

a perl program would be nice, I might even be able to tweak it myself.

---

### Post by finer recliner on 2007-08-06
for a *basic* web crawler, this wouldnt be too difficult to implement on your own (i assume you have some programming knowledge already). 

use a system call to call wget which will download a seeded webpage. parse the page's source code for any <a href="...">...</a> tags. use wget to download that page and repeat.

---

