---
title: "bash: syntax error near unexpected token `('"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by hafunui on 2006-01-26
Hello, I seem to have run into another problem :P

Ever since my move to Linux, I've been learning how to use the console to do almost everything ( cause its fun :D ). 

Using the console, I copied a whole directiry to my desktop. And the permission setting didnt allow anyone to write the folder OR the files inside. So I did some searching and figure that I want to do:
[COLOR="Sienna"]
sudo chmod 777 [directory][/COLOR]

It fixed the problem on the folder, but not the files inside.

So i try it with the file.

One of the files happens to be "Earthbound (U).001"
So I enter:

[COLOR="Sienna"]sudo chmod 777 /home/nathan/Desktop/Snes9X/ness/Earthbound\ (U).*[/COLOR]

( asterisk because all the files share the same name, but different extentions )

By doing that, it plops out this error:

[COLOR="Sienna"]bash: syntax error near unexpected token `('[/COLOR]

So how do I do anything with a file name like that?

I DID get around this by doing *.* but I doubt that will work for every situation.

---

### Post by Iowan on 2006-01-26
Once again showing my "just enough to be dangerous"... I presume the backslash was to dereference the space?  Perhaps dereference the paren's too?
Maybe single, double quotes - or the backtick?

---

### Post by cwaldbieser on 2006-01-26
[QUOTE=Iowan]Once again showing my "just enough to be dangerous"... I presume the backslash was to dereference the space?  Perhaps dereference the paren's too?
Maybe single, double quotes - or the backtick?[/QUOTE]
Single quotes will treat all contained characters as non-special by the shell.  You can also escape them with the backslash (\).

---

### Post by IdolizingStewie on 2006-01-26
That is correct, Iowan. Use backslash to dereference both parentheses just like you did the space. I frequently find tab-completion quite useful for this sort of thing.

edit: Dang it, you posted while I was typing, cwaldbieser. Oh well, I didn't know about the single quotes thing. Interesting.

---

