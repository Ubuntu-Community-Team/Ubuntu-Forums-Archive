---
title: "Need command line to change file extensions"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by margni on 2007-01-21
I'd thought I'd done good...  I got my scanner working!  - But...

When I was scanning, I forgot to add the *.jpg at the end of the scanned files.  Thus my stupid windows computer can't tell what my smart Ubuntu computer made...  w/o renaming each individual file to include *.jpg...

Isn't there a command line command to change all the files in a folder that look like:

Picture  >>>  to  >>> Picture.jpg   

(I went crazy and have scanned almost 1100 pictures and was sooooo stupid as to forget to add the extension to each and everyone of them...)   ](*,) 

Help!  and thanks in advance...

Margni

---

### Post by taurus on 2007-01-21
```
mv Picture Picture.jpg
```

---

### Post by meng on 2007-01-21
Try this shell command:

for filename in `ls`; do mv $filename $filename.jpg; done

EDIT: oh make sure you're in the directory with all these files before you go renaming everything from the WRONG folder!!!!

---

### Post by margni on 2007-01-21
Thanks Taurus and Meng...

You guys gave me the basic idea if I have one file to change...

I should make myself clearer...  How do I do this if I have multiple files that are missing extensions...?

pic1, pic2, pic3  >>> to >>>  pic1.jpg,  pic2.jpg,  pic3.jpg

Is it the same command?  or what am I missing?

Thanks in advance...

---

### Post by Pobega on 2007-01-21
> **meng said:**
> Try this shell command:

for filename in `ls`; do mv $filename $filename.jpg; done

Might want to also mention that that edits **everything** in the folder, not only the images.

> **margni said:**
> Thanks Taurus and Meng...

You guys gave me the basic idea if I have one file to change...

I should make myself clearer...  How do I do this if I have multiple files that are missing extensions...?

pic1, pic2, pic3  >>> to >>>  pic1.jpg,  pic2.jpg,  pic3.jpg

Is it the same command?  or what am I missing?

Thanks in advance...

What meng said should work for you.

---

### Post by meng on 2007-01-21
> **margni said:**
> Thanks Taurus and Meng...

You guys gave me the basic idea if I have one file to change...

I should make myself clearer...  How do I do this if I have multiple files that are missing extensions...?

pic1, pic2, pic3  >>> to >>>  pic1.jpg,  pic2.jpg,  pic3.jpg

Is it the same command?  or what am I missing?

Thanks in advance...
My shell command will nuke EVERYTHING within the current working directory. It's great if every single file within that directory is a misnamed jpeg.

---

### Post by margni on 2007-01-21
Thanks Pobega, and Meng...

The mv command says it can't move the directory inside of itself.  so I'm trying to redirect the shell's output to a different folder...

Terminal comes back and says it can't stat 'ls'...

???

---

### Post by meng on 2007-01-21
You should be inside the directory containing these pics when you run that command ... perhaps you have some complicated folder structure that you're not telling us about?
By the way, ls is spelt as in Larry Schneider.

---

### Post by dwblas on 2007-01-21
I found this link with a rename file search
[http://www.ubuntuforums.org/showthread.php?t=336897](http://www.ubuntuforums.org/showthread.php?t=336897)

---

### Post by margni on 2007-01-21
> **meng said:**
> You should be inside the directory containing these pics when you run that command ... perhaps you have some complicated folder structure that you're not telling us about?
By the way, ls is spelt as in Larry Schneider.


Nope... its a straight path to the pictures folder, and the folder itself has no subs...

Thanks for the Larry Schneider tip

/home/margni/pictures/

thats it!

---

### Post by margni on 2007-01-21
> **dwblas said:**
> I found this link with a rename file search
[http://www.ubuntuforums.org/showthread.php?t=336897](http://www.ubuntuforums.org/showthread.php?t=336897)

Thanks for the link...  It looks a little freaky/daunting, but I'll try it and report back later...

Margni

---

### Post by meng on 2007-01-21
I still think my command should work.

cd /home/margni/pictures

gets you inside the required folder

then run my command.

But if it doesn't work for you and you want to get more complicated than that, be my guest!

---

### Post by Buck2348 on 2007-01-21
> **meng said:**
> I still think my command should work.
Meng's command **does** work--I just tried it out.  If you do 
```
cd /home/margni/pictures/
```
in a terminal and then copy and paste Meng's command and run it, it will rename every file in the folder by adding ".jpg" to its name.

Buck

---

### Post by margni on 2007-01-21
OK!  When I did a cut-n-paste mengs command worked...

I don't know what I was doing wrong to get the 'stat' nag on the terminal...???

Anyhow that worked!  Thanks!!!

---

### Post by meng on 2007-01-21
You probably used single quotes ' instead of backtick `
Originally, I thought you had spelt eye-ess instead of ell-ess.

---

### Post by margni on 2007-01-22
> **meng said:**
> You probably used single quotes ' instead of backtick `
Originally, I thought you had spelt eye-ess instead of ell-ess.

Your command worked when I cut-n-pasted it, but I thought I faithfully had typed it - and got the 'stat' issue...  And I most likely DID type something wrong - which was not using the 'backtick' - I did use the apostrophe instead... 

None-the-less it worked very well.  Thanks!  Once again the Ubuntu community came to save my bacon!!!  Thanks! =D>

---

### Post by Catsworth on 2007-01-22
I think you need to be inside the folder structure before you carry out the command.

Type this in a shell to move to the folder with your pictures in and then try the rename again.
```

cd /home/margni/pictures/

```

---

### Post by margni on 2007-01-22
BTW Meng,

Since I did use the apostrophe instead of the backtick, what is the reason for using the backtick character to frame the ls command?

Thought I'd ask, to know why...

Margni

---

### Post by JamieC on 2007-01-22
It evaluates what is between the two backticks. For example:-

$ echo 'ls' (This is essentially the same as "echo ls" since there are no spaces and it does not require quotes):
> 
ls


$ echo `ls`:
> 
Folder Folder File Folder Folder


Therefore, in context, the command loops over the directory listing, 'moving' each file by relocating it with the correct extension.

---

### Post by margni on 2007-01-22
Thanks JamieC...

I did find if my pictures didn't have underscores in the name i.e.  this picture  instead of
this_picture  then the command wouldn't do anything and it would comeback and say each of the words in the pictures title would not be a valid directory...

Is there a way to get around this? Like I said in my opening post I got the scanner to work and so I went nuts scanning pictures!!!  But as a 'greenhorn' I didn't name them with underscores inbetween the words in the title to the files...

Mengs command worked like a champ when all the files in a directory were single names like 0001 or pic...  But when I named them:  cool shot of old canon instead of cool_shot_of_old_canon  then it doesn't work...

???  Thanks for all your help out there to all!!!

---

