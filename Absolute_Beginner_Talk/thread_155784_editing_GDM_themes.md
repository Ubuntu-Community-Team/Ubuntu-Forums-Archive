---
title: "editing GDM themes?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-05
I just tried downloading themes and icons and such, I found a how to and dowloaded the same ones listed there for my first run through.  from GNOME-look.org i got GDM theme Etiquan.tar.gz saved right now.  The info at its download site says to edit line (x) to say what you want, but how to I edit it?  I tried sudo gedit Etiquan.tar.gz but it says it doesnt recognize the characters to open??  
Please tell me how to edit files, thats the only way I know how.  

Also, where do you get the cpu/memory/lan connectivity monitor to sit on the desktop?  The howto said he used gDesklets, but I couldnt find it on Gnome-look.

---

### Post by diebels on 2006-04-05
[QUOTE=x5452]I just tried downloading themes and icons and such, I found a how to and dowloaded the same ones listed there for my first run through.  from GNOME-look.org i got GDM theme Etiquan.tar.gz saved right now.  The info at its download site says to edit line (x) to say what you want, but how to I edit it?  I tried sudo gedit Etiquan.tar.gz but it says it doesnt recognize the characters to open??  
Please tell me how to edit files, thats the only way I know how.  [/quote]The file needs to be unpacked. You could use sudo file-roller Etiquan.tar.gz.
[QUOTE=x5452]
Also, where do you get the cpu/memory/lan connectivity monitor to sit on the desktop?  The howto said he used gDesklets, but I couldnt find it on Gnome-look.[/QUOTE]Search for gdesklets in Applications->Add/Remove->Advanced

---

### Post by kassetra on 2006-04-05
[quote=diebels]The file needs to be unpacked. [/quote]

Another way to unpack the file is to simply click on it.  File-Roller will open & unpack the file automatically for you (similar to winzip on windows) - then all you need to do is drag and drop the folder wherever you want.

---

### Post by x5452 on 2006-04-05
I went in terminal and sudo file-roller Etiquan.tar.gz and it opened up a list where i could see the etiquan.xml file, I clicked it and found where to change what i wnat to tpye, but it wont let me change the words?  do i have to open that file inan editor now that its unrolled?  I tried gedit etiquan.xml and it opens a blank page....

also since I have a thread going, anyone know how i can change the firefox icons?  I ran automatix and got newest firefox, but still old icons.  Also icons on desktop are really big....can they be smaller?  

thanks for your indulgence, sorry I am new  :-(

---

### Post by sn123 on 2006-04-05
[QUOTE=x5452]I went in terminal and sudo file-roller Etiquan.tar.gz and it opened up a list where i could see the etiquan.xml file, I clicked it and found where to change what i wnat to tpye, but it wont let me change the words?  do i have to open that file inan editor now that its unrolled?  I tried gedit etiquan.xml and it opens a blank page....

also since I have a thread going, anyone know how i can change the firefox icons?  I ran automatix and got newest firefox, but still old icons.  Also icons on desktop are really big....can they be smaller?  

thanks for your indulgence, sorry I am new  :-([/QUOTE]
To edit the file:
Most probably when you unpacked .gz file it created a folder structure same as how they were packed, you need to fully qualify the .xml file to open it in gedit.
```

$ find ./ -name "etiquan.xml" -print

```
(get the path from the output of the find and use the fully qualified path to open it in gedit)
```

$ gedit Etiquan/xxx/yyy/etiquan.xml

```

For restoring Fx original icons follow these instructions:
[http://www.ubuntuguide.org/#restoreoriginaliconsfirefox](http://www.ubuntuguide.org/#restoreoriginaliconsfirefox)


HTH,
S

---

### Post by x5452 on 2006-04-05
thank you all very much for your help, ill try that edit when i get back from the stupid math lab.  stupid college.  ](*,)

---

### Post by x5452 on 2006-04-06
is there another way to find the etiquan.xml file to edit it? I tried typing the code in and all it get, no matter what variation i tried  was command not found, or no such file exists.  but if i click place->home->(goes to my home, up top says scott-file browser) i then click Etiquan.tar.gz and then theres an Etiquan folder, inside of whick is etiquan.xml.... i just cant edit it?

---

### Post by trent dillman on 2006-04-06
```

sudo -s
cd /usr/share/gdm/themes/
tar zxf ~/Etiquan.tar.gz

```

Now, go and find the .xml file and edit it to your liking.

---

### Post by sn123 on 2006-04-06
[QUOTE=trent dillman]```

sudo -s
cd /usr/share/gdm/themes/
tar zxf ~/Etiquan.tar.gz

```

Now, go and find the .xml file and edit it to your liking.[/QUOTE]
do this instead, a lot more safer:
```

$ cd /usr/share/gdm/themes
$ sudo tar zxf ~/Etiguan.tar.gz

```


It's always safer to prefix the commands with sudo when you need it :)


S

---

### Post by x5452 on 2006-04-06
thanks for the reply, I had already tried the first way, and i didnt do much, I am not sure where to look i guess. I typed in the code, then went back to the folder and clicked on the etiquan.xml and still nothing to edit?  I tried gedit etiquan.xml and it brings up a blank page..I must be doing something wrong, but i cant figure out what!!???

---

