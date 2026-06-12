---
title: "how do i take space from my windows partition?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-09
I have 4 partitions 2 r used in linux and total 20gig's i have 2 in windows that total more. I have one in windows thats a 7gig. i had originally planned to use it as spare space on windows but now that my wifi is working and i finally have automatix working and all the programs i will ever need except maybe one i will be in ubuntu mostly full time and use windows as my backup. I would like to convert that to a linux part or share it with windows. how can i take that 7 gigs or make it a share drive?

also how do i get my bookmarks from firefox windows and import them to firefox linux? i have the firefox file copied to a windows folder in my documents how do i retrieve the needed info?

thanks in advance.

---

### Post by glotz on 2006-06-09
Unless it's NTFS partition, there's nothing you need to do. If it is NTFS, open partition manager (system > admin > ) and convert it to FAT32.

To import the bookmarks file, open Firefox and goto bookmarks > manage > file > import > from a file > and point to the file.

---

### Post by maddbaron on 2006-06-09
ok i am in the copied firefox directory i made in my documents. which is it? nothing says bookmarks? unless i had to take the bookmarks and export them first?

---

### Post by glotz on 2006-06-09
It's bookmarks.html. Since you say you can't find it, did you take the right folder? [http://www.mozilla.org/support/firefox/profile#locate](http://www.mozilla.org/support/firefox/profile#locate)

(You can also fire up Firefox on windoze and goto bookmarks > manage > file > export to produce the file if the manual way seems complicated.)

---

### Post by grsing on 2006-06-09
It's probably easiest just to export them to somewhere you can find and then just import them in Ubuntu.  As an alternative, google just released a firefox extension that allows you to sync firefox bookmarks (and passwords and history and such if you want, but you can choose) across different computers (your Ubuntu Firefox and your Windows Firefox are essentially different computers for these purposes): [http://www.google.com/tools/firefox/browsersync/index.html](http://www.google.com/tools/firefox/browsersync/index.html)

Might be a good solution if you'll still be using Firefox in Windows (don't know if you need to or not).

---

