---
title: "Help with command line...add file extension to group of files."
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Pianoman72 on 2006-11-08
I have a folder full of pdf files that do not have the ".pdf" extension tag at the end of the filename.

I like to have the extension on things just for compatibility reasons.

What syntax should I use to rename/add a ".pdf" to all of the files in this folder?  I'd like to preserve the date/time stamp on the files if possible, too.

Thanks.

I tried mv "*" "*.pdf"
but it didn't find any files to modify.

---

### Post by underdog on 2006-11-08
Look up the "rename" command. Seems to do what you want it to.

---

### Post by skymt on 2006-11-08
rename would do the job. A loop would also work:```
for i in * ; do mv $i ${i}.pdf ; done
```

---

### Post by Pianoman72 on 2006-11-08
This is a little more complicated than I thought it would be...

Problem is that I am at work and I'm on OSX.  I don't have the rename command and skymt - your suggestion retuned "for : command not found."

I found this example which converts foo.* to bar.*

ls -d *.foo | sed -e 's/.*/mv & &/' -e 's/foo$/bar/' | sh

I'm trying to modify this example to fit my needs, but I don't understand how it works enough to modify it on my own.

I don't have a problem reading man pages but usually I need more than one example in order to pick apart the correct syntax.

Thanks.

---

### Post by skymt on 2006-11-08
This should work (based on your example and one in the xargs man page):```
ls * | xargs -I '{}' mv '{}' '{}'.pdf
```xargs is confusing and rather complex, but it comes in handy once in a while.

But the for loop should have worked also. I tested it, and it works in zsh, bash, and even the minimalistic dash. Any shell that doesn't understand a for loop is seriously broken.

By the way, I hope you have a copy of these PDFs somewhere. When you're testing batch commands like these, something something goes wrong. I don't want you to lose anything because of a missing ' or something stupid like that.

---

