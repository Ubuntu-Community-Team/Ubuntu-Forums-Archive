---
title: "Spliting files"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by th3gh05t on 2006-09-14
Hi,

I have a big 450 MB (.csv) file that I need to split up into smaller 2 MB files.

I have run the split cmd like this:

"split -b 2m myfile.csv"

That splits up the main file, but it outputs lots of file that look like this, "xaa, xab, xac, etc" with no extensions. Not only are there no extensions for the 200+ files it created, but it also messed up the formatting.

I want the files to be 001.csv, 002.csv, etc...

I have already look at the man page, but that doesnt help me out.

How do I specify what the filename and extension are to be?

Any help in this matter will be greatly appreiciated!

Thanks, th3gh05t

---

### Post by Najand on 2006-09-14
"split -b 2m -d myfile.csv"

---

### Post by th3gh05t on 2006-09-14
> **Najand said:**
> "split -b 2m -d myfile.csv"

Hi, 

I have tried this command, however, it doesn't work. 

"-d" uses a number instead of letter, but it doesn't help in my case, because when I split up the files, there are over 200+ files created...

---

### Post by Najand on 2006-09-14
Well, it is 450 Mb, when you want to split it to 2 Mb files it would be 225 files... What exactly do you wanna do?

---

### Post by th3gh05t on 2006-09-14
That is fine. I don't care about how many files there are. I just need thme to be named like this:

001.csv, 002.csv, 003.csv, etc..

---

### Post by Najand on 2006-09-14
And what happened with
"split -a 3 -b 2m -d myfile.csv"

---

### Post by th3gh05t on 2006-09-14
well, that split up the files like this:

x001, x002, x003, etc.

That is fine, I don't care about the 'x' in the front, but there is still no file extension.

I need a (.csv) extension at the end of alll the files...

---

### Post by Najand on 2006-09-14
Ever heard of "Bulk rename"? You can use the application to make changes to the name of multiple files... like removing some characters, adding some and etc. 
Let us solve your problem using that,  is it ok?

---

### Post by th3gh05t on 2006-09-14
yea, sure...if that works...

Here is the problem though. Because there is no extension given for the files when they are being split, the formatting gets messed up. Even when I rename the file (x001) to (x001.txt) or (x001.csv), gEdit cannot open the files. It says that it doesn't support the character encoding. But (x001.csv) will open up fine in Spreadsheet. Then I have to copy all ofthe columns, and create a new (.csv) file. I don't want to have to do that for 229 files.

---

### Post by Najand on 2006-09-14
Can you install:
```

sudo apt-get install thunar-media-tags-plugin

```

---

### Post by th3gh05t on 2006-09-14
Done.

What now?

---

### Post by Najand on 2006-09-14
Now in Applications  => System Tools => Bulk Rename

Click on BIG "+"  and select all your files;
then click on the box beside  "?"  and select "Remove Characters"
select "0" for "remove  from position"
and select "1" for "to position", click on "rename files" at the bottom.

Now  click on "Remove Characters" and select "insert/overwrite"
Change "overwrite" to "insert" and add ".csv" to "text", select "3" for "at position:" and then click "rename files" 
You are done now.

---

### Post by Najand on 2006-09-14
Please inform me with the results.

---

### Post by th3gh05t on 2006-09-14
Well, that has accomplished what I want,(for filenames) but I still have to go into every file using Spreadsheet and save a new (.csv) file.

I cannot open the file up in gEdit:

> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I added more Western character encoding, but none of them seem to work...

---

### Post by Najand on 2006-09-14
Files with csv suffix  doesn't work for you? 
Anyway, why do you need to split the  files at the first point?

---

### Post by th3gh05t on 2006-09-14
When you use the "split" command, it splits the original (.csv) into binary files.

How do I prevent this from happening? 

This is the root of the problem..

---

### Post by th3gh05t on 2006-09-14
> **Najand said:**
> Files with csv suffix  doesn't work for you? 
Anyway, why do you need to split the  files at the first point?

Yea, I re-named all of x000 -> x000.csv, but just adding an extension doesn't cut it.

The need for you to know the reason why I am spliting the files is irrelevant.

---

### Post by Najand on 2006-09-14
Hmm, maybe it is better to split it by limiting the lines number not the file size. It might work in that case.

---

### Post by th3gh05t on 2006-09-14
Well, first of all, that won't matter in my case.

My filesize restriction is 2MB and less. When you split up using a 65000 line restriction, the files are way too large.

We need to figure out how to split up the files, and keep the (.csv) file extension.

---

