---
title: "Simple Question about Installing ,.tar, .gz2, .tar.bz2 , Packages"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by noncentz303 on 2007-08-21
Ok so im a complete nub about what goes down when installing a package in linux...

I am running ubuntu 7.02 I believe.. basically what im trying to do is install and use this editing program Blender....

it comes zipped and compressed from what I can tell : blender-2.44-linux-glibc232-py24-i386.tar.bz2
The problem im having is that I cannot extract any of these files, what im assuming at this point is that these files must be extracted via a add and remove app feature. But when I go to the add/remove function I just get a bunch of programs to download and I cannot navigate to the files I downloaded which are on my desktop...

First am I on the right path????

Second when I try to extract file it tells me the file is corrupt using bzip2, but ive download multiple times and no luck yet and it does this for all my files which is telling me im stupoud...

So I must be doing it wrong...

---

### Post by scrooge_74 on 2007-08-21
That is a compressed file, which is different from a .deb packages which is what you use to under the add/remove.

Probably with that compress file you need to compile the program in order to use it.

You can also open synaptic and search there for the program you are trying to install

---

### Post by Perfect Storm on 2007-08-21
Try with (if the compressed files are on Desktop):

```
cd ~/Desktop
tar jxfv blender-2.44-linux-glibc232-py24-i386.tar.bz2
```


by the way why not grab Blender through synaptic?

---

### Post by noncentz303 on 2007-08-21
I would get from synaptic but the ubuntu box we are using is not connected to internet so thats a no go. Plus I would like to learn how to install my own packages, to much hand holding is a killer....

I tried:   tar jxfv blender-2.44-linux-glibc232-py24-i386.tar.bz2 

Last night and I got the message that the file was not compressed right or damaged. But when I used my Windows box and decompressed the file with winrar it worked just fine for me... then i moved the files over to my linux box and I was able to run blender just fine!!!!!!

I guess I just dont understand where im going wrong as I have always used  tar jxfv  for all of my tarballs. I have tried the archive manager on multiple files with the same results... command line and gui

Driving my crazy....

---

### Post by Irony on 2007-08-21
Simply download the file, e.g.;

[http://download.blender.org/release/Blender2.44/blender-2.44-linux-glibc232-py24-i386.tar.bz2](http://download.blender.org/release/Blender2.44/blender-2.44-linux-glibc232-py24-i386.tar.bz2)

Then right click on it and choose;

[PHP]Extract here[/PHP]

Then open the extracted folder and double click on blender - and thats it; you can of course now move the folder to anywhere you like. I put in in my home folder and put a dot before it so its hidden and then create a menu link to the blender file.

I always find that the extracted blender works faster than the repository installed blender.

Note the terminal way of doing it is for me;

[PHP]user@ubuntu:/media/hda8/NOSAVE/blender$  tar xjvf '/media/hda8/NOSAVE/blender/blender-2.44-linux-glibc232-py24-i386.tar.bz2' [/PHP]

Thus I first open up the terminal in the folder where I have downloaded the blender compressed file to then I execute the command.

---

