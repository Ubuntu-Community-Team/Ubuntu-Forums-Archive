---
title: "Firefox google web accelerator"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Rosemere on 2007-09-04
I received an newsletter where they are talking about the Google Firefox web accelerator. I downloaded but it is a bin file so how do execute the program?

---

### Post by skymera on 2007-09-04
i dont thunk its linux availible.

---

### Post by Rosemere on 2007-09-05
Thank you.

---

### Post by banewman on 2007-09-05
There is an optimised firefox for linux called "swiftfox". I noticed 10-20% improvement with it and it takes all firefox plugins. [http://getswiftfox.com/](http://getswiftfox.com/)  :)

---

### Post by nilufer on 2007-09-18
it  must be an executable file.
open the terminal and cd to the directory where the bin file is located.
eg: if it is in /home/wasn/Desktop/install.bin
then
type in 
> cd /home/wasn/Desktop/
at the $ prompt. and enter.
type 
> ls -l
and see the file's properties.

it should be something like this.
> -rwxrwxrwx wasn:wasn Date ..............   install.bin

if you find '-' instead of 'x' in the relevant places i.e something like -rw-rw-rw- without x.

then type 
> chmod +x install.bin
thats it.
now the file is executable.

now run the file using the command 
> ./install.bin

it should run the installer.

tell me whether it did work.

---

### Post by Kilz on 2007-09-18
> **banewman said:**
> There is an optimised firefox for linux called "swiftfox". I noticed 10-20% improvement with it and it takes all firefox plugins. [http://getswiftfox.com/](http://getswiftfox.com/)  :)

Swiftfox is a proprietary application made from free code. It restricts freedoms Firefox has. In fact Ubuntu cant even add it to the Ubuntu repositories because of that. You may want to try other applications if freedom is important to you.[ Let me recommend Swiftweasel]("http://swiftweasel.sourceforge.net/").

---

