---
title: "stop ls scrolling"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by tudedude on 2006-08-03
So I cd and I want to see the files in a directory. I type in ls and a zillion files scroll by, then it stops on the last screenfull of files. How do I get the screen to pause when I do ls so I can see each screen of files?

---

### Post by ciscosurfer on 2006-08-03
Try typing```
ls | less
```that's 'ls', then 'pipe' command (just above the Enter key), and the 'less' command.  Use less to page through your screen.  Use the spacebar to scroll an entire page full, and the Enter key to scroll through line by line.  Hit the 'q' key to quit out and return to your normal console.  Hope this helps! :grin:

---

### Post by wvslkr on 2006-08-03
Try less or more command.  

Check man less and man more.

---

### Post by tudedude on 2006-08-03
Thank you. That did the trick.

---

### Post by wylfing on 2006-08-03
This is the UNIX way -- the output of one tool is used as the input of another tool. Another way to handle this issue, depending on your needs, is something like:
```
ls > foobar
```
Where the output of the 'ls' command is dumped into the file 'foobar'. That way, you can open the 'foobar' file with any text editor and look at the contents.

It is worthwile to learn how to use the pipe and redirect symbols. They are very powerful and can help you do a ton of things very quickly and easily.

---

