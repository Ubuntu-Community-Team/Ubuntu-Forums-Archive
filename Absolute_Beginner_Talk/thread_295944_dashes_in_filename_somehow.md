---
title: "dashes in filename somehow"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by ocdude on 2006-11-08
Ok, so I have a file with two dashes (--) at the beginning of the name. I've tried to rename them using mv, but of course, mv tries to interpret the dashes as options. Nautilus doesn't list the file at all, but a shell script I tried to run finds the file and is unable to operate on it.  Any ideas on how I can fix this?](*,)

---

### Post by po0f on 2006-11-08
ocdude,
```
$ mv -- --weirdfile weirdfile
```

---

### Post by ocdude on 2006-11-08
> **po0f said:**
> ocdude,
```
$ mv -- --weirdfile weirdfile
```
Groovy. That was a ridiculously quick response.  Once again, the forums to the rescue.  Thanks!

---

### Post by Arndt on 2006-11-09
> **ocdude said:**
> Ok, so I have a file with two dashes (--) at the beginning of the name. I've tried to rename them using mv, but of course, mv tries to interpret the dashes as options. Nautilus doesn't list the file at all, but a shell script I tried to run finds the file and is unable to operate on it.  Any ideas on how I can fix this?](*,)

You got a good answer, but an even more general one is to use an alternative name for the file. There always is one in Unix. For example,

```
$ ls myfile
myfile
$ ls ./myfile
myfile
$ pwd
/home/yeti
$ ls /home/yeti/myfile
/home/yeti/myfile

```
So

```
$ rm ./--weirdfile
```

would work.

Still another way to get rid of a file with a really weird name, say containing characters you don't even know how to enter, or which will confuse the shell, is using the "interactive" option to 'rm':

```
$ rm -i *
rm: remove regular empty file `INBOX'? n
rm: remove regular empty file `--gråsten'? y

```

---

