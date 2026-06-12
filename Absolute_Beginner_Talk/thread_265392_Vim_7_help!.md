---
title: "Vim 7 help!"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by bkildow on 2006-09-25
Hello, lately I have been exploring different some editors and I wanted to give vim 7 a try. So I uninstalled the ubuntu default vim(6.x) and downloaded  vim 7 from their site and compiled from source. Now I open it and start typing and it seems wildly different from the default vi that was installed. the backspace keys just write over the letters and they don't dissappear, and the arrow keys produce the letters ABCD going up on a new line on each. Does anyboday have any insight into this, I am relativly new to linux and vim and I just want to be able to use it like I did with 6.

---

### Post by Mr Frosti on 2006-09-25
I have not used Vim 7 specifically, however I have seen many people stuck in a macro, or a mode they did not intend.

Make sure that you have exited out of all the advanced functions of Vim by pressing the "Escape" key several times. The status bar at the bottom of the application should show just the line that you are currently on.

In Visual Mode, you can highlight text and copy and paste. In Insert mode, you can create or delete text. If you are in Insert mode, make sure that you didn't accidently press the "Insert" key, as this causes different results.

There is a Command mode, where different keys cause different actions, such as ":q"

Also, note that there is a difference between vi and vim. Vi is the original circa 1970's application, and Vim has improved upon this base. Currently, the Vim varient with the smallest learning curve is Gvim. It is point and click with drop down menus. Give it a try!

---

### Post by bkildow on 2006-09-25
Thanks for the suggestions. I actually found out how to solve the problem. Create a file in the home directory called .vimrc and add "set backspace=indent,eol,start" to it. (minus quotes).

---

### Post by Brunellus on 2006-09-25
Vim is a powerful text editor.  It is also frightentingly terse, and not what most new users used to.

vim actually has a good online tutorial--start it with 

```
vimtutor
```

from the command line.

if you need a cheat sheet, several excellent ones exist:

[http://www.worldtimzone.com/res/vi.html](http://www.worldtimzone.com/res/vi.html)

[http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf#search=%22vim%20cheatsheet%20pdf%22](http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf#search=%22vim%20cheatsheet%20pdf%22)

---

