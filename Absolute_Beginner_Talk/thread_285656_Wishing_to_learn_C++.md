---
title: "Wishing to learn C++"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by marx2k on 2006-10-27
As far as C++ goes, I am a TOTAL newbie but would like to learn it.  What should I do in Ubuntu to get started putting in code, compiling and debugging?  What development system sould I use?  Can someone give me a startup tutorial to do so? 

Thanks in advance!

---

### Post by swamytk on 2006-10-27
1. Just install compile system as shown below:
> $ sudo apt-get install build-essential

2. Run "cc <your c++ file>" at shell to compile.

3. Refer for more detail: 
[http://www.gnu.org/software/gcc/](http://www.gnu.org/software/gcc/)
[http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html](http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html)

---

### Post by whiterabbit on 2006-10-27
If you're wanting to write and learn, Anjuta is a great IDE.

---

### Post by marx2k on 2006-10-27
Both of your answers are PRECISELY what I was looking for!

---

### Post by IYY on 2006-10-27
I find that the beginner doesn't need to confuse herself with IDEs. Just write the program in a plain text file, compile and run.

---

### Post by seijuro on 2006-10-27
> **IYY said:**
> I find that the beginner doesn't need to confuse herself with IDEs. Just write the program in a plain text file, compile and run.

I completely agree. Personally I recommend Vim for editing.

---

### Post by marx2k on 2006-10-27
Im going to start with the command line plain-text editing using nano as I know HOW to use nano...

vi and its' current incarnation vim are very confusing for a newbie such as myself.  Once I begin being somewhat comfortable with coding something more than a 'Hello World' program, I will also begin to explore vim.

Once I gain some prowess with the more 'native' of the linux text editors, I will then move onto an IDE and Im glad there's a good one out there for me to use when I need it.

Heh, I got to say.. after trying to mess around with redhat 3 years ago, slack and debian last year and then Fedora yesterday I got to say that Ubuntu so far has been the easiest to work with and the forum support for it is unreal.  Ive ever been able to ask a question in a forum and get support within minutes. It's what makes people want to stick with something and I definately want to stick with Ubuntu! Even if its just on this Compaq Evo N610c for now. I'd totally convert my 2 desktops to Ubuntu but I need the visual basic environment on one and the other one needs XP to control the ATI All In Wonder Radeon to output to the ole' TV

---

### Post by phranx on 2006-10-27
> 
Im going to start with the command line plain-text editing using nano as I know HOW to use nano...

vi and its' current incarnation vim are very confusing for a newbie such as myself. Once I begin being somewhat comfortable with coding something more than a 'Hello World' program, I will also begin to explore vim.

well...instead of vi and vim, you can use gvim, which is the gnome version.
Then,type this in a terminal:
```
vimtutor
```
 So you will get the 30min tutorial and you will understand why vim (gvim in this case) is so largely used and absolutely loved ;)

That's what i did. After 30' minutes i was able to actually use vim. Be patient for half an hour you'll enjoy vim

Another reason to love vim are the vim-scripts, but you'll see them later.

A simple reason to not use nano:**no syntax highlight**

---

### Post by seijuro on 2006-10-27
> **phranx said:**
> 
A simple reason to not use nano:**no syntax highlight**

that and the autoformatting like automatic indents and such are quite handy imo and one of the long list of reasons I prefer Vim.

---

### Post by zetsumei on 2006-12-20
when i type vimtutor into the terminal it says command not found

---

### Post by n.aggel on 2006-12-20
i suppose you have installed vim??.By the way it is a great editor.Also if you begin using gvim{go to add remove and write gnome vim..}you can easily use it as an ordinary editor...until you understand its gr8t potential.....

Also i don't really like anjuta i prefer gvim or/and Kdevelop, although im just starting to know Kdevelop....

---

