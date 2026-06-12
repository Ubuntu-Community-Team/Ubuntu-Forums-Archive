---
title: "Creating a Desktop Launcher"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-05-06
I have a file for a game called ActionCube located in:

[HTML]home/ian-m3gxx/Desktop/ActionCube[/HTML]

The file is [HTML]actioncube.sh[/HTML]

I know How to run it in Terminal
[HTML]Cd Desktop
cd ActionCube
sh actioncube.sh[/HTML]

How can I make a desktop launcher to do the same thing?

Ian

---

### Post by holmb101 on 2007-05-06
I think this will work:

/home/ian-m3gxx/Desktop/ActionCube/./actioncube.sh

---

### Post by engla on 2007-05-06
Get Properties on the file (actioncube.sh), go to permissions and make sure it is 'executable' (or do 'chmod +x actioncube.sh' in the terminal).

Right-click on the desktop, choose create launcher. as the command, enter the full path to the file ( /home/ian-m3gxx/Desktop/ActionCube/actioncube.sh ) if the file is executable it should work.

*However:* if the script depends on the current directory being the ActionCube, directory, you have to do this: do the steps above, then take gEdit and open the Launcher file. Add this line:
Path=/home/ian-m3gxx/Desktop/ActionCube/

That is the equivalent of the launcher doing "cd /home/ian-m3gxx/Desktop/ActionCube/", then "./actioncube.sh"

---

### Post by ianb72 on 2007-05-06
> **engla said:**
> Get Properties on the file (actioncube.sh), go to permissions and make sure it is 'executable' (or do 'chmod +x actioncube.sh' in the terminal).

Right-click on the desktop, choose create launcher. as the command, enter the full path to the file ( /home/ian-m3gxx/Desktop/ActionCube/actioncube.sh ) if the file is executable it should work.

*However:* if the script depends on the current directory being the ActionCube, directory, you have to do this: do the steps above, then take gEdit and open the Launcher file. Add this line:
Path=/home/ian-m3gxx/Desktop/ActionCube/

That is the equivalent of the launcher doing "cd /home/ian-m3gxx/Desktop/ActionCube/", then "./actioncube.sh"

I did  'chmod +x actioncube.sh' in the terminal and got nothing.

I am not sure how to do the second part of what you said as I am still learning Ubuntu/Linux

---

### Post by aktiwers on 2007-05-06
Make it like this:
```
sh  /home/ian-m3gxx/Desktop/ActionCube/actioncube.sh
```
or
```
sh  ./home/ian-m3gxx/Desktop/ActionCube/actioncube.sh
```

And tick the run in Terminal box.

---

### Post by ianb72 on 2007-05-06
Neither of them worked :(

---

### Post by aktiwers on 2007-05-06
what error did you get?
EDIT:
What about without the "sh"?

---

### Post by ianb72 on 2007-05-07
I have sorted it now.

The command I needed is:
[HTML]sh -c "cd /home/ian-m3gxx/Desktop/ActionCube && sh actioncube.sh"[/HTML]

---

### Post by ianb72 on 2007-05-07
I  have a new Launcher I want to create this time for Urban Terror

To run it in Terminal I have to do this 
[HTML]ian-m3gxx@ian-m3gxx-desktop:~/Linux-i386$ ./ioUrbanTerror.i386[/HTML]

But how can I transfer this to a Desktop Launcher??

In Terminal if I type:

[HTML]cd /home/ian-m3gxx/Linux-i386 && ./ioUrbanTerror.i386[/HTML]

It works great, but not if I add that line to the Launcher!!!

---

### Post by puttingau on 2007-09-20
I found this a problem too, and have before.
This time I solved it by creating a shellscrip (using the example):

#! /bin/bash
PATH=$PATH:/home/ian-m3gxx/Desktop/ActionCube/
cd /home/ian-m3gxx/Desktop/ActionCube/
actioncube.sh

I think the problem is that the desktop launcher does not start with the path that is normally in your shell, (check with echo $PATH).

Hope this gives a clue to others.

puttingau

---

