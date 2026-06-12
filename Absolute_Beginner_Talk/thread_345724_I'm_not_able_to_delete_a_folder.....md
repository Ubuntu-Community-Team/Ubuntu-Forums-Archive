---
title: "I'm not able to delete a folder...."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by jcroot on 2007-01-24
I'm not able to delete a folder...

I tried to install OpenOffice 2.1 2 weeks ago, everything went fine. I just wonder how can I delete a folder called "ooo" (which contains the office download files from the internet) this folder (ooo) is located in my Trash directory, but I'm not able to delete from there because it says I have no permission.

Can somebody please tell me how can I delete this folder without problem using the command line?

---

### Post by jbayone on 2007-01-24
try typing sudo before the command and path

---

### Post by taurus on 2007-01-24
```
cd ~/.Trash
sudo rm **filename**
```

---

### Post by antiwindows798 on 2007-01-24
> Can somebody please tell me how can I delete this folder without problem using the command line?

Yeah, log in as root but that will require you to allow root to log into Ubuntu.

I advise you nevertheless to use the command line, try something like this:

su - root
rm [path to the folder]

I think it's "rm".

---

### Post by ardchoille42 on 2007-01-24
> **antiwindows798 said:**
> Yeah, log in as root but that will require you to allow root to log into Ubuntu.

I advise you nevertheless to use the command line, try something like this:

su - root
rm [path to the folder]

I think it's "rm".

Removing a folder would be "rm -r folder"

---

### Post by ComplexNumber on 2007-01-24
> **ardchoille42 said:**
> Removing a folder would be "rm -r folder"
is 'rm **-R** <foldername>' :)

---

### Post by ardchoille42 on 2007-01-24
> **ComplexNumber said:**
> is 'rm **-R** <foldername>' :)

rm -r and rm -R are the same thing.. according to man rm, both r and R will work.

---

### Post by ComplexNumber on 2007-01-24
> **ardchoille42 said:**
> rm -r and rm -R are the same thing.. according to man rm, both r and R will work.
yeah, you're right. just tried it. for most command such as chmod, chown, etc, its only the -R options. the rm command is an exception in that both the r and R switches perform the same action.

---

### Post by jcroot on 2007-01-24
I tried this:

cd ~/.Trash

and then:

rm -R <ooo>

But it didn't work I get this error message:

bash: syntax error near unexpected token `newline'

I also tried this:

cd ~/.Trash

and then:

rm -R ooo

Note: Without the <> and I get this error message:

rm: descend into write-protected directory `ooo/RPMS/openoffice.org-core02-2.1.0'?

What I'm doing wrong? The folder is still there...

---

### Post by Phosphoric on 2007-01-25
I think it might be because you don't have write permissions for the file.  Therefore Bash is asking you if it's OK to go down in to the directory and delete.

It's probably waiting for a "y" input......without the quote marks

---

### Post by chiarachiara on 2007-07-01
this comes a bit late, but I had now the same problem and I solved like this:
rm -r "foldername"
try also rm -r ./"foldername"
;)

---

