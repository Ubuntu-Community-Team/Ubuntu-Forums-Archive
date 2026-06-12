---
title: "wine can't find C:Program Files"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-04-04
Hi, I have a program called camouflage in wine.

It works by going to program files and clicking the exe

I'm trying to run it from terminal with ```
 wine C:Program Files/camouflage/camouflage.exe 
```

I've tried it with ```
 wine /home/ian/.wine/drive_c/Program Files/camouflage/camouflage.exe 
```
"It says wine can't find" in both cases.

What I'm trying to do is figure out the path and a way to run ```
 camouflage.exe -c [file1] [file2] [file3] 
```

That is the syntax for camouflage to hide a file in another file. 

I just can't get wine to even find the exe through terminal. Is there a way to set the default places wine looks so I can use the "wine C:/camouflage.exe" syntax to run something in wine?

Oh, does wine use those backward slashes like windows?

---

### Post by oni5115 on 2008-04-04
Have you tried using "s  like
wine "C:\Program Files\folder\app.exe"

For desktop links you can use something like this (example of my ventrillo command):
env WINEPREFIX="/home/USER_NAME/.wine" wine "C:\Program Files\Ventrilo\Ventrilo.exe"

Remember to change USER_NAME to your actual user name.  Hope that helps.

---

### Post by Tatty on 2008-04-04
try putting the paths in quoteation marks - "<PATH>"  There is a space in "Program Files", and so you need to surroound the path in quotes so ubuntu knows it is one parameter and not two

I havent used wine from the terminal for ages, but i imagine you would have to use the backwards slashes.  also, i believe there should be a slash after the c:

try this:

```
wine "C:\Program Files\camouflage\camouflage.exe"
```

or

```
wine "/home/ian/.wine/drive_c/Program Files/camouflage/camouflage.exe"
```

---

### Post by iansane on 2008-04-04
OK thanks

I needed the "'s and the backward slashes

Now to figure out how to add parameters. It's actually meant to be run in a command line or from right click menu. Since it did't add to Ubuntu's right click menu, I'm trying to get the right syntax/parameters down so I can use nautilus-action to add it.

---

### Post by oni5115 on 2008-04-04
I think you can just append them like normal.

```
"wine "C:\Program Files\camouflage\camouflage.exe -w"
```

Assuming -w is for windowed mode, or some such parameter.

---

### Post by iansane on 2008-04-05
that's what I'm trying and I think it's right in concept but not working so far

```
 wine "C:\Program Files\camouflage\camouflage.exe -c file1 file2 file3 
```

There is the correct syntax  according to an error message I got from the program. I tried appending it at the end. if you guys think of anything else I'd appreciate your input. I imagine there will be complication in using files on desktop or in home directory for file1 file2 and file3 instead of files in c drive.

 I tried it with full paths to files and it said could not find as if it thought I was telling it some super long file name.

I'll try "'s around each path and filename since it seems to be using exactly what's in the "'s like in programming, saying a variable="whatever"

It's not a big deal, just a project idea I had to integrate it into the nautilus right-click menu but thanks for setting me in the right direction.

---

