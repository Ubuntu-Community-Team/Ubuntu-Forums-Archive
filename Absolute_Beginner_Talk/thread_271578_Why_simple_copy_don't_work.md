---
title: "Why simple copy don't work"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-04
I have tried to copy a .jpg image from the Desktop to Desktop to create a copy with a different name so I can modify it.

I can copy a different image and change the name and it works.

The permissions are the same and I am the owner of both files.

```

Ubuntu1:~/Desktop$ cp SLOW_FAN.jpg  fan.jpg
```

error message is 

cp: cannot stat `SLOW_FAN.jpg': No such file or directory

---

### Post by encompass on 2006-10-04
When you mean desktop to desktop do you mean the multiple work spaces?  if so... the data is the same in each.
Is that what your talking about?

---

### Post by kent41 on 2006-10-04
> **encompass said:**
> When you mean desktop to desktop do you mean the multiple work spaces?  if so... the data is the same in each.
Is that what your talking about?

I mean my directory Desktop on my computer.

I can copy other images and change the name in the process.

I just want another copy with a different name.

---

### Post by encompass on 2006-10-04
from the desktop to where...
put it like this...
source:/home/foobar/Desktop
destination:???/+++/&&&

---

### Post by kent41 on 2006-10-04
> **encompass said:**
> from the desktop to where...
put it like this...
source:/home/foobar/Desktop
destination:???/+++/&&&

My first post shows the actual code I used

---

### Post by NT4usB on 2006-10-04
I don't know diddly about Linux... only been at it 6 months.
If I was trying to make a copy of a jpg to the same place with a different name, I would:
cd /home/*username*/desktop/ (not sure if this is right but you get the idea...)
cp somefile.jpg thesamefile.jpg
rather than trying to type the whole path along with the cp command.
ymmv.

ed. does the file you're trying to copy, SLOW_FAN.jpg, exist in the directory you're working in? (I'm sure you're aware) this stuff is all case sensitive.
You have a bunch of jpg's in the folder? What happens if you:
cp SL*.jpg fan.jpg

---

### Post by kent41 on 2006-10-04
> **NT4usB said:**
> I don't know diddly about Linux... only been at it 6 months.
If I was trying to make a copy of a jpg to the same place with a different name, I would:
cd /home/*username*/desktop/ (not sure if this is right but you get the idea...)
cp somefile.jpg thesamefile.jpg
rather than trying to type the whole path along with the cp command.
ymmv.

Please look at my first post. I used the same code on another image and it works but not on the image in the first post.

---

### Post by Brownedwg89 on 2006-10-04
filenames are case-sensitive... if the original file isn't in all caps, then it won't copy
is that the problem?

---

### Post by kent41 on 2006-10-04
> **NT4usB said:**
> I don't know diddly about Linux... only been at it 6 months.
If I was trying to make a copy of a jpg to the same place with a different name, I would:
cd /home/*username*/desktop/ (not sure if this is right but you get the idea...)
cp somefile.jpg thesamefile.jpg
rather than trying to type the whole path along with the cp command.
ymmv.

ed. does the file you're trying to copy, SLOW_FAN.jpg, exist in the directory you're working in? (I'm sure you're aware) this stuff is all case sensitive.
You have a bunch of jpg's in the folder? What happens if you:
cp SL*.jpg fan.jpg


Yes I am in the Desktop directory trying to copy to the same dir.

Yes the file is in upper case.

Yes I can copy othe files in the Desktop dir.


And NO 

```
cp SL*.jpg fan.jpg
```

does not work

---

### Post by Brownedwg89 on 2006-10-04
could you post your ls -l output for us?

---

### Post by kent41 on 2006-10-04
> **Brownedwg89 said:**
> could you post your ls -l output for us?



-rw-r--r--   1 kent kent      38 2006-02-19 15:43 Search for files
-rw-r--r--   1 kent kent 2823639 2005-12-17 14:03 SLOW_FAN.JPG
-rw-r--r--   1 kent kent   23889 2006-08-28 15:35 statement.pdf,

---

### Post by rplantz on 2006-10-04
> **kent41 said:**
> 
error message is 

cp: cannot stat `SLOW_FAN.jpg': No such file or directory

stat is a program that displays the status of a file. (Look at man stat.)

This error message suggests that the file is not in the current directory, or that you have misspelled the name.

A good way to avoid typing errors is to use the tab key to complete the name. For example, if you type
```

cp SL<tab>

```
where <tab> means push the tab key, the shell should complete the name for you. If it does not, that means either (1) you have no files whose names begin with "SL" in the current directory, or (2) you have several files whose names begin with "SL" but have a different third letter. The completion algorithm will continue until it cannot distinguish between similarly named files.

You can tell when it has found a unique name because there will be a space before the cursor. Now you can simply type in the name of the new file.

I am not sure, but you may have some problems if a program has the file open, say, for editing. Just to make sure, you might try quitting all other programs.

---

### Post by Brownedwg89 on 2006-10-04
> **kent41 said:**
> -rw-r--r--   1 kent kent      38 2006-02-19 15:43 Search for files
-rw-r--r--   1 kent kent 2823639 2005-12-17 14:03 SLOW_FAN.JPG
-rw-r--r--   1 kent kent   23889 2006-08-28 15:35 statement.pdf,

oh... i think the .JPG is the problem
did you try typing the extension in all caps too?

---

### Post by Sp00ne on 2006-10-04
Open the picture in GIMP or whatever,then select "save as" and change the name.

That should do it.

---

### Post by kent41 on 2006-10-04
Problems solved

The extension on the source file (jpg) looked like lower case but was UPPER case. 

Changed extension to JPG and it worked

Sorry

Thanks

---

### Post by jordanmthomas on 2006-10-04
Brownedwg89 is absolutely correct.

---

### Post by NT4usB on 2006-10-04
> **kent41 said:**
> Yes I am in the Desktop directory trying to copy to the same dir.

Yes the file is in upper case.



Then you must type it in upper case. *g*

---

### Post by encompass on 2006-10-09
And now he says nothing... hmm well if you see this... type
```
man cp
```
if you want to get the low down of how that command works.

---

### Post by Ben Sprinkle on 2006-10-09
People are dumb as a rock.
First guy, do this:
```

mv file.jpg file.png

```
Or whatever, mv is same as rename. If I misenturperted what you all said then correct me. :)

EDIT:
I see now, just do this mate:
```

mkdir newfolder
cp fan.jpg newfolder
mv fan.jpg fan2.jpg
cp newfolder/fan.jpg /home/$USER/Desktop
rm -r newfolder

```

---

### Post by lemonsCC on 2006-10-09
The problem was solved 4 days ago it was a case error....

---

