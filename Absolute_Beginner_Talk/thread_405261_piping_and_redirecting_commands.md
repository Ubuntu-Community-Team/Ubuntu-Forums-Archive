---
title: "piping and redirecting commands"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-04-09
I am trying to figure out how to quickly move/copy/delete a large number of files in different formats in my system at once. I know that you can redirect the standard output of the ls command to a text file, and I know that you can move multiple files at the same time by doing either 
```
mv file1 file2 file 3 /destination
```
or
```
mv *.filetype /destination
```
assuming that they are all the same type of file. How would one go about redirecting or piping the standard output of ls to the standard input of mv/cp or rm?

---

### Post by Swab on 2007-04-09
Not sure what you are trying to do.

If you want to find all occurrences of a certain type of file and then copy them somewhere you could try the find command.

For example..

```
find ./ -name *.doc -exec cp {} /path/to/copy/top \;
``` 

This would search recursively from the current directory for files with .doc extension, for each file found it would execute the copy command.  The {} is used to signify the path of the found file.

Again, not sure if this is what you are asking.  Also be very careful, this is a powerful command.

---

### Post by rich.bradshaw on 2007-04-09
look at xargs, probably what you need.

try ls | xargs

you will need to use a flag for ls to get it just giving the filenames, perhaps ls -b | xargs

---

### Post by terdon on 2007-04-09
There are many cool trick for this. The easiest is to make an ls for all the file types you want and then use a simple bashscript. eg: ```

for name in $(/bin/ls *.txt *foo* bar*); do  cp $name <new destination> ; done 
```

else you could do the same ls, and redirect its output to a temp file (eg, "temp"). And then read the file's contents and do something to them:
```

ls *.txt *foo* bar* > temp
cat temp | while read name; do cp $name <new destination>

```

Finally, to answer your basic question:
1. redirect output
   You can redirect standard output to a file using the redirect operator ">"
so, for example ```

command > file
```
will send the output of "command" into the file "file". If the file already exists, it will ovewrite (delete) it's contents. If it doesen't it will create it. You can add the output to the end of the file, without deleting its contentd by using the concatenate operator ">>". eg:```

command >> file
```

2. Pipe. The pipe operator "|" will pass the output of one command to another. So, for example if you want to find all .doc files which contain the letter x in their names you could do```

ls *doc | grep ab
```

Between them these operators give you a huge range of consequtive commands you can do.

Finally, there are a couple more you might find interesting:

3. Run a command in the background. If you type a command with "&" at the end, then that command will be run in the background and won't take up your terminal. So, to find all mp3 files in the current directory and redirect the result to mp3s.txt do:```

find . -name "*.mp3" > mp3s.txt &
```

The find will run in the background and you can inspect the results at your leisure

4. Finally, you can set commands to be run one after the other simply by separating a list of commands with the ";":```

command1; command2; command 3
```
In this example, command 2 will be run when command1 finishes and, command3 after command2.

Hope this helps, if you want more specific help on the files you are trying to move/copy/delete give me some details on them and I'll be happy to help.

---

### Post by rich.bradshaw on 2007-04-09
imagine you wanted to do

rm *.doc

you could do

find *.doc | xargs | rm

this works better if you have thousands of files, as rm can only take a certain number of arguments. It feeds rm the filenames one by one.

---

### Post by brennydoogles on 2007-04-09
This has all been very helpful, but let me explain again what I want to do. Lets say that I have a folder full of 100 media files of differing file types (lets say a collection of mp3 avi mpeg jpeg ogg and wav files), and I want to move all of the files in this particular directory to another directory, without moving the directory itself. The way I theorized I could do this would be to navigate to the desired directory and  ```
ls > file.txt
```. From there, i would want to take the contents of that file (which would be a list of 100 media files of differing formats), and make it the object of the mv, cp, or rm command. So basically:
```
ls (directory) > file.txt 
cp (contents of file.txt) /target _directory
```
Does that make any more sense??

---

### Post by Bachstelze on 2007-04-09
```
cp * /target/dir
```

That's all folks !

---

### Post by terdon on 2007-04-09
Yes, you could do that, I'll tell you how in a sec, however it is much easier to just do ```

mv *mp3 *avi *mpeg *jpeg *ogg  *wav target _directory
```

To do it using an intermediate file you would do the ls as you said but then :```
cat file.txt | while read n; do mv $n new_directory; done
```

cat simply spews the contents of a file to standard out, "while read n" is a simple script which puts the contents of each line being read into a variable "n" (you can name it whatever you want) and then does something to each in turn (refering to the variable as dollar n ($n).

---

### Post by Bachstelze on 2007-04-09
```
ls | while read n; do mv $n new_directory; done
```

Why create a file ?

---

### Post by terdon on 2007-04-09
No reason whatsoever, he just seemed determined to do so :)

---

### Post by brennydoogles on 2007-04-10
> **HymnToLife said:**
> ```
ls | while read n; do mv $n new_directory; done
```

Why create a file ?

It's good to know how to do, because if I wanted to```
ls > text.txt
``` l could then go through the text file and manually edit out files that I don't want to move (lets say a particular mood of music... something that I can't really weed out by wildcards) and after editing it I could use the ```
cat file.txt | while read n; do mv $n new_directory; done
``` command to move my now custom list of files. This could be useful for sorting large collections of files in unusual ways.

---

