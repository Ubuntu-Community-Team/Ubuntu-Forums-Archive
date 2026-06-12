---
title: "Search through all files in one directory recursively"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Barleyman on 2007-08-28
Hi All,

Using Feisty and looking for a tool (command line or other) to search through all files in a specific directory.

I tried google desktop search, but was unable to specify which directory I want to search in.  I have tracker installed currently, but it still searches my entire home directory.  

I realize I can change the default directory, but I have many projects in ~/rails that I want to search through per project.  i.e sometimes I want to search all files in rails/project1 for any file containing user_tool.rb, and next I want to search only in rails/project2

Thanks in advance for any help.

---

### Post by dwhitney67 on 2007-08-28
Use this command:

[FONT="Courier New"]$ find *dir* -exec grep *pattern* {} \; -print[/FONT]

where *dir* is the directory from where to start searching, and *pattern* is the word you are looking for (which can be enclosed in double-quotes for strings).

For example:

[FONT="Courier New"]$ find /home/foo/source -name '*.cpp' -exec grep "hello world" {} \; -print[/FONT]

---

### Post by dwhitney67 on 2007-08-28
> **dwhitney67 said:**
> Use this command:

[FONT="Courier New"]$ find *dir* -exec grep *pattern* {} \; -print[/FONT]

where *dir* is the directory from where to start searching, and *pattern* is the word you are looking for (which can be enclosed in double-quotes for strings).

For example:

[FONT="Courier New"]$ find /home/foo/source -name '*.cpp' -exec grep "hello world" {} \; -print[/FONT]

Once you understand the basics of the find command and can't stand to type such a lengthy command, try adding the following to your ~/.aliases file:

```
#!/bin/bash

findstring()
{
  if [ $# != 2 ]; then
    echo "Usage:  findstring <dir> <string>"
  else
    find $1 -exec grep "$2" {} \; -print
  fi
}

findfile()
{
  if [ $# != 2 ]; then
    echo "Usage:  findfile <dir> <filename>"
  else
    find $1 -name '$2" -print
  fi
}
```

Then source the ~/.aliases file from your ~/.bashrc file:

```
if [ -f ~/.aliases ]; then source ~/.aliases; fi
```

---

### Post by Barleyman on 2007-08-28
Thanks for the advice.  The standard commands work fine, but when I try to put them into my aliases file and reload, I get the following error.

$ findstring(mystring)
bash: syntax error near unexpected token `mystring'

---

### Post by Paulmd on 2007-08-28
> **Barleyman said:**
> Thanks for the advice.  The standard commands work fine, but when I try to put them into my aliases file and reload, I get the following error.

$ findstring(mystring)
bash: syntax error near unexpected token `mystring'

I dind't see 'mystring' in the sample code, is it in yours?

---

### Post by dwhitney67 on 2007-08-28
> **Barleyman said:**
> Thanks for the advice.  The standard commands work fine, but when I try to put them into my aliases file and reload, I get the following error.

$ findstring(mystring)
bash: syntax error near unexpected token `mystring'

The proper usage is:

$ findstring <dir> <mystring>

There is no need for the parenthesis.

Another thing one could consider doing is changing the functions to accept a string and *then* a directory name.  If no directory name is supplied, then assume the search begins in the current directory (i.e. ./).

---

