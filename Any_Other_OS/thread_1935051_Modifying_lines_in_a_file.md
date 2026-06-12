---
title: "Modifying lines in a file"
date: 2012-03-03
forum: Any Other OS
---

### Post by gayden on 2012-03-03
hi everybody ,

i've got a txt file that has 1000000 lines , i wanna add this number "050" at the beginning of each line for all the 1000000 lines
is there any way to add them easily ??? i mean a script or a .bat file , i have Backtrack 5 and Windows Vista so anything would help .

thanks in advance

---

### Post by howefield on 2012-03-03
Thread moved to "*Other OS/Distro Talk*" forum.

---

### Post by Porcini M. on 2012-03-03
Open the file in a text editor. Select a newline (with your mouse, click on the end of a line, hold the left button, drag it to the beginning of the next line, release the button). Press ctrl-C to copy the newline.

Select edit->replace. In the search box, press ctrl-V to paste the newline in there. Also paste it in the "replace" box, but then add "050" or whatever to it. Then click "replace all". Then fix up the first and last lines in the file.

---

### Post by gayden on 2012-03-03
sorry but i didn't know where to put it :)
ok thanks imma try it now ^_^

---

### Post by Tiganjero on 2012-03-03
The easiest way to do it is to use vi. Open the terminal and enter:
```
vi /path_to_file/file.txt
```
Once it opens up your file:
```
:%s/^/050/g *<enter>*
:wq *<enter>*
```
That's it, as simple as that.

Cheers,
George

---

### Post by gayden on 2012-03-03
thanks george its woking xD

---

### Post by qyot27 on 2012-03-03
It can be achieved by using sed as well, which has the advantage of not requiring user interaction.  It uses virtually the same syntax as the vi example:

```
sed 's/^/050/g' inputfile > outputfile
```
or, if you aren't worried about backups,
```
sed -i 's/^/050/g' inputfile
```

This will also work just fine in Windows if you've got a usable bash shell available (i.e., if you've got MSys, msysgit, or Cygwin installed).

---

