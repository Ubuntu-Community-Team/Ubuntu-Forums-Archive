---
title: "Different stuff like games, music, videos etc."
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by ir_newbie on 2006-08-05
Right, so i started using ubuntu like a week back and i need to know some stuff...
1. How do i connect to the internet i already have a pcmcia card which i use on a different laptop which has windows
2. Now before ubuntu i used suse 10.1 for like 10 days and had found some great games like battle for wesnoth and armagetron and was wondering how i could get them on ubuntu
3. there are a lot of formats which linux or ubuntu doesn't play, it doesnt even play mp3!!! also except .avi no other video format seems to be supported, help!
4. In college we are being taught c++ and i tried writing a program on ubuntu terminal using the vim command but dont know how to compile it,

I know all of this sounds completely hopeless, but what's worse is that there's more... I just dont remember it right now!!

Anyway an early thanks to the people who help out... thanks!

---

### Post by tommcd on 2006-08-05
See this for MP3 and other codecs:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I think armagetron can be found in synaptic:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
I'm not sure about compiling. Can't help with that.

---

### Post by anasofiapaixao on 2006-08-05
Oh boy, I am susprised that you teacher didn't almost force you guys to use a unix terminal, like mine did... you were probably using on Windows Dev-C++ or something, right?

To write programs and compile them you have two ways: either use an IDE (meaning a program like Dev-C++ that allows to write the code, compile, generate projects, etc etc in a nice graphich interface without muss or fuss) or use the command line to compile and Gedit (Applications-- Accessories-- Text Editor) to create the code, and yes, your average plain text editor has syntax highlighting for several programming languages, now tell me how cool is that. I assume you probably want an IDE - I think Anjuta is a nice one.


- Add the universe and multiverse repos to your repos list (to be able to get many many more appas that are not "officially" supported by the Ubuntu Team): System-- Software Preferences-- Add... button-- Check all checkboxes available, then click Add. It will ask to refresh the software list, that's ok.

- Then open a terminal (Applications-- Accessories-- Text Editor) and type:
```
sudo apt-get install anjuta g++
```
(this will install the IDE, Anjuta, and the compiler, g++)

After all done, close the terminal and you should have it under the "Programming" menu entry, that has just awakened from invisibility in your GNOME menu.

If you want/need to use console, just use
```
g++ -o /path/to/output-executable /location/of-your/sourcecode
```

With quotation marks if any of the paths have spaces.

And have fun! BTW I have a sudoku solver on hold written on C, I'll post it out somewhere once it has minimal functionality...

---

### Post by ir_newbie on 2006-08-06
Well, funnily enough, or college does make us use the unix or linux based systems, which dont have all the hassles of different editors to be started just type vim write ur program and compile and run

How bout the games...
and most importantly THE NET!
because right now i have to rely on my dads windows lappy for the net access and that can sometimes be a hinderance... you know what i mean!

---

