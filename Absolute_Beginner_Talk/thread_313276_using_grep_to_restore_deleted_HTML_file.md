---
title: "using grep to restore deleted HTML file?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by smegmaster on 2006-12-05
I emptied my trash last night, not realizing that my only copy of an important HTML document was in there. I've heard it's possible to use the grep command to locate deleted text files, so long as they haven't already been overwritten on the drive. Does anyone know about this?

Thanks a lot.

---

### Post by ciscosurfer on 2006-12-05
Depends on how much you've done to your drive since the deletion.  Every time your drive was accessed after the deletion, the less likely you are to recover that file.

For example >> From cyberciti.biz:

To recover text file starting with &#8220;nixCraft&#8221; word on /dev/sda1 you can try following command```
grep -i -a -B10 -A100 'nixCraft' /dev/sda1 > file.txt

```More on this here: [http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

I reread your post and noticed you want to recover an html file -- don't know if the above syntax covers that or not (it should, since an html really is just a text file with special code)  Anyway, the above syntax works for text files.  Try the recover command if you're using ext2 or ext3.  You can try this instead: [http://recover.sourceforge.net/linux/](http://recover.sourceforge.net/linux/)

---

### Post by moshuptrail on 2006-12-05
grep is designed to read from standard input, search for text strings, and write the filename to the output if it finds the text.  The standard input would have to be a file, listed in a directory.  Doesn't seem like a good choice to me.  

However, I have seen posts recently naming a few publicly available utilities that are designed to do this.  But, by the time you get one downloaded and installed, unless you can ensure it's on a different filesystem, there's a good chance it will overwrite your original.  Good luck.  Be careful!

---

