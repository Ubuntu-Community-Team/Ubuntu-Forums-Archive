---
title: "doing a &quot;text search&quot; of all text files in a directory"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-06-30
I want to a search through all the text files in one directory. how do i do so in terminal?

---

### Post by woedend on 2006-06-30
are you looking for a search phrase?  If so, use grep.  Say you have all of your text files in /home/text and wanted to find all of the instances of the word ubuntu

cd /home/text
grep ubuntu *



for a phrase, such as I LOVE UBUNTU, use quotation marks
grep "I LOVE UBUNTU" *

the asterisk(*) means search every file in this folder.
HTH let me know if this isnt what you wanted.

---

### Post by hanzj on 2006-06-30
Mr and Mrs. Woedend,
Thanks for your help. How do i search for 2 groups of text. 
So say, I require the words ABCD and XYZ to be in one text file. Can that be done?

---

### Post by woedend on 2006-06-30
good question.  This answer I really haven't ever considered before.  I don't think it could be done using grep unless done with a script, as grep only searches on a line by line basis.

---

### Post by Thundercat on 2006-06-30
Full list of options for grep can be found here:
[http://www.computerhope.com/unix/ugrep.htm](http://www.computerhope.com/unix/ugrep.htm)

I'm no expert but I think the following is correct:

If ABCD has to be before XYZ in the file I think you can just look for ABCD*XYZ
   grep 'ABCD*XYZ' *

If the order doesn't matter, I'm sure there is a more elegant way of doing it, but I would just run 2 grep commands
grep 'ABCD*XYZ' *
grep 'XYZ*ABCD' *

you could pipe the results various ways to get it formatted nicely too

Add: If it does it line by line (which sounds about right) my method wouldn't work, but I guess you could pipe the filename found to a second grep command which would search it for the second string.
I won't attempt to say what that command line would look like, I need a bit of practice with piping first ;)

---

