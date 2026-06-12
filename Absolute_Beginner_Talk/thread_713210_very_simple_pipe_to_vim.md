---
title: "very simple pipe to vim"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by PGScooter on 2008-03-02
Hi,
I searched online for the answer to this simple questions, but perhaps it is so simple that there is not much on it. I would like to do something similar to ```
ls|less
``` but with vim.

How can I pipe the output of a command to vim, so that vim either:
1. just opens with the output of the command as text
2. creates a file names test.txt and opens with the output of the command.

```

roddick@Happy:~$ ls|vim test.txt
Vim: Warning: Input is not from a terminal
Vim: Error reading input, exiting...
Vim: preserving files...
Vim: Finished.

```

thanks!

---

### Post by glennric on 2008-03-02
Type
```
ls | vim -
```
to save the file as test.txt in vim type
```
:w test.txt
```

---

### Post by PGScooter on 2008-03-02
thanks glennric, what does the - stand for or mean? is it particular to vim or are the uses with other programs/commands?

---

### Post by glennric on 2008-03-02
The - means read from stdin.  This is somewhat particular to vim, although there are other programs that us it to mean the same thing.  Not all programs do however.

---

### Post by PGScooter on 2008-03-02
thanks for the explanation

---

### Post by drubin on 2008-03-02
This is to answer your second point.
```
ls -l >test.txt
```

That code  writes the out put of the command ls to a file called test.txt.

```
>
```
That is used to re-direct the output. 

This doesn't exactly answer you question but thought you might like to know

---

### Post by Oldsoldier2003 on 2008-03-02
> **rubinboy said:**
> This is to answer your second point.
```
ls -l >test.txt
```

That code  writes the out put of the command ls to a file called test.txt.

```
>
```
That is used to re-direct the output. 

This doesn't exactly answer you question but thought you might like to know
and :
```
>>
``` redirects the output in append mode instead of overwriting the file. (another good thing to know)

---

### Post by PGScooter on 2008-03-03
thanks for the extra tips

---

