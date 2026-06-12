---
title: "How Do I Compile!!"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by nerddy on 2008-04-09
hey there pros.. i have a question.. im doing on widgets LINES.. im trying to compile a sample programme from this website "http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html" 

can anyone show me or teach me how to compile? i tried doing a makefile but i still cant compile it.. thanks for aiding me !!!

---

### Post by Tatty on 2008-04-09
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

Try that.

in short: ```
sudo apt-get install build-essential
```

then

```
./configure
make
sudo make install
```

But you might want to install with checkinstall, which adds an entry for the software to synaptic so it can be easily removed later, in which case:

```
sudo apt-get install checkinstall
```

then

```
./configure
make
sudo checkinstall
```

---

### Post by Jest3r on 2008-04-09
What commands are you using?
Also what is the error that you are getting back ~ from the commands?

---

### Post by nerddy on 2008-04-09
OK i done a makefile for it.. i got an error called makefile:41: *** commands commence before first target. Stop .

---

### Post by joshrobinson on 2008-04-09
> **nerddy said:**
> OK i done a makefile for it.. i got an error called makefile:41: *** commands commence before first target. Stop .

so you got that from running ./configure?
could you post the end 5 or so lines of the error? or was that the only thing that shows up?

---

### Post by nerddy on 2008-04-09
nope i ran that using MAKE.. thats the error.. cus i was told to create a .O file.. im using makefile btw.. however if u have any idea i can compile this widget programme. im willing to learn. =) i got the codes from this site ....... [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html)

---

### Post by nerddy on 2008-04-09
JOSH can i have your email.. so i can ask u questions privately

---

### Post by cheetaux on 2008-04-09
If you only have a couple of files that need to be compiled/link, you should be able to do:

> cc -c main.c

> cc -c sub1.c

> cc -c sub2.c

> cc main.o sub1.o sub2.o -o program

Where **main.c** is the main program, **sub1.c** is another source code file, and **sub2.c** is another source code file.  The **cc -c** command tells the compiler to only compile the source code and create an object file.  The last line links all 3 object files and creates the executable called **program**.

---

### Post by nerddy on 2008-04-09
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html)........ however my file is in .cc format.. do i have to make a makefile?

---

### Post by nerddy on 2008-04-09
i have now a main.cc myarea.cc and a myarea.h file.. how am i going to compile them? u guys can get this code from this website and try to compile.. [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html).. lemme know if u can compile.. im dead beat URGH!

---

### Post by lackofcreativity on 2008-04-09
Did you run ./configure before you tried to compile? You need to do this to make sure you have all the necessary files and libs.

---

### Post by nerddy on 2008-04-09
where do i type ./configure?

---

### Post by nerddy on 2008-04-10
HELP ME AGAIN GUYS!!! how do you compile this program [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-cairo-drawing-lines.html) -->> SEE FROM THIS WEBSITE.. i want that 3 lines to appear!!! HELP ME OUT THANKS!

---

### Post by Laser Dude on 2008-04-10
I think he probably didn't navigate to the directory...

In terminal, (Applications>Accessories>Terminal) use the "cd" command to go to your directory.  Then once you're in the directory that you extracted it into, run the commands that the others have indicated.

---

### Post by hugmenot on 2008-04-10
nerddy, the people shouting around about configure scripts and whatnot have no clue. Try what ceetaux suggested first. A Makefile is something like a script doing this.

---

