---
title: "how to copy a file into multiple directories?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by spearfish on 2008-02-26
Hi,

I have a directory that contains a text file and several other directories:

%ls
text.txt
folder1
folder2
folder3
folder4

How can I copy the "text.txt" file into all the folders in the current directory?  I want folder1, folder2, folder3 and folder4 to each have a copy of "text.txt".

---

### Post by Oldsoldier2003 on 2008-02-26
> **spearfish said:**
> Hi,

I have a directory that contains a text file and several other directories:

%ls
text.txt
folder1
folder2
folder3
folder4

How can I copy the "text.txt" file into all the folders in the current directory?  I want folder1, folder2, folder3 and folder4 to each have a copy of "text.txt".

You could link the file to the folders and only keep the one copy. unless of course each folder would have the file in different versions in which case you would need to copy it. 

In the second case,It would probably be faster though less educational to just to use your window manager's file manager( gui ) and copy it in that case, unless its a recurring operation in which case it might be worth the time to write a shell script.

hint: as a start try cat test.txt >> <destination> you can use a loop to make the job easier as well.

---

### Post by spearfish on 2008-02-26
I was hoping the GUI would have the ability to select multiple folders at the same time for a Paste operation, but it doesn't work like that.  I have to copy and paste the file into each and folder, one at a time.  :(

Doesn't cp have a flag to allow copying into multiple directories?

I tried cp text.txt ./*    but that doesn't work.  Bash responds with:

cp: omitting directory `./folder1'
cp: omitting directory `./folder2'
cp: omitting directory `./folder3'
cp: omitting directory `./folder4'

---

### Post by disturbedite on 2008-02-26
could you do something like:
cp /path/to/file /path/to/destination1 /path/to/destination2 etc.?

---

### Post by benfindlay on 2008-02-26
> could you do something like:
cp /path/to/file /path/to/destination1 /path/to/destination2 etc.?

No, that will try and copy the file, and all but the last directory into the last directory. And it will fail to copy the directories, giving an error saying something about 'omitting directory' if I remember correctly. Not sure how you'd go about doing it though, think a script would be required. Something like is discussed here: [http://www.linuxquestions.org/questions/linux-general-1/copy-one-file-to-multiple-directories-253228/]("http://www.linuxquestions.org/questions/linux-general-1/copy-one-file-to-multiple-directories-253228/")

Hope this helps!

---

### Post by herbster on 2008-02-26
Simple:

```
for i in dir1 dir2 dir3; do cp filename $i; done
```

So for your situation:

```
for i in folder1 folder2 folder3 folder4; do cp text.txt $i; done
```

---

### Post by spearfish on 2008-02-26
> **herbster said:**
> Simple:

```
for i in dir1 dir2 dir3; do cp filename $i; done
```

So for your situation:

```
for i in folder1 folder2 folder3 folder4; do cp text.txt $i; done
```

Ah ha... ok this is good.  However, what if I have 100 folders to copy to?  Then I would have to type in:  for i in folder1 ... folder99 folder100;

Is there a way to do all the folders without having to type the name of each one?  The thing is, I have a folder full of directories of student's names, like:

ajsingh
twoods
hsthompson
ajfoyt
jpeterman
pspecter
mmonroe
pmcartney
...
[and about 90 more...]

I'd like to find the script that says something like:

for each [folder] in ./thisDirectory copy text.txt to [folder]

---

### Post by bodhi.zazen on 2008-02-26
for i in xxx;do
cp file "$i";
done

You just have to change xxx to a listing of the destination directories, in your example:

`ls -d */`

bac tics not single quotes

> for i in `ls -d */`;do
cp file "$i";
done

You do not need to write a script :) , jsut enter those commands in the terminal :twisted:

If you can not use a command like ls, use brackets (for xxx)

for i in {dir1,dir2,dir3};do
cp file "$i";
done

---

### Post by herbster on 2008-02-26
```
for i in folder[1-100]; do cp test.txt "$i"; done;
```

Boom

---

### Post by powderhound99 on 2008-02-26
woldn't  a string splice work something like

cp file dir%n

while dir%n==(0,100)

---

### Post by panayk on 2008-02-26
How about:

```
$ find . -mindepth 1 -maxdepth 1 -type d -exec cp file '{}' \;
```

---

### Post by herbster on 2008-02-26
Ooooh this is fun ;) :D

Just tested this and copied a file to dozens of subdirectories:

```
 for dir in *; do [ -d "$dir" ] && cp file.txt "$dir" ; done
```

Clean and doesn't result in the file.txt trying to copy to itself with "." being one of the destinations.

---

### Post by powderhound99 on 2008-02-26
Assuming that you have a hundred folders for multipal users, how about 

user1@computer1$ vi fle 
user1@computer1$ cat file >> you@comp$ 
then have cronjob run rsync -r to update each dir?

---

