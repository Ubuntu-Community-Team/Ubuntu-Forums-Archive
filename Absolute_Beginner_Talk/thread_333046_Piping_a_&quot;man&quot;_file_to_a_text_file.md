---
title: "Piping a &quot;man&quot; file to a text file?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-01-06
I know you can pipe "|" terminal output into text files.  I just don't know how.  Can anyone show me how to pipe a command to a text file?  
For bonus points, is it possible to pipe a manual to a text file.  I'm still trying to solve my samba woes and it would help if i could turn "man smb.conf" into a text file that I can hightlight the text on.

---

### Post by meng on 2007-01-06
Rather than using the pipe symbol, you direct the output to somewhere other than standard output.
e.g.
ls -la > directory.txt

man man > man.txt

---

### Post by Wight_Rhino on 2007-01-06
I use;

> man <*command>* | col -b | lpr  

...to print a manpage. I don't see why you couldn't divert it to a text file rather than the printer.

---

### Post by l951b951 on 2007-01-06
> **meng said:**
> Rather than using the pipe symbol, you direct the output to somewhere other than standard output.
e.g.
ls -la > directory.txt

man man > man.txt

This worked! Thanks.  
What is the difference between this ">" and this "|" ?  
What do they do different?

---

### Post by meng on 2007-01-06
As I understand it:
">" directs the output of a command to a file or device
"|" makes the output of one command an argument of the next command

There are situations where either can be used to achieve the same result.

---

