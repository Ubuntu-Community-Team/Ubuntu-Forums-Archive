---
title: "how to split a file?"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by vipin on 2006-02-20
Please help me with a way to split file in ubuntu linux!



I am not been able to understand the command which will do the splitting of the file.



Here is the case:-



==>Suppose there is a file named ABC.EXE at my desktop whose size is 100 MB. I want to split it into sizes of 10 MB. So what will be the required command for it?







Also, what will be the command for joining it?



please give me the exact command.



thanx in advance.

---

### Post by zugvogel on 2006-02-20
I had a quick look on google, and found this:

[http://www.cgi-interactive-uk.com/splitting_large_files.html](http://www.cgi-interactive-uk.com/splitting_large_files.html)

I hope this helps. If you have trouble, let us know.

---

### Post by vipin on 2006-02-20
well i got one command from here:-

http://www.computerhope.com/unix/usplit.htm'

Now I am able to split but not able to join. 


I am not able to use that TAR command. I don't know why?

---

### Post by az on 2006-02-20
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Split_and_Reassemble_files)


to reassemble, use cat

cat ABC*.* > reassembled.exe

---

