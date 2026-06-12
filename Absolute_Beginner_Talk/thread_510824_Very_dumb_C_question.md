---
title: "Very dumb C question"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Ian Toner on 2007-07-27
Starting to get around to teaching myself C, and stuck on something really basic.

 So I've compiled my program, and want to execute.  I've done all this in a subdirectory of my Home directory.  I type the command - tells me bash doesn't know the command. If I preface the command with ./ then it runs.

I know that its something to do with Paths, right?  What should I do (when compiling, or by setting the Paths appropriately) so that I don't have to preface with ./ ?

Thanks for your help

---

### Post by Rocket2DMn on 2007-07-27
That's just the convention for running an executable file.
The . represents current directory, .. is the previous directory, ../.. is 2 steps up the directory tree, and so on and so forth.
Just the way it is :)

---

### Post by bbzbryce on 2007-07-27
> **Ian Toner said:**
> Starting to get around to teaching myself C, and stuck on something really basic.

 So I've compiled my program, and want to execute.  I've done all this in a subdirectory of my Home directory.  I type the command - tells me bash doesn't know the command. If I preface the command with ./ then it runs.

I know that its something to do with Paths, right?  What should I do (when compiling, or by setting the Paths appropriately) so that I don't have to preface with ./ ?

Thanks for your help

Add "." to your path.

```
PATH=$PATH:.
```

However I've heard it's not recommended to do that, though I'm not sure why.

---

### Post by Ian Toner on 2007-07-27
Thanks chaps.  Problem solved.

---

### Post by Carlos Santiago on 2007-07-27
The usual way to do it is to create a dir in your home (ex. ~/bin) and add that dir to your path.
Then when you want to run a program without prefix ./ just place it in your dir.
For testing, just use ./your_compiled_program (ex. ./a.out)

If you still want to add '.' to your path, be sure to add it at the end, for security reasons. 
Imagine that someone can add a binary to the working directory of a program that requires to run some command of the system (ex. sed, cat, tail, whatever)
If you add '.' to the beginning of the path, it would run the intruder program (named as the command) and not the expected => security leak

Is better to get used to ./compiled_program!

---

### Post by rich.bradshaw on 2007-07-27
[http://bashcurescancer.com/never_ever_ever_put_the_cwd_in_path.html](http://bashcurescancer.com/never_ever_ever_put_the_cwd_in_path.html)

Never put . (Current Working Directory) in your path....


Never!


If someone makes a file called ls, for instance in any folder, then you will run that ls instead of the system ls without realising. It's a major security risk, especially when the alternative is so easy to do.

I would just learn to prefix with ./ , or put just the folders you use to program in your path.

---

### Post by johsch on 2007-07-27
To give an explicit example, this is what I do:

Create a directory called linux in you home directory.  Under this linux directory, create diretories bin, src, doc, share, man, etc.  Actually you only need the bin directory at the moment.  Put you executable in the bin directory.  Then add ~/linux/bin to your path.

---

### Post by lamar_air on 2007-07-27
Is there a way to revert back... say you accidentally erased the contents of your env PATH variable...?

---

### Post by LaRoza on 2007-07-27
If you are compiling and running the same  (altered) program, you will actually do little typing, just use the "up" arrow to select previous commands. So the first time you will have to type "gcc whatever -o binary", and then "./binary", but all the times after that, you will only have to press up two or three times to get the commands. Also, in case you didn't know, "clear" will clear the screen, very useful when you get compile time errors, one after another, and the screen becomes a mess of cryptic messages, and you can't see the prompt.

---

### Post by Ian Toner on 2007-07-27
Thanks very much for the above.  Saved from my own stupidity again!

---

### Post by AlexenderReez on 2007-07-27
i use to create executable file for c program like this....

example-->
rename your c text to example.c in your home directory 

then > cc -o example /home/<USERNAME>/example.c

run

> /home/USERNAME/example 

and compile directly for python and perl text....
:)

---

### Post by asmoore82 on 2007-07-27
> **lamar_air said:**
> Is there a way to revert back... say you accidentally erased the contents of your env PATH variable...?

PATH is local to each shell; so if you ruin it you can just open another term.

---

