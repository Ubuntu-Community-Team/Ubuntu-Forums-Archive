---
title: "To check free HDD space on debian"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Aliyans on 2008-04-04
hi
   sorry...accidently posted..i found it on other threads...anyway i aslo have another doubt..whether there is a recylcle bin on linux...if there how do i empty it..n the temorary files...thanx

---

### Post by ajmorris on 2008-04-04
> **Aliyans said:**
> hi
   sorry...accidently posted..i found it on other threads...anyway i aslo have another doubt..whether there is a recylcle bin on linux...if there how do i empty it..n the temorary files...thanx

Hi there,
i dont believe teh recycle bin on ubuntu is in /tmp where your other temporary files are... the recycle bin in linux barely ever gets used... i cant remember exactly, but i think it is in ~/.Recycle<something a rather>. if you ls ~/.Recycle<tab> i.e, press tab where i have written <tab> it should tell you the name of the recycle bin folder, however, this may not be where the recycle bin is located..... sorry, not much help i know :( at least it will bump the thread for someone else to see :)

---

### Post by kpkeerthi on 2008-04-04
Its .Trash folder in your home directory. Files deleted using File manager usually get in there. Unlike windows, there is no 'restore' option - you need to manually move the file from trash to wherever you want.
SHIFT+ DELETE and remove command from terminal cause permanent deletion.

---

### Post by Aliyans on 2008-04-04
hi
   is there a commmand to delete files from trash folder... but i couldnt see trash folder in home directory... u mean it will be inside  /home/user  ??

---

### Post by kpkeerthi on 2008-04-04
> **Aliyans said:**
> hi
   is there a commmand to delete files from trash folder... but i couldnt see trash folder in home directory... u mean it will be inside  /home/user  ??

Are you viewing it using nautilus? Press <Ctrl> + H to see hidden files and folders.

or open a terminal and type 
```

cd .Trash<press-tab-key> <enter>

```

Then ```
 rm *
```

**[COLOR="Red"]Be sure to run this command from correct folder or you may risk loosing data[/COLOR]**

---

### Post by Aliyans on 2008-04-04
hi
   i want command from a terminal ..like putty or xterm  is the above one is for terminal

---

### Post by kpkeerthi on 2008-04-04
Yes.. run the above 'cd' and 'rm' commands from a terminal window

---

### Post by aeiah on 2008-04-04
you will find a .Trash folder in every partition, incidentally, not just your home folder. if you have, say, a hard drive for your movies, deleting /media/movies/video.avi will put it in /media/movies/.Trash

---

