---
title: "Problems with md5sum in general"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by giorgione on 2007-12-08
Hi there,
I have some question regarding md5-checksums. 

- I know that "md5sum file.flac > file.md5" will create me a text file with the checksum and the filename. But how do I make it when I want to create a checksum of a folder and all the files and folders in that folder? I tried "md5sum -r" but it did not work.

- I have a lot of checksum files from my Windows-time which were created with md5summer. But when I try to use md5sum to check these files I always get the error:
: No such file or directory
: FAILED open or read
for every file. But when I open the md5-file with an editor it looks the same as those created by md5sum (except that there is a '*' before every filename). 

Thank you very much for your help.

---

### Post by conehead77 on 2007-12-08
Use this to create a .txt file for your md5sums:
```
md5sum mydirectory/* > mymd5sums.txt
```

To check if the md5sums are correct, use this command:
```
md5sum -c mymd5sums.txt
```

Let me know if this is what you wanted

---

### Post by giorgione on 2007-12-08
Thank you but this does not do the trick. If there is a folder in mydirectory I get the error
```
md5sum: mydirectory/anotherfolder: Is a directory

```
and in the mymd5sums.txt file are only the files from the mydirectory.
What I want is a list of all the files of all the folders and subfolder of mydirectory. Like when you make a 
```
ls -R
```

And do you have any Idea about my 2. problem? 
By doing 
```
md5sum -c  mymd5sums.md5
```
with mymd5sums.md5 created with md5summer in windows I always get the error
```
: No such file or directory
: FAILED open or read

```
for every file in the list. What I found is that then I replace the backspaces of the windows-created .md5-file with new ones in an editors, md5sum starts to recognize the files. Are the Backspaces different in Linux and Windows??

---

### Post by conehead77 on 2007-12-08
If you only want to compare 2 directories without saving the md5sums you could use the diff command, like
```
diff -r directory1 directory2
```

But for saving the md5sums it seems you have to write a bash script for it, which goes through all subdirectories and adds the md5sums from each directory to the .txt file.
I didnt do much scripting yet, so im sorry i cant help atm. (Maybe ill look into it during next week as it seems a good exercise for learning)

As for the windows-md5sums i really dont know. It could be that md5summer uses a different formatting than the linux md5sum. Im sure this can be solved with a very simple script too (but again i have no concrete idea).

I will subscribe to this thread and maybe i find the time to make a script this week.

---

### Post by conehead77 on 2007-12-12
Looks like this has been done before:
```
sudo apt-get install md5deep
```
To use it recursive and have the output in a file use it like this:
```
md5deep -r my_directory > my_output_file
```

---

### Post by giorgione on 2007-12-14
Thank you. This does exactly what I was looking for.

---

