---
title: "color on terminal."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-12-23
hello pplz . i am trying to add color on terminal texts... i am looking for this since long time. still i didnt get thing . is there any scripts for it ?

---

### Post by coder_ on 2006-12-23
Try this: [http://www.intuitive.com/wicked/showscript.cgi?011-colors.sh](http://www.intuitive.com/wicked/showscript.cgi?011-colors.sh)

It's from a really nice book that I recommend buying.

---

### Post by slimdog360 on 2006-12-23
try using a different terminal like konsole, yakuake, tilda, the xfce terminal (I dont know if it has a special name), eterm, and heaps of others. My favourite is yakuake.

---

### Post by jordanmthomas on 2006-12-23
If you're talking about gnome-terminal, try this:
right click in the terminal, and go to edit current profile
then, go to the colors tab and you can play around in there.

If you're talking about your ttys (or just your prompt, etc...), then check out coder_'s link.

**oh, btw coder_ that site does have some pretty cool stuff on there.  Thanks for the link

---

### Post by coder_ on 2006-12-23
jordanmthomas: Yeah, that is a really neat book.  I recommend it fully.

 pavel_kbc: Did I misinterpret you?  Did you want to change the color of the text palette of a terminal or change text styles/colors in a script you wrote?  Sorry.

---

### Post by pavel_kbc on 2006-12-23
coder_, no thank you but i got a problem maybe. i run the scripts . its showing me this 

r00t-fck@r00t-suck-on-that:~$ ./color.sh
This is a phrase in yellow and red
This is bold this is italics bye bye
This is italics and this is not
This is ul and this is not
This is inv and this is not
Warning IWarning II
r00t-fck@r00t-suck-on-that:~$ 
r00t-fck@r00t-suck-on-that:~$ 

and color is not working ... 
please help me

---

### Post by pavel_kbc on 2006-12-23
its not what i mean. 

i mean to say 

[COLOR="Red"]r00t-fck[/COLOR]@[COLOR="YellowGreen"]r00t-suck-on-that[/COLOR]:[COLOR="DarkOrange"]~[/COLOR][COLOR="Black"]$[/COLOR][COLOR="RoyalBlue"]sudo[/COLOR]

---

### Post by VuDu on 2006-12-23
check your .bashrc for the lines:

```
# set a fancy prompt (non-color, unless we know we "want" color)
```

```
# Comment in the above and uncomment this below for a color prompt
```

---

### Post by pavel_kbc on 2006-12-25
Thank you Vudu

i added this code

if [[ ${EUID} == 0 ]] ; then
                PS1='\[\033[01;31m\]\h\[\033[01;34m\] \W \$\[\033[00m\] '
        else
                PS1='\[\033[01;32m\]\u@\h\[\033[01;34m\] \w \$\[\033[00m\] '
        fi


and work so fine..

can you tell me how do i add color on every where...
everything even apt , find , and every where :D

---

### Post by moma on 2006-12-25
Check also this thread : [http://ubuntuforums.org/showthread.php?t=229991](http://ubuntuforums.org/showthread.php?t=229991)

---

