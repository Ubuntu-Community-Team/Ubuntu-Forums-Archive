---
title: "simple shell script"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by georgepds on 2006-04-15
I need help getting a simple shell script to run

I created the following script in gedit

#!/bin/bash          
echo Hello World 

saved it to aa, amd mad aa executable

it is definately there
george@ubuntu1:~/test$ ls
aa

but when I issue the command, it tells me 
george@ubuntu1:~/test$ aa
bash: aa: command not found

---

### Post by aysiu on 2006-04-15
Type ```
./aa
```

---

### Post by Bloch on 2006-04-15
Hi george;

The shell only executes programs that are in its path. Type $PATH and you'll see which directories are in the path.

You need to type ./aa
where the shell understand the dot to be the present directory. Or else type in the full filename of your script:  /home/~yourname/aa

Or add that directory to your path - but this is only worth doing if you are going to test several scripts

---

### Post by PriceChild on 2006-04-15
Simply typing aa makes linux look in it's own little places for a file installed called aa to run.

As aysiu pointed out, that command will make it execute the file there, as long as you're in that folder.

---

### Post by georgepds on 2006-04-15
Thanks... ./aa did it. I must have looked at a half dozen guides

Now here's the second question. iknow ./ just says look in the current directory. But, weh i issued the command, i was in the same directory as aa. Why did it not find it. I thought the current directory was always the start fo the path

--G

---

### Post by georgepds on 2006-04-15
OK

I get it... just because you are in the directory does not mean that you will look in the directory for things to execute ( that's a dos convention)

--G

---

### Post by Bloch on 2006-04-15
No, it isn't. Type $PATH and that's the only places the shell looks.

Maybe you're thinking of DOS? :-)

It may seem strange that linux is so strict.

---

### Post by Bloch on 2006-04-15
Crossed wires.

---

