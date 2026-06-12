---
title: "Bash Scripting (Help Please)"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-05-06
I need some help working with bash scripting.

Ok so I have a bash script (myscript.sh).
```

echo $1
echo $2
echo $*

```

If I where to run:
```
./myscript.sh hello world
```

I would get:
```

hello
world
hello world

```

Ok so what I want to do is allow for any number of options being passed to my script. And then test each individual string.

eg:
```


i=1
while [ $# -gt $i ] ; do

          if [ (the i'th string passed) = $stuff ] ; then
                  command
          fi

          i=$($i+1)

done


```

Any ideas?

Sorry I have tried searching but I'm not sure what I'm asking for!

---

### Post by phossal on 2007-05-06
$@

$* and $@ are very closely related. Bash is well documented, so you will find great descriptions to do what you need to do. In a nutshell though, $* represents all of the arguments in a single string, separated by an IFS, which is usually the comma. $@ is equal to $1, $2, $N, as if all the arguments had been passed separately (as they are).  $# is equal to the number of arguments that were passed.

---

### Post by guysmiley25 on 2007-05-06
Could you please explain? I just gave it a test with echo $@ in my script and it seems to do the same as $*. That is just storing the whole line.

---

### Post by phossal on 2007-05-06
I edited the previous post. Look again.

---

### Post by guysmiley25 on 2007-05-06
So is there away to do what I want?

Can I take $1, $2, ..., $N. for any positive integer N. And process them in a loop to compare each one?

---

### Post by phossal on 2007-05-06
Here is a *working* example:

```
#!/bin/bash

for command in "$@" ; do
	echo "$command"
done
```

---

### Post by guysmiley25 on 2007-05-06
Ah I see.

Thank you very much phossal.

I've been wondering about this for quite some time now, but this was the first time where I really needed to use it. Thanks

---

### Post by phossal on 2007-05-06
Welcome. Thank you for at least replying to the post on Mousepad. It isn't possible to know everything, and I'm quite content knowing nothing more about it. It's a *text editor* that doesn't print. That's all I need to know about *that.* lol 

Cheers.

---

