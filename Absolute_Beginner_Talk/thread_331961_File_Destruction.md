---
title: "File Destruction"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Prime_Numbers on 2007-01-05
Is there something equivalent to Inferno for Linux? :-k   Inferno is a file destruction program that also encrypts files.  Thank you
Prime Numbers

---

### Post by kosmic on 2007-01-05
Hum, you have the 'shred' comand.

Just do 'man shred' in a terminal to see what it can do :)


SHRED DESCRIPTION
       Overwrite the specified FILE(s) repeatedly, in order to make it  harder
       for even very expensive hardware probing to recover the data.

---

### Post by Prime_Numbers on 2007-01-05
ok, I typed "man shred" on my terminal and I get a description of the command.  Is "synopsis" the way the command works???  

      **shred** [OPTIONS] _FILE_  [...]

This is as far as I got and Im a total noob.  Can anyone elaborate on what I need to do next??
Thank you so VERY much

---

### Post by jvc26 on 2007-01-05
well 
```

shred [OPTIONS] FILE [...]

```
Explains how you run the file! In terminal you type
```

shred **/path/to/file/filename**

```
The options you can choose will probably also be included in there:
> 
  -f, --force
              change permissions to allow writing if necessary

       -n, --iterations=N
              Overwrite N times instead of the default (25)

       -s, --size=N
              shred this many bytes (suffixes like K, M, G accepted)

       -u, --remove
              truncate and remove file after overwriting

       -v, --verbose
              show progress

       -x, --exact
              do not round file sizes up to the next full block;
              this is the default for non-regular files

      -z, --zero
              add a final overwrite with zeros to hide shredding

       --help display this help and exit

       --version
              output version information and exit

Il

---

### Post by Prime_Numbers on 2007-01-05
Well, I tried typing: 
                             shred -fuz /home/'my user name'/news/'file name.extension'
and I get an error message:
                             'failed to open for writing: no such file or directory'
](*,)  any suggestions??

---

### Post by Albi on 2007-01-05
you spelled it wrong, remember linux is caps sensitive

also you can use tab to autocomplete something

---

### Post by Prime_Numbers on 2007-01-05
Albi, thank you, thank you, thank you...  I was spelling it wrong.  Actually I was typing 'news' in lower case.  You Rule!

---

