---
title: "Boot Menu Order"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by jhartford on 2006-03-17
How Can I change "Windows XP Professional" as the top choice and reduce the timer to 3 seconds?  My parents use the computer and they're.....techincally challenged so I want it to just choose Windows automatically unless I switch to Ubuntu real quick.  \\:D/

---

### Post by sn123 on 2006-03-17
[QUOTE=jhartford]How Can I change "Windows XP Professional" as the top choice and reduce the timer to 3 seconds?  My parents use the computer and they're.....techincally challenged so I want it to just choose Windows automatically unless I switch to Ubuntu real quick.  \\:D/[/QUOTE]
You can change the timer time and the default boot option by editing the grub menu.lst file, to edit the file open a console and type this:
```

$ sudo gedit /boot/grub/menu.lst
(enter your password when it prompts for it)
>scroll down to the entry for timeout and change it to your liking:
timeout **3**
>to set Windows as the default boot option change the default param:
default **n**
Where n is the number of Windows in the Boot Menu Sequence starting from 0. Save the file and you should be done (it's generally a good idea to make a backup of the file before you edit it).

``` 

Best,
S
Edit: forgot the / before boot/grub....

---

### Post by jhartford on 2006-03-17
Thanks! :mrgreen:

---

### Post by jhartford on 2006-03-18
I found the boot time, but whats the command line where I change the #?  Thanks!

---

### Post by dvarsam on 2006-03-18
You did NOT get an answer, because nobody understands what you are talking about man...

Explain yourself...

The "#", means that whatever words are lying on the right side of it are comments & should not be read during Run...

What exactly are you trying to do with the "#"?

---

### Post by sn123 on 2006-03-18
[QUOTE=dvarsam]You did NOT get an answer, because nobody understands what you are talking about man...

Explain yourself...

The "#", means that whatever words are lying on the right side of it are comments & should not be read during Run...

What exactly are you trying to do with the "#"?[/QUOTE]
I *think* # meant "number", to change the default there would be line in menu.lst starting with **default** (something like default 0), to change it to Win XP as being the default change the value from 0 to the position of Win XP in the Menu list (remember the numbering starts from 0, so if Win XP is the fourth option in the menu you would have to make it "default 3").

HTH,
S

---

### Post by jhartford on 2006-03-19
At the boot menu it lists a few different Ubuntu files and then Windows XP at the bottom.  It automatically chooses Ubuntu if I dont use the arrow keys to go down to Windows XP and hit enter.  How do I make it so Windows XP is the default unless I select Ubuntu?

---

### Post by PhilOSparta on 2006-03-19
[QUOTE=jhartford]At the boot menu it lists a few different Ubuntu files and then Windows XP at the bottom.  It automatically chooses Ubuntu if I dont use the arrow keys to go down to Windows XP and hit enter.  How do I make it so Windows XP is the default unless I select Ubuntu?[/QUOTE]

This should tell you everything your need.  
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

