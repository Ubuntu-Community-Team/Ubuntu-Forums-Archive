---
title: "wget download into multiple folders"
date: 2013-04-05
forum: Any Other OS
---

### Post by Si1414 on 2013-04-05
I am using *wget *to download some files. I am using the following code:

```
wget -i list.txt
```

and the *list.txt* is shown below:

```
list.txt:
www.amazon.com/1
www.amazon.com/2
'create & change directory'
www.amazon.com/3
www.amazon.com/4
www.amazon.com/5
'create & change directory'
www.amazon.com/6

```

Is it possible to download the first two links in one folder and the next three in a separate folder and so on?
I mean, is it possible to put a sign or code in the "*list.txt*" file, in such a way that once *wget *reads that line, it creates a new folder and download the rest of the files to that folder? 
In the above example, it starts downloading 1 and 2 in the default folder, then it creates a new folder and downloads 3, 4, and 5 to the new folder, then creates another folder, and downloads 6 into that.

*Why I want to do this*: because I have some links that have the same output filenames, and I do not want to overwrite or rename them, but to put them in separate folders.

I am using cygwin on Windows 7.

Thank you for your help.

---

### Post by erind on 2013-04-06
> **Si1414 said:**
> I am using *wget *to download some files. I am using the following code:
[...]

Is it possible to download the first two links in one folder and the next three in a separate folder and so on?
I mean, is it possible to put a sign or code in the "*list.txt*" file, in such a way that once *wget *reads that line, it creates a new folder and download the rest of the files to that folder? 
[...]

I am using cygwin on Windows 7.

Thank you for your help.
AFAIK *wget* doesn't have such an option, ( check "Directory Options" section in wget's man pages ). So I think that you'd need a script for that.
One way with awk:

```
awk '/^dir=/{
       close(wget_links); sub(/dir=/,"");
       wget_links="wget -i - -P " $0; Mkdir="mkdir -p " $0;
       system(Mkdir) ; close(Mkdir)
       next
     }
  { print $0 | wget_links }' list.txt
```

where **list.txt** has this format:

```
**dir=dir_1**
http://Link_1
http://Link_2
**dir=dir_2**
http://Link_3
http://Link_4
http://Link_5
**dir=dir_3**
http://Link_6
http://Link_7
http://Link_8
**dir=dir_4**
http://Link_9
...

```
Note that:

[LIST]
[*] The *list.txt* sample above uses relative paths ( ***dir=dir_1 , dir=dir_2 ***...), so the script will create the directories *dir_1, dir_2*, ... in the current directory, 
[*] you can use *absolute *paths in the dir lines too -** *dir=/full/path/dir_1*** ... 
[*] the dir lines *must *have the format ***dir=/path/to/dir_1**, or **dir=dir_1** *, ... 
[/LIST]
 
Tested on Cygwin.

---

