---
title: "ask simple shell script about number type"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by jualansandal on 2008-03-04
I have this script

```
for fname in *
do
echo "$fname"
i=`expr $i + $n`
done
echo "$i"
```


in this line code
```
i=`expr $i + $n`
```
why it always issues error : 
"expr : syntax error"

anybody know why, thanks

---

### Post by lloyd_b on 2008-03-04
What exactly is "$n"?  What I suspect is happening is that you're calling the "expr" command with one or more null parameters, so it's trying to execute 
```
expr 5 +
```
or something similiar.

Suggestion - Add the line highlighted below so you can see what's happening:
```
echo "$fname"
**echo "executing: expr $i + $n"**
i=`expr $i + $n`
```

One suggestion: assuming you're using bash, it's simpler to use the built in arithmetic:
```
i=$((i + n))
```
than to call the "expr" command.  It's also a lot more forgiving - a null variable is treated as zero, rather than causing an error.

Lloyd B.

---

### Post by jualansandal on 2008-03-04
-- sorry , just use bash

---

### Post by erginemr on 2008-03-04
Are you trying to enumerate a bunch of files (i.e. give them numbers in order)?

---

### Post by jualansandal on 2008-03-04
actually i am confusing for this command
```

ftp.....
quote....
.........
.......
for (( i = 0 ; i < ${#FNAMES[@]} ; i++ ))
do
  echo ${FNAMES[$i]}
done
............
quit........

```

could not be executed within ftp command part in script, the error is :
```

We only support non-print format, sorry.
?Invalid command
?Invalid command
?Invalid command

```

---

