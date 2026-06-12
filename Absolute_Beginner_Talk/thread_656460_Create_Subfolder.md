---
title: "Create Subfolder"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by tlf on 2008-01-02
All I need to do is create a new 2008 folder-not a problem.  However, I need to create this empty folder under 200 separate client folders.  I really don't want to open each client and create a new folder 200 times.  Does anyone know of a way that I can add a subfolder to a group of folders?

---

### Post by rich.bradshaw on 2008-01-02
```
for i in $( ls ); do mkdir $i/2008; done
```

---

### Post by ~LoKe on 2008-01-02
> **rich.bradshaw said:**
> for i in $( ls ); do; mkdir $i/2008; done

Simple.  I'm sure I can find a use for this.

---

### Post by llamakc on 2008-01-02
> **rich.bradshaw said:**
> for i in $( ls ); do; mkdir $i/2008; done

That was quick. Mine was a bit longer. I like yours. You'll have to remove the semi-colon after** do** though.

---

### Post by rich.bradshaw on 2008-01-02
Do it in the directory with all the directories you want subdirs in.

as mentioned above, it should read

```
for i in $( ls ); do mkdir $i/2008; done
```

in other words

for all items in this directory make a subdir called 2008

---

### Post by tlf on 2008-01-02
Thank you.  I really am an "absolute beginner", though - Do I enter this command after clicking start > run, or do I need to get to the command prompt?  I know this is obvious to you - sorry!

---

### Post by ~LoKe on 2008-01-02
> [16:10:12 loke]$ for i in $( ls ); do mkdir $i/2008; done
[16:10:20 loke]$ ls
test1  test2  test3  test4  test5  test6  test7  test8  test9
[16:10:24 loke]$ ls test*
test1:
2008

test2:
2008

test3:
2008

test4:
2008

test5:
2008

test6:
2008

test7:
2008

test8:
2008

test9:
2008


Well done, sir.

---

### Post by tlf on 2008-01-02
When I entered the command (I just copied and pasted to the command prompt in the directory that contains the folders I want the subfolder placed in) I get the message "i was unexpected at this time."  ??:confused:

---

### Post by ~LoKe on 2008-01-02
Can you give us an exact copy and paste of what you entered and what it output?  I have a feeling you left something out.

---

### Post by tlf on 2008-01-02
C:\>P:

P:\>chdir CSFA\Clients Current\

P:\CSFA\Clients Current>for i in $( ls ); do mkdir $i/2008; done
i was unexpected at this time.

---

### Post by ~LoKe on 2008-01-02
Err...this is a linux forum, not a windows forum...

---

### Post by llamakc on 2008-01-02
> **tlf said:**
> C:\>P:

P:\>chdir CSFA\Clients Current\

P:\CSFA\Clients Current>for i in $( ls ); do mkdir $i/2008; done
i was unexpected at this time.

You realize that's Windows, right?

---

### Post by rodo-&gt;dave on 2008-01-02
looks like your running windows....

you could install cygwin on it and use the cygwin shell to make it work.

---

### Post by rich.bradshaw on 2008-01-26
After my gem of a oneliner, it wasn't even useful! That's the funniest thing!

---

