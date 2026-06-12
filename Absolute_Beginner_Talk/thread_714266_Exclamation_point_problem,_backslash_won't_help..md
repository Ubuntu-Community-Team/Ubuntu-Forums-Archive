---
title: "Exclamation point problem, backslash won't help."
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by dynamonoid on 2008-03-03
I ran into a problem I apparently can't solve. What's the proper formatting for the following kind of command?

```
 program -a 1 -b target name!! -c 2 
``` 

Everything works fine when the -b flag's content is spelt "normally" e.g:

```
 program -a 1 -b targetname -c 2 
``` 

But it no longer works when the exclamation points come into play. Instead it returns:

```
 bash : !! event not found 
```

I thought adding a backslash after "target name!!" would help, but apparently it has no effect. Help would be very much appreciated.

---

### Post by kaens on 2008-03-03
In bash, !! means "do the previous command entered again."

You need to escape both exclamation points:
```

program -a 1 -b targetname\!\! -c 2

```

Edit: If targetname is one file and it needs that space in between target and name, you need to escape that as well.

---

### Post by bodhi.zazen on 2008-03-03
I can not tell from your post if the problem is with the space in the name or the !!

Try escaping the space with quotes or a \

"target name"

or

target\ name

The ! have a special meaning and I would advise against using them. I am not sure how to escape them, it may be "\!"

---

### Post by dynamonoid on 2008-03-03
Thank you both!

Escaping the empty space and both of the exclamation points did the trick. I used a simple backslash: ```
 program -a 1 -b target\ name\!\! -c 2 
``` and it worked. I hope people will refrain from using !s in filenames from now on. :)

---

### Post by kaens on 2008-03-03
If you use the command line often, it would be very beneficial to you to familiarize yourself with all the shortcuts it provides - it's a very powerful tool.

For instance, Ctrl-r will recursively search through your history for whatever you type (try it!)

^foo^bar will run the last command with bar substituted for foo

There's a whole plethora of convinience, see [this]("http://www.catonmat.net/blog/the-definitive-guide-to-bash-command-line-history/")  and "man bash" for more info.

Edit: oh, and I forgot to mention earlier that instead of using backslashes to escape, you could surround the target name!! with single quotes:

```

program -a 1 -b 'target name!!' -c 2

```

---

### Post by dynamonoid on 2008-03-03
I just finished printing out the cheat sheet. This is good stuff! I'm using the CL more and more these days, and the experience just keeps getting better.
 
I'll try the single quotes next time. Certainly decreases the error rate, especially when there are multiple spaces. 

Thanks again!

---

