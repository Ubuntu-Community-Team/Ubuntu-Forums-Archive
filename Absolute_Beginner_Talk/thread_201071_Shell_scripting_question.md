---
title: "Shell scripting question"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by WebDrake on 2006-06-21
Hello all,

I have a program in C, which, when it runs in a shell, engages in an interactive dialogue with the user rather like this:

```

Hello!  Welcome to my program.
Please enter the parameter x: 1.0
Please enter the parameter alpha: 23.5
... etc ...

```

Is it possible to write a shell script to do all this automatically, so I could e.g. type
```

./script [option]

```
and have all the data automatically entered for me?

The aim here is to get something that I can send to a queue on a computing cluster without having to run an interactive job.  I'm not experienced in shell scripting so I thought this would be a nice way to learn, instead of just rewriting the C program.

Many thanks,

    -- Joe

---

### Post by dcstar on 2006-06-21
[QUOTE=WebDrake]Hello all,

I have a program in C, which, when it runs in a shell, engages in an interactive dialogue with the user rather like this:

```

Hello!  Welcome to my program.
Please enter the parameter x: 1.0
Please enter the parameter alpha: 23.5
... etc ...

```

Is it possible to write a shell script to do all this automatically, so I could e.g. type
```

./script [option]

```
and have all the data automatically entered for me?

The aim here is to get something that I can send to a queue on a computing cluster without having to run an interactive job.  I'm not experienced in shell scripting so I thought this would be a nice way to learn, instead of just rewriting the C program.

Many thanks,

    -- Joe[/QUOTE]
Try:
```
./script < input-file
```
Where input file contains:
```
1.0
23.5
```

---

### Post by WebDrake on 2006-06-21
[QUOTE=dcstar]Try:
```
./script < input-file
```
Where input file contains:
```
1.0
23.5
```[/QUOTE]
Wonderful!  Thanks very much for the advice.  It certainly works on my own machine; I'll test it with the queue system and see how it goes.

---

