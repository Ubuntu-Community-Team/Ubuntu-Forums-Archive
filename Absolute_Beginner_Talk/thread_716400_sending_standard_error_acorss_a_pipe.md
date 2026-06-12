---
title: "sending standard error acorss a pipe"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by shakejuhn on 2008-03-05
i don't know if this is the correct forum for this but in the terminal im running the command **ls /etc/hosts /etc/h | tr h H **. from what i know you use the "|" character to send across a pipe and that is what i am doing but it does not seem to be working any one have any ideas to this?

---

### Post by jw5801 on 2008-03-05
What are you trying to do? And what output are you getting when you try?

---

### Post by shakejuhn on 2008-03-05
no such file or directory is the output on the screen

---

### Post by niteshifter on 2008-03-05
The error message occurs because this command:
```
ls /etc/hosts /etc/h
```
fails on the **/etc/h** portion. This is not working:
```
ls /etc/h
```
because the folder *h* is not found in folder *etc*

That being said, when one runs the command:
```
ls /etc/hosts /etc/h | tr h H
```
one gets this response:
> dlk@dlk-lt-1420:~$ ls /etc/hosts /etc/h | tr h H
ls: /etc/h: No such file or directory
/etc/Hosts
See that? ls printed /etc/**H**osts. With an upper case h, But look at the ls error output, the word "such". It's still lower case. Running the command without piping to the tr utility gives:
> dlk@dlk-lt-1420:~$ ls /etc/hosts /etc/h
ls: /etc/h: No such file or directory
/etc/hosts

The pipe command ( | ) takes only what a process is writing to standard output and passes it to some other process' standard input.

I take it that the OP wants to know why this is :)

And I'll answer by saying a complete explanation is way, way, way, beyond Abs.Bgnner, repost in the Programming area for that. Suffice to say this:
 "This beaviour is by design"  ;)  (Because it's intuitive to do so.)

Quick answer: Yes, stdout and stderr can be combined and piped.

---

