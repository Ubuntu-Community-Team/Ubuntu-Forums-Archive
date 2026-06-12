---
title: "Cant install anjuta"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by markblue777 on 2007-08-15
Hi All,
i am new to Linux in general and i am use to windows. However, i wanted to make the swap (on my laptop at least). i am trying to install anjuta (c++ide and compiler) however i cant get it to install. i run the config file but it produces this 

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

am i doing something very wrong?

if you can let me know it would be very apprechiated .
Regards
Mark

---

### Post by markblue777 on 2007-08-15
has any one got any idea's please?
Regards
Mark

---

### Post by Hazmat. on 2007-08-15
Anjuta - is that a C++ IDE or something?
Nvm, saw the first post now.  

Are you installing it from add/remove? It works fine there.

---

### Post by markblue777 on 2007-08-16
no i was trying to install it through the download file i got. i will give it a go in add/remove and let you know.
Regards
mark

---

### Post by markblue777 on 2007-08-16
anjuta is not showing in the programming section list any idea's?
Regards
Mark

---

### Post by schorsch on 2007-08-16
It can be installed via the "synaptic" packet manager. You have to enable the universe repositories first:

System --> Administration --> Software Sources --> Ubuntu Software

then check  "Community maintained ... (universe)

---

### Post by markblue777 on 2007-08-16
right i now have it coming up and i check the box next to it then click apply and then install, it appears to do something but once it is finished i check it and it has not installed it (it is not in a list and it is not checked in the add/remove application windows)

any idea's?
Regards
Mark

---

### Post by schorsch on 2007-08-16
I just installed in, too, and the icon can be found under

Applications --> Programming.

But you can also fire up a terminal

Applications --> Accessories --> Terminal

and type "anjuta" in it to start the program.

---

### Post by markblue777 on 2007-08-16
but that is the problem it is not showing under applications-> programming. it is not showing under anything. as if it has not been installed
even though i done everything to install it.

any ideas?
regards
Mark

---

### Post by markblue777 on 2007-08-16
hmm i got it installing under root but when i try to install it under my normal name it states that the sudoes file is 660 (i think) and it should be 440 is the just the permissions set that is wrong on this file?
Regards
Mark

---

### Post by schorsch on 2007-08-16
> **schorsch said:**
> 
But you can also fire up a terminal

Applications --> Accessories --> Terminal

and type "anjuta" in it to start the program.

... and you HAVE TO install programs as root ... but they SHOULD be used with your normal user!

---

### Post by markblue777 on 2007-08-16
o rite cool cheers mate

---

### Post by cwmoser on 2007-08-16
Anjuta?  Boy did I have great difficulty getting Anjuta to install.  I do though have v1.2.4a installed on my PC.  I have not figured out how to build a GUI -- I assume you go to Project -> Edit Application GUI and use the Glade editor.  

Do you know of a tutorial on how to get stated with Anjuta?  How about an example source project?

I also have Mono Develop and was able to to create GUI-based programs.  Be nice to have some tutorials on using Linux IDE's so that more and more programmers will write more and more applications for Linux.

Carl

---

