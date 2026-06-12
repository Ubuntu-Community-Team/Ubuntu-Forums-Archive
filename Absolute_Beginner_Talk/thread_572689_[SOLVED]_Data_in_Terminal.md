---
title: "[SOLVED] Data in Terminal"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Durden10 on 2007-10-10
Hi

I have a simple question: how can I save data displayed in the terminal? Lets say I have to extract data from various files via a shell command, and i want to save it in a txt file or similar. I dont want to do it manually, since it would take too much time.
Thanks,
Durden

---

### Post by llamakc on 2007-10-10
Give an example and we'll show you more than one way to do it.

---

### Post by Durden10 on 2007-10-10
ok, i have a txt file containing several large columns of numbers. After extracting the relevant columns with awk (which are simply displayed in the terminal) I want to quickly save them in another txt File. In order to save time, I'd like to use a batch command for this.
The output-data consists of simple numbers

---

### Post by llamakc on 2007-10-10
Okay.


awk blah bla bhah > data.txt

will redirect the output to the file data.txt. 

awk blah bla blah >> data.txt

will append the output to the existing file data.txt.

---

### Post by kevdog on 2007-10-10
Like piping the output to a file??

Something similar to 

awk '{print $1}' > output.txt

---

### Post by Durden10 on 2007-10-10
That's exactly what I was looking for :)
Thanks!

---

### Post by wormser on 2007-10-10
You can ad a redirect to the end of the command.
```
my command > textfile
```

This will write the data to the file and delete anything already in it.  To append to the document use the redirect twice.
```
my command >> textfile
```

---

### Post by bodhi.zazen on 2007-10-10
A little off topic, but you can also use script :

[http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/](http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/)

[http://www.linux.com/articles/53729](http://www.linux.com/articles/53729)

---

