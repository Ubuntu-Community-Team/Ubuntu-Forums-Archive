---
title: "Search feature not working?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-01-25
My music collection is rather large and when I search through it (using ctrl+f) I never get any results.

How can I get the nautilus search feature working?

---

### Post by Jelmoh on 2008-01-25
Got the exact same problem...
really annoying...

---

### Post by billgoldberg on 2008-01-25
Nobody?

---

### Post by Majorix on 2008-01-25
Well the Nautilus search feat. has some bugs related to it making it next to useless.

You could go with a
[php]sudo updatedb; locate FILENAME_HERE
#Or if the results list is too large, transfer the results into a text file, like this:
locate FILENAME_HERE > results.txt; nano results.txt[/php]

---

### Post by Jelmoh on 2008-01-25
TrackerD (a process that uses way to much memory) is the indexing tool of nautilus am I right?
So if nautilus is next to useless I could just as well disable the indexing service...
Or is TrackerD also used for anything else?

---

### Post by stchman on 2008-01-25
I find the search function under Applications works real well.

Since you have a HUGE music collection just use .mp3 and it will find all teh MP3s in your hdd.

---

### Post by Majorix on 2008-01-25
Not all bugs strike everybody. For me, when I used to use Gnome Ubuntu there was that annoying bug that wouldn't let me search using the default search engine. Instead I learned to use the locate program, which I still use on my Xubuntu (which comes with no other search engines by default).

---

### Post by stchman on 2008-01-27
The search function is under Places--->Search for Files

Works very well.

---

