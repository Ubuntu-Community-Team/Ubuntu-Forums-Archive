---
title: "[SOLVED] how do i copy files from dvd drives  to a nfs share using terminal?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-01-24
since nautilus is not currently working in hardy, i'm wondering if anyone can point me in the right direction re: how to copy files from my 3 dvd drives to a nfs share? I am in the process of ripping many .avi files to my server and have been drag/dropping using samba...
i tried
```
sudo cp /media/Movie.avi /storage/storage1
```
but all i get is 
```
cp omitting directory '/media/Movie.avi/'
```

---

### Post by hyper_ch on 2008-01-24
paste the output of:

```

ls -al /media

```

---

### Post by e1ektrob0y on 2008-01-24
```

total 18
drwxr-xr-x  5 root root 4096 Jan 24 18:18 .
drwxr-xr-x 24 root root 4096 Jan 24 17:58 ..
-rw-r--r--  1 root root  166 Jan 24 18:18 .hal-mtab
-rw-------  1 root root    0 Jan 24 18:18 .hal-mtab-lock
dr-xr-xr-x  2 ben  root 2048 Dec  5  2003 Dogma
dr-xr-xr-x  2 ben  root 2048 Nov 30  2003 Ice Age
lrwxrwxrwx  1 root root    6 Jan 17 23:16 cdrom -> cdrom0
dr-xr-xr-x  1 root root 2048 Jan 10  2004 cdrom0

```

---

### Post by hyper_ch on 2008-01-24
well, as you can see, there is no "Movie.avi" in that directory hence you can't copy it.

---

### Post by e1ektrob0y on 2008-01-24
> **hyper_ch said:**
> well, as you can see, there is no "Movie.avi" in that directory hence you can't copy it.
i was using "Movie.avi" as an example...

---

### Post by YoG%*@ on 2008-01-24
> **e1ektrob0y said:**
> since nautilus is not currently working in hardy, i'm wondering if anyone can point me in the right direction re: how to copy files from my 3 dvd drives to a nfs share? I am in the process of ripping many .avi files to my server and have been drag/dropping using samba...
i tried
```
sudo cp /media/Movie.avi /storage/storage1
```but all i get is 
```
cp omitting directory '/media/Movie.avi/'
```


did you try to copy a single file or a directory? for directories you'd have to add the '-r' switch (for recursive).
```

cp -r srcdir targetdir

```

hth,
mux

---

### Post by barbedsaber on 2008-01-24
This may not answer your question, but I am sure there are other file managers other than nautilus, they probobly wont work in hardy tho.

---

### Post by hyper_ch on 2008-01-24
Well, your description is flawed because you are not giving the relevant data so I cannot tell you what is wrong with the command you used.

---

### Post by e1ektrob0y on 2008-01-25
> **hyper_ch said:**
> Well, your description is flawed because you are not giving the relevant data so I cannot tell you what is wrong with the command you used.

People use examples all the time like, "your/home/directory". It is not flawed. You could tell me what command YOU would use to copy from a dvd drive to a nfs share? Otherwise, stay out of this thread and let someone who knows how to do it answer the question...

---

### Post by Whiffle on 2008-01-25
Well, the first command in your original post is asking it to copy a single file, but the error message is one you would get if you were trying to copy an entire directory, which is why I'm confused.  I'll play with it when I get home...

---

### Post by MrKlean on 2008-01-25
A suggestion.... using synaptic...install gnome-commander...I put mine up one the bar...Under properties..I launch it with gksudo added so I can do anything I want..BUT...THAT"S DANGEROUS LOL!!

---

### Post by hyper_ch on 2008-01-25
you have also mc (midnight commander for the command line)

---

### Post by YoG%*@ on 2008-01-25
> **Whiffle said:**
> Well, the first command in your original post is asking it to copy a single file, but the error message is one you would get if you were trying to copy an entire directory, which is why I'm confused.  I'll play with it when I get home...

exactly! did you make any progress with the command i posted?

oh, and have a look at midnight commander. it really is a great tool!

---

### Post by e1ektrob0y on 2008-01-26
> **mux said:**
> exactly! did you make any progress with the command i posted?

oh, and have a look at midnight commander. it really is a great tool!

not exactly, but you lead me in the right direction :) i was trying to copy the directory that held the .avi file. so now i just cd to /media/movie and copy the file to the nfs share fro,m there. its working now. thanks for all the replies :)

---

### Post by hyper_ch on 2008-01-26
> **e1ektrob0y said:**
> People use examples all the time like, "your/home/directory". It is not flawed. You could tell me what command YOU would use to copy from a dvd drive to a nfs share?.[/QUOTE

Well, people do use examples all the time but a single file is not the same as a directory. So your example/information that you have given is flawed. 

[QUOTE=e1ektrob0y;4204233]Otherwise, stay out of this thread and let someone who knows how to do it answer the question...
I know to answer your question but you do not ask the right question so I can't give you the right answer.
But given your statement everyone would stay out of here because you're not asking the right thing... would you prefer that?

---

### Post by e1ektrob0y on 2008-01-26
whatever dude...the thread has been marked solved...move on ;)

---

### Post by hyper_ch on 2008-01-26
Friendliness is never inappropriate ;)

---

### Post by kindafunnylookin on 2008-01-26
> **e1ektrob0y said:**
> People use examples all the time like, "your/home/directory". It is not flawed. You could tell me what command YOU would use to copy from a dvd drive to a nfs share? Otherwise, stay out of this thread and let someone who knows how to do it answer the question...

You may be frustrated but please calm down. You reply is against the spirit of ubuntu.

---

