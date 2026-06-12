---
title: "[SOLVED] Reading a file and storing its variables in Bash"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-09-05
I have a file with the following in it, 
```

partname=xxxxx
partnumber=xx-xx-xxx
quan=xxxx

```

How can I read  these variables with another program,  and temportary store them so that I may print them to a list? 
Thanks

---

### Post by ericmitz on 2007-09-05
> **uclalinux said:**
> I have a file with the following in it, 
```

partname=xxxxx
partnumber=xx-xx-xxx
quan=xxxx

```

How can I read  these variables with another program,  and temportary store them so that I may print them to a list? 
Thanks

What kind of "another program"? If you mean another Bash script, you can just do

```

#!/bin/bash

. myfile

echo "$partname"

...rest of your code...

```

Obviously you dont need the 'echo', but its there to show that you can use the variables just like any other
If you are trying to import the variables into another language..you will have to give that information if you want help

---

### Post by uclalinux on 2007-09-05
This other program is going to real alot of these files containting the 3 variables and print variouse master list. this is for an invintory program i am working on I am an M.E. so programming is new for me.

---

### Post by uclalinux on 2007-09-05
I wrote this but it will not work, I don't think I am reading the file into this program write

```
#!/bin/bash
~/05-01-223 ## file name in dir

echo "$partname"
```

---

### Post by asmoore82 on 2007-09-05
also the format of the file with the variables in it will have to be slightly different
depending on what will be reading it ...
in the case of BASH... all of the data to be stored in the variables should be in
quotation marks at the very least and maybe even in single quotes.

```
#variables_file

right="Bash likes this."
wrong=This loose assignment will cause bugs.
good='This would work too.'
```

```
**asmoore@asmoore-laptop:~/jail$** . variables_file 
bash: loose: command not found
**asmoore@asmoore-laptop:~/jail$** echo $write

**asmoore@asmoore-laptop:~/jail$** echo $right
Bash likes this.
**asmoore@asmoore-laptop:~/jail$** echo $wrong

**asmoore@asmoore-laptop:~/jail$** echo $good
This would work too.
```

---

### Post by uclalinux on 2007-09-05
Thank you ericmitz and asmoore82 I got it working,

I know there are alot of howto web sites for script writing but can you recommend any goodones for begginers.

Thanks.

---

