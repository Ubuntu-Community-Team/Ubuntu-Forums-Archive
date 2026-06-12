---
title: "awk beginner q."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by chelfc on 2008-03-19
I have an awk script (starting with #!/bin/awk -f)

anyway how would I be able to filter out each line and print only those that do not begin with say, 811. So anything that starts with 811, likw 8112412, that line will not be printed. I tried an if statement testing 811* but I get a syntax error

---

### Post by glennric on 2008-03-19
What is an awk script?  awk is not a shell as you are seeming to indicate with #!/bin/awk.

---

### Post by chelfc on 2008-03-19
ooh. i've seen scripts online that say #!/bin/awk

and i've also read tutorials that tell me to run files like so

awk -f <source file> <input file>

so i assumed that it was an awk script.

---

### Post by glennric on 2008-03-19
awk is a pattern scanning and processing language, not a shell.  Usually a script will start with
#!/bin/sh
All this does is determines what type of file the script file is.  It doesn't affect execution of the script.  If you post the contents of your script file I may be able to help you with getting it to work.

---

### Post by Oldsoldier2003 on 2008-03-19
> **glennric said:**
> awk is a pattern scanning and processing language, not a shell.  Usually a script will start with
#!/bin/sh
All this does is determines what type of file the script file is.  It doesn't affect execution of the script.  If you post the contents of your script file I may be able to help you with getting it to work.

+1

Often people don't know that shabang - shell line means! They just see it in use , but don't know its there to pass the script to a specific interpreter.

---

### Post by chelfc on 2008-03-19
> **glennric said:**
> awk is a pattern scanning and processing language, not a shell.  Usually a script will start with
#!/bin/sh
All this does is determines what type of file the script file is.  It doesn't affect execution of the script.  If you post the contents of your script file I may be able to help you with getting it to work.

this  is what I initially did, 
```
#! /bin/awk -f
{ if ($0 != /811*/) print $0}

```

i ran it using the awk - <source file> <inputfile> but it gives me a syntax error pointing to the closing bracket for the if statement

---

### Post by chelfc on 2008-03-19
so would I do something along the lines of

```

#!/bin/bash

awk {if ($0 != /811*/) print $0

```

would the $0 be read as the filename as it would normally do in a bash shell, or would it still just refer to the current line? Also, is that the correct way to test if the line starts with 811?

---

### Post by glennric on 2008-03-19
I think what you are looking for is
```
#!/bin/bash
awk '!/811.*/' $1

```
Then 
```
chmod +x script-name
```
Execute it with 
```
./script-name file-to-be-processed
```

---

