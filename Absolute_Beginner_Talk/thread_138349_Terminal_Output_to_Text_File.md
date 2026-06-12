---
title: "Terminal Output to Text File"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by TrevorNet on 2006-03-01
Is there a command I can pass terminal at the beginning of my sh script that forces the output to be written to a text file? ;)

---

### Post by suRoot on 2006-03-01
```
./script.sh > output.txt
```

would probably be the most basic example.  Depending on how your script works, there may be other ways of doing it.

---

### Post by Ramses de Norre on 2006-03-01
You can redirect a command using >
For example: $ ls > ls.txt drops the output of ls to a file ls.txt in the current directory.

---

### Post by TrevorNet on 2006-03-01
Sorry suRoot, your suggestion didn't produce the desired results... but Thank You just the same!

Ramses de Norre, that did work. :)

I've been trying to dump the entire PEAR library onto my box and have had no luck with either the web or Gtk front-ends. So, I had pear list out all of the packages, and in a text editor, I added "sudo pear....". Anyway, terminal wasn't displaying the complete results. I want to make sure all the holes are patched. With a text file I can do that. I've attached my hack-job-of-a-script.

Thanks for your help!

---

### Post by suRoot on 2006-03-02
Maybe I'm misunderstanding what you want, but instead of putting ```
sudo ls > ls.txt
``` at the beginning of the file, change that to ```
sudo ls
``` (assuming you actually want the directory listing) & then run your script as ```
./pear.sh > output.txt
``` - that should redirect any console output to the text file.

Also, add ```
#!/bin/bash
``` as the very first line of your script... since it's a bash script :)

---

### Post by daredevil on 2006-03-02
Good explanation all. thnk you all.

---

### Post by frodon on 2006-03-02
[QUOTE=suRoot][/CODE] (assuming you actually want the directory listing) & then run your script as ```
./pear.sh > output.txt
``` - that should redirect any console output to the text file.[/QUOTE]This will put the script output in the output.txt text file except the error messages.
If you want to put also the error messages add the "&" character like that : ```
./pear.sh >& output.txt
```

---

### Post by tonytraductor on 2008-01-31
Okay...but what do I do if I want to pipe the output of something more
complex to a text file, such as

for i in 0 1 2 3 4 5 6 7 8 9 10 11 12
do 
	echo "$a x $i =" $(($a * $i))
done

I want to ouput that to a textfile, so I can display the output in zenity.

I'm trying to do something like this:

#!/bin/bash

# math program written by anthony baldwin / [email]tonytraductor@linguasos.org[/email]
# for my daughter...

usr=$(whoami)


zenity --info --title "Daddy's multiplaction mAddness" --text "Hi, $usr.  
Welcome to Daddy's multiplaction mAddness, 
which will help you with multiplication."

a=$(zenity --entry --text "Enter a number to generate a multiplication table:")

for i in 0 1 2 3 4 5 6 7 8 9 10 11 12
do 
	echo "$a x $i =" $(($a * $i))
done > mtable

zenity --text-info --title "Multiplication table for $a:" --filename="mtable"

exit

I also though of trying to assign the output to a variable, such as

mtable=$(for i in 0 1 2 3 4 5 6 7 8 9 10 11 12
do 
	echo "$a x $i =" $(($a * $i))
done)

# then display with zenity

zenity --info --title "Multiplication table for $a:" --text "$mtable"

But that doesn't work either...

I'm kind of new at this stuff, and trying to learn.
I just thought a little program to help my 3rd grade daughter with math would be a good project.

thanks
tony

---

