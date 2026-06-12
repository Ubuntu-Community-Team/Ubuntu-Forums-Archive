---
title: "VPC07 &amp; U704 Editing Grub Boot"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by MacScotland on 2007-06-11
I've been following instructions here -

[http://ubuntuforums.org/showthread.php?t=414094&highlight=virtual+PC+2007&page=2](http://ubuntuforums.org/showthread.php?t=414094&highlight=virtual+PC+2007&page=2)

And have 7.04 installed with VPC2007. Trying to make mouse change permanent I look at this

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Which tells me I need to  use - sudo vi /boot/grub/menu.lst

I try in terminal but get this empty window - what am I doing wrong?

---

### Post by Skrynesaver on 2007-06-12
vi is an editor, in my personal opinion the best editor there is, however it can be a bit tricky if you're not used to it, as it has many variants vim elvis .... I'm not sure which you are using, but that blank screen is normally associated with a new/empty file  
You should perhaps try using a more familiar editor.
```

gksudo gedit 
```
Then open the file from the File>Open dialog.

---

