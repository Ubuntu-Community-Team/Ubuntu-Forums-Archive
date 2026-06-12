---
title: "Gnuplot LaTeX output"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by dt19 on 2008-02-20
Hey guys, wondering if anyone could help me with a little problem I'm having with plotting data in gnuplot. I can get a graph from my input data (I'm inputting from a file), and I want to put the graph in a report I'm writing in LaTeX. I can make gnuplot give the output in LaTeX code (or whatever you call it) - the only problem is I have 500 data points and the terminal runs out of space i think - it gets to the end of the code, then I scroll back to the beginning to copy it, and I can't see the beginning of the output code. Is there any way to make it so that the terminal output contains more lines? Or have I reached the limit?

---

### Post by finer recliner on 2008-02-20
if i'm understanding the problem correctly, the program you're using spits out a bunch of data to the terminal, and you can't capture all the data withough the terminal running out of room....

the solution, if you're using the normal GNOME terminal, is to do this:

open a terminal
edit > current profile > scrolling tab

increase the scrollback to something larger than 500 (assuming each data point takes up 1 line)


EDIT:
or you can redirect your output of the program to a new file instead of the terminal.
example: the program 'echo' simply prints your input back to the terminal. but we can use the redirect operator in bash (>) to save it to a new file instead.
```

davef@laptop:~$ echo hello world!                              #normal use of echo
hello world!
davef@laptop:~$ echo hello world! > myFile.txt             #redirect output to a new file instead 
davef@laptop:~$ cat myFile.txt                                    #print contents of a file to the terminal
hello world!

```

now you can open myFile.txt (or whatever you named it) with your favorite text editor for easy viewing/modifying.

note that if myFile.txt already exits, this command will overwrite it.

---

### Post by dt19 on 2008-02-20
thanks a lot - solved my problem, and it's a useful thing to know !

---

