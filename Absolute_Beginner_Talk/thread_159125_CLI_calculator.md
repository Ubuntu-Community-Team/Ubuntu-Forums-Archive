---
title: "CLI calculator?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-04-12
Is there a pre-installed CLI calculator installed?  If so, what is the command?

---

### Post by WelterPelter on 2006-04-12
Python works good for that, and is pre-installed.

---

### Post by Harleen on 2006-04-12
"bc" is what you are looking for.

---

### Post by tux101 on 2006-06-08
I read the bc manual up to the expression part.  And I still don't understand how it is suppose to work.  This tiny application's manual is over 800 lines!

Is there something CLI that just works for a newbie?

Something as simple as typing in 'app 1+2=?' and it will give me back a result as '3'.

---

### Post by mcduck on 2006-06-08
[QUOTE=tux101]I read the bc manual up to the expression part.  And I still don't understand how it is suppose to work.  This tiny application's manual is over 800 lines!

Is there something CLI that just works for a newbie?

Something as simple as typing in 'app 1+2=?' and it will give me back a result as '3'.[/QUOTE]
try the suggested Python:

1.type 'python' to enter the python console
2.type '1+2' and press enter
3. youll get the answer.
4. press ctrl-D to exit (if I remember right ;))

---

### Post by Van_Gogh on 2006-06-08
I use the Deskbar [Calculator]("http://live.gnome.org/DeskbarApplet/Extending")(Search for "Calculator Handler"). After you install that, you can enter expressions like "2+3" into Deskbar and it will give you the answer.

---

### Post by Arndt on 2006-06-08
[QUOTE=tux101]I read the bc manual up to the expression part.  And I still don't understand how it is suppose to work.  This tiny application's manual is over 800 lines!

Is there something CLI that just works for a newbie?

Something as simple as typing in 'app 1+2=?' and it will give me back a result as '3'.[/QUOTE]

There is the program 'expr':

```
% expr 1 + 2
3
%
```

Its intended use is in scripts, but of course you can use it like this too. Note that all items need to be separated by spaces.

'bc' is a whole language, but it seems it's intuitive enough if you just dive in:

```
% [COLOR="Blue"]bc[/COLOR]
bc 1.06
Copyright 1991-1994, 1997, 1998, 2000 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'.
[COLOR="Blue"]1+2[/COLOR]
3
[COLOR="Blue"]1.2 + 4.5[/COLOR]
5.7

```

---

### Post by tux101 on 2006-06-08
The expr is what I was looking for since I am using it as part of a script.  But I can't get the multiplication to work.

```
 expr 2 * 2
expr: syntax error

```

A little more help, please?

---

### Post by void_false on 2006-06-08
```
[1752][void@linux:~]$ echo $((2+2))
4
[1752][void@linux:~]$ echo $((2*2))
4
[1752][void@linux:~]$ echo $((2/2))
1
[1752][void@linux:~]$ echo $((2-2))
0
[1752][void@linux:~]$
```
Bash can count O.o:shock:
[www.linuxcommand.org](www.linuxcommand.org) is your friend.

---

### Post by mostwanted on 2006-06-08
* is interpreted by BASH as a semi-regular expression (* means everything in this case), you need to backslash it like this:

expr 10 \* 5

(returns 50)

Or just do it like void false showed (using BASH evaluations).

---

### Post by Arndt on 2006-06-08
[QUOTE=tux101]The expr is what I was looking for since I am using it as part of a script.  But I can't get the multiplication to work.

```
 expr 2 * 2
expr: syntax error

```

A little more help, please?[/QUOTE]

The asterisk '*' is a shell meta-character. That means it has a special meaning, which is to indicate an indeterminate part in a filename (ls a*, for example, lists all files with names beginning with 'a'). When you need the '*' itself, you have to quote it, either using single or double quotes, or with a backslash:

expr 2 '*' 2
expr 2 "*" 2
expr 2 \* 2

[Edit:] So what 'expr' got in your case was a list of filenames, with a 2 before and after. To see exactly what, use 'echo' instead of 'expr'. 'echo' just reprints all its arguments, with meta-characters expanded by the shell.

---

### Post by tux101 on 2006-06-17
How do I get echo to do fractions?
```
echo $((1*0.5))
bash: 1*0.5: syntax error in expression (error token is ".5")
```

---

### Post by Arndt on 2006-06-19
[QUOTE=tux101]How do I get echo to do fractions?
```
echo $((1*0.5))
bash: 1*0.5: syntax error in expression (error token is ".5")
```[/QUOTE]

'bash' doesn't handle floating-point numbers, and neither does 'expr'. But 'bc' and 'perl' do.

```
% echo '3 * 4.3' | bc -q
12.9
% perl -e 'print 3 * 4.3; print "\n"'
12.9

```

---

### Post by soze on 2006-06-19
Although not a general-purpose "calculator" one very useful program is *units*. It can do pretty much any type of unit conversion.

If you ever wanted to know that 55mph equals 147,840 furlongs/fortnight or that 1 parsec contains 3.085678 X 10**26 angstroms, this program will tell you.

---

