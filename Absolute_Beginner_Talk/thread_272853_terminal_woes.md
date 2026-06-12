---
title: "terminal woes"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by thedivvyman on 2006-10-07
Hi - have been messing in the terminal and seemed to have lost a file. I am very new to ubuntu and was playing about changing directories and moving files. I typed this command  in  "spike@spike-desktop:~$ mv tenerife06.odt Martins".  The  result created  a zip archive file on the desktop called Martins.
When extracted it created a folder with  3 folders and 6 files in it. There is no trace of the original file "tenerife06.odt" I was playing with. Although not that important, I would like my file back if at all possible. Can anyone tell me what I've done? Can I delete this folder I created.
I really do find the terminal hard work, but I do want to learn.
Thanks in advance.

---

### Post by pay on 2006-10-07
If it is possible (probably not) try mv Martins tenerife06(1).odt. That might change it back but might not:confused: 
To use the terminal mv <infile> <outfile> for example if you wanted to move tenerife06.odt to the folder Martins you would use mv tenerife06.odt Martin/tenerife06.odt. To move a folder use mv -r. Hope this helps.

---

### Post by aysiu on 2006-10-07
This may not work, but have you tried just doing the opposite? ```
mv Martins tenerife06.odt
```

---

### Post by whistl3r on 2006-10-07
whoops somebody said that before me. I donno how to delete posts over here.

maybe you should try:

"mv Martins tenerife06.odt"

Hope it works.

---

### Post by thedivvyman on 2006-10-07
Ignoring the original file I was playing wth, can anyone explain how or why  the zip file was created. If it helps tenerife06.odt  was on the desktop, and I was trying to move it to "Martinsstuff", which is my home folder. It's as though tenerife06.odt has been swapped for "Martins" zip file, but why does it contain these folders and files, and are they important?
I have took a snapshot of the contents of said folder, but how do I get it on here?
Thanks again

---

### Post by aysiu on 2006-10-07
If you had done ```
mv tenerife06.odt Martinsstuff
``` then it would have moved the file into the Martinsstuff folder.

I just did a test on moving an .odt file to a non-specified extension non-existent folder, and it did make an archive, but when I moved it back to being .odt, it was fine.

---

### Post by thedivvyman on 2006-10-07
Hi - aysiu  thanks for that - can you expand on "but when I moved it back to being .odt, it was fine." What do you mean by when I moved it back?
Thanks for patience

---

### Post by aysiu on 2006-10-07
In other words, this command ```
mv tenerife06.odt Martins
``` changes the OpenOffice document into an archive and this command ```
mv Martins tenerife06.odt
``` will change that archive back into an OpenOffice document.

---

### Post by NeoLithium on 2006-10-07
With terminal you rename files using the mv command on the line (I've done more than my fair share of oopsies with this); but after a while you get used to it.

Really it's nothing to worry about; because it's essentially, as far as I remember, just changing the extension of the file, without actually converting or corrupting the data...at least that's been my lucky experience so far...

---

### Post by thedivvyman on 2006-10-07
A thousand thanks aysiu. That  did the  trick. :-D :-D :-D

---

### Post by thedivvyman on 2006-10-07
Just like to thank everyone. This  community  is  what makes  Ubuntu great.

Cheers

---

