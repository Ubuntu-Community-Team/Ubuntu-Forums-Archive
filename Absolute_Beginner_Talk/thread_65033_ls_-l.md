---
title: "ls -l\ ?"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by YourSurrogateGod on 2005-09-12
I typed into my console the run-of-the-mill "ls -l\", the backslash at the end was added by accident. After I've done that I got another command line this time beginning with the greater than sign ">". What feature/function have I activated?

I checked out the man pages, but that didn't answer my question.

---

### Post by bsussman on 2005-09-12
Continuation - you merely escaped the return  O:)

---

### Post by YourSurrogateGod on 2005-09-12
[QUOTE=bsussman]Continuation - you merely escaped the return  O:)[/QUOTE]
Continuation? Sorry, I don't follow.

---

### Post by bsussman on 2005-09-12
the slash indicated that you weren't done with the command and wanted a fresh line to continue:

 ```
prompt: ls -l\
> filename
``` 

would be the equivalent of

 ```
prompt: ls -l filename
```

---

### Post by YourSurrogateGod on 2005-09-12
[QUOTE=bsussman]the slash indicated that you weren't done with the command and wanted a fresh line to continue:

 ```
prompt: ls -l\
> filename
``` 

would be the equivalent of

 ```
prompt: ls -l filename
```[/QUOTE]
Hmm... I just tried the below. It didn't seem to work too well for directories.
```
C$ ls -l\
>
total 24
drwxr-xr-x  2 andrew andrew 4096 2005-09-07 22:26 doubly_circly_linked_list
drwxr-xr-x  2 andrew andrew 4096 2005-08-18 00:30 make_file_test
drwxr-xr-x  2 andrew andrew 4096 2005-07-14 13:00 singly_linked_list
drwxr-xr-x  3 andrew andrew 4096 2005-07-02 20:26 test
drwxr-xr-x  2 andrew andrew 4096 2005-08-21 19:44 test_debugging
drwxr-xr-x  2 andrew andrew 4096 2005-08-22 23:51 test_debugging2
C$ ls -l test
total 36
drwxr-xr-x  3 andrew andrew  4096 2005-06-02 10:09 further
-rwxr-xr-x  1 andrew andrew 19431 2005-07-02 20:26 test
-rw-r--r--  1 andrew andrew  1137 2005-07-02 20:26 test.c
-rw-r--r--  1 andrew andrew  1202 2005-07-02 20:25 test.c~
-rw-r-----  1 andrew andrew   379 2005-06-10 22:45 test.s
C$ ls -l\
> test
ls: invalid option -- e
Try `ls --help' for more information.
andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C$

```
When I did "ls -l\<enter>" and then <enter> again, it did what "ls -l" would do. But when I did "ls -l\<enter>" and then typed in a folder name and then hit enter, it gave that error saying that there was an ivalid option of e.

---

### Post by cwaldbieser on 2005-09-12
[QUOTE=YourSurrogateGod]Hmm... I just tried the below. It didn't seem to work too well for directories.
```
C$ ls -l\
>
total 24
drwxr-xr-x  2 andrew andrew 4096 2005-09-07 22:26 doubly_circly_linked_list
drwxr-xr-x  2 andrew andrew 4096 2005-08-18 00:30 make_file_test
drwxr-xr-x  2 andrew andrew 4096 2005-07-14 13:00 singly_linked_list
drwxr-xr-x  3 andrew andrew 4096 2005-07-02 20:26 test
drwxr-xr-x  2 andrew andrew 4096 2005-08-21 19:44 test_debugging
drwxr-xr-x  2 andrew andrew 4096 2005-08-22 23:51 test_debugging2
C$ ls -l test
total 36
drwxr-xr-x  3 andrew andrew  4096 2005-06-02 10:09 further
-rwxr-xr-x  1 andrew andrew 19431 2005-07-02 20:26 test
-rw-r--r--  1 andrew andrew  1137 2005-07-02 20:26 test.c
-rw-r--r--  1 andrew andrew  1202 2005-07-02 20:25 test.c~
-rw-r-----  1 andrew andrew   379 2005-06-10 22:45 test.s
C$ ls -l\
> test
ls: invalid option -- e
Try `ls --help' for more information.
andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C$

```
When I did "ls -l\<enter>" and then <enter> again, it did what "ls -l" would do. But when I did "ls -l\<enter>" and then typed in a folder name and then hit enter, it gave that error saying that there was an ivalid option of e.[/QUOTE]
That's because you didn't leave a space.  The shell interpreted it as:
```
$ ls -ltest
``` 
"l" and "t" are valid options for the "ls" command.  "t" is not.  Hit the up arrow for the history after you issue the command, and you will see what it looked like without the continuation.

---

### Post by bsussman on 2005-09-12
if you press your up arrow a couple of times I think you will discover that your continued command was :

 ```
ls -ltest
``` 

e is not a valid option to ls (t is - sort by mod time)

you need a space before the t.  Sorry I forgot it in my example...

corrected example:

 ```
prompt: ls -l \
>test
``` 

or

 ```
prompt: ls -l\
> test
```

---

### Post by YourSurrogateGod on 2005-09-12
Ok, gotcha, thanks guys.

---

