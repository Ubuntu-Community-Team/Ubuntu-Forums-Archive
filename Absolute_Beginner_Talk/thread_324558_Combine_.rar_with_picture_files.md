---
title: "Combine .rar with picture files"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Famicommie on 2006-12-23
When I used Windows, I would occasionally use the command prompt to combine picture files with .rar files so that I could post small .rar files on forums and such. Is there any way to do that via the terminal?

---

### Post by dbbolton on 2006-12-23
are you saying that you want to make a rar archive of a directory containing images, or did i misunderstand ?

---

### Post by IYY on 2006-12-23
To download RAR if you do not already have it :

```
sudo apt-get install rar unrar
```

Well, the easiest solution is obviously to just select all of your pictures in the file manager, right click and select 'compress'. 

I think that the commandline for RAR in Linux is the same as in Windows, so the command-line method you used in Windows should now work as well. However, since I've never actually used RAR in Windows, here's a great guide for RAR on Linux (other compression methods also covered):

[http://www-128.ibm.com/developerworks/library/l-lw-comp.html#h3](http://www-128.ibm.com/developerworks/library/l-lw-comp.html#h3)

---

### Post by Famicommie on 2006-12-23
I should have been more specific. There's a way within the MS command prompt to combine a .rar file with a .png so that it can be posted on the internets as a viewable image, but upon downloading it and changing the extension to .rar (or opening it with winrar) it will function as though it were an ordinary archive. It's super neat, so I was wondering if I could recreate that in Ubuntu somehow with the terminal.

---

### Post by Famicommie on 2006-12-23
Oh wait, I just got the answer from another forum. For anyone interested, this is what I was trying to do:

```
cat image.jpg archive.rar >newfile.jpg
```

---

