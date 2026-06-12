---
title: "rmdir command"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-14
if i use above command rmdir but there something in dir then it will not remove what is the correct command to remove everything

lex1
l

---

### Post by DirtDawg on 2006-07-14
I beleive it's 
```
rmdir -r <directoryname>
```

This command removes the directory plus everything inside the directory, which is what I believe you want.

---

### Post by lex1 on 2006-07-14
ok tried rmdir -r


root@lex1:/home/lex1# rmdir -r .wine 
rmdir: invalid option -- r
Try `rmdir --help' for more information.

any other suggestions please


lex1

---

### Post by verbatim210 on 2006-07-14
rm -r directoryname
not 
rm**dir** -r directory name

verbatim

---

### Post by mlind on 2006-07-14
```

rm **-rf** *directory*

```

be careful though..

---

### Post by DirtDawg on 2006-07-14
> **verbatim210 said:**
> rm -r directoryname
not 
rm**dir** -r directory name

verbatim

oops! :)

---

### Post by wildseven on 2006-07-14
hmm, I am a little confused. I was under the impression the -f **forced** deleting directories. I thought that it was needed. I also beleived that the -r **recursive** deleted everything inside. So why is it a threat to do rm -rf <directory>?
I thought it was supposed to be that way. I know that:
```
 #: rm -rf / 
```

is very dangerous though. Have I been doing things wrong?

---

### Post by muep on 2006-07-14
The -f overrides any write-only files there probably are in the filesystem. Otherwise it would at least have the user confirm every read-only file.

---

### Post by autocrosser on 2006-07-14
That would delete your root directory---If you like the thrill of reinstalling your OS---well, you get my point.
 
In any case, use commands that rm -r or rm -rf only if you REALLY need them--
 
I enabled my root user account so I can GUI thru my directories--that way I KNOW EXACTLY what I am deleting (note: enabling the root user is kind'a "frowned" upon--I have used Linux & UNIX for 15+years & know what you should do & NOT DO--I use within very narrow limits for very specific work--you can DAMAGE your system way beyond repair with the root user!!!!!!!!!)
 
If you "want" to enable root user there are several good guides available--I will not go thru the process here.

---

### Post by DirtDawg on 2006-07-14
It seems to me like "rm -r" would suffice for most cases. Just use "rm -rf" when needed and only when you know *exactly* what you're deleting.

I mean, "rm -r" couldn't remove your home directory, but "rm -rf" could, no?

---

### Post by richardward101 on 2006-07-14
instead of enabling root account to browse with a gui, why not just *sudo nautilus*?

---

### Post by Brunellus on 2006-07-14
> **richardward101 said:**
> instead of enabling root account to browse with a gui, why not just *sudo nautilus*?
or indeed

```
gksudo nautilus
```

---

### Post by autocrosser on 2006-07-14
Yes--I've done sudo nautilus many times--I guess it's old habits that die hard--I've had a root account in every UNIX & Linux system I've set-up--goes back to the days that it was the only way you could do system admin;)

---

