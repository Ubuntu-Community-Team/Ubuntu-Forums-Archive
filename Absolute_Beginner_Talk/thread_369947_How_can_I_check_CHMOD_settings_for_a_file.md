---
title: "How can I check CHMOD settings for a file?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-25
How can I check CHMOD settings for a file in terminal?
I know that you change a files CHMOD by typing this for instance in terminal
```
chmod 755 make_page
```
but how can I confirm what kind of chmod a certain file has in terminal?

chmod --help wasn't much of a help I dunno what it's trying to say
> 
mike@sanka:~/bin$ **chmod --help**
Usage: chmod [OPTION]... MODE[,MODE]... FILE...
  or: chmod [OPTION]... OCTAL-MODE FILE...
  or: chmod [OPTION]... --reference=RFILE FILE...
Change the mode of each FILE to MODE.

  -c, --changes like verbose but report only when a change is made
      --no-preserve-root do not treat `/' specially (the default)
      --preserve-root fail to operate recursively on `/'
  -f, --silent, --quiet suppress most error messages
  -v, --verbose output a diagnostic for every file processed
      --reference=RFILE use RFILE's mode instead of MODE values
  -R, --recursive change files and directories recursively
      --help display this help and exit
      --version output version information and exit

Each MODE is of the form `[ugoa]*([-+=]([rwxXst]*|[ugo]))+'.

Report bugs to <bug-coreutils@gnu.org>.
mike@sanka:~/bin$

---

### Post by haricharan on 2007-02-25
use ```
ls -l
``` for that directory which would list the files with the permissions!!..
or if you just want a single file use ```
ls -l <filename>
```

---

### Post by jingo811 on 2007-02-25
ic thx.

---

### Post by haricharan on 2007-02-25
u r welcome... :)

---

