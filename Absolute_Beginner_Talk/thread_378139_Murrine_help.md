---
title: "Murrine help"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by satchelpig on 2007-03-06
I have downloaded a Murrine configurator, but it's empty and I can't figure out how to install themes that I download.  Can someone guide me?  

Thank you!

---

### Post by ComplexNumber on 2007-03-06
> **satchelpig said:**
> I have downloaded a Murrine configurator, but it's empty and I can't figure out how to install themes that I download.  Can someone guide me?  

Thank you!
"empty"? what do you mean by empty? 


to install themes that you've downloaded:
1) unpack them by right clicking on the package and choosing 'extract here'.
2) if there is more than 1 theme in the package, have a look inside the extracted contents for the themes and place the themes in /home/<your username>/.themes. otherwise, just take the extracted theme and place it in said place.

---

### Post by satchelpig on 2007-03-06
OK, that makes sense, but something weird is going on.   I can't find a ".themes" folder anywhere in my home folder.  But when I try to create one, it gives me the error message "The name ".themes" is already used in this folder. Please use a different name."  

But I don't see the thing anywhere.  What the heck is going on?

(By "Empty" I meant there are no themes listed in the configurator)

---

### Post by pburdick on 2007-03-06
The dot in front of a file name makes it a hidden file. If you are using Nautilus (GUI), press ctrl+H and it will "unhide" the hidden files. If you are using the terminal, type ls -a to list all the files.

---

### Post by satchelpig on 2007-03-07
> **pburdick said:**
> The dot in front of a file name makes it a hidden file. If you are using Nautilus (GUI), press ctrl+H and it will "unhide" the hidden files. If you are using the terminal, type ls -a to list all the files.

Ahhhhhh.  Didn't know that. Did the trick.  Thank you.

---

