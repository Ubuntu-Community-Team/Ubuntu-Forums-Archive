---
title: "help, this command for linux .sh's [for my client]"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-16
guys this is the start of my .sh for my new client for linux:

```

# Endar Main Startup, 100% by Goat Spirit.
# This is the code below XD

cd 'files'
echo ==============================

echo Endar - Linux Version

echo ===

echo Made by Goat Spirit

echo ===

echo goat_spirit@hotmail.com

echo ==============================

#first part of code ^^^
#gotta add a pause sometimer later

menu() {
	echo Type 1 to start Endar.
	echo Type 2 to start the Endar Updater.
	echo Type 3 to start the Website Stealer.
	echo Type 4 to view info.
	echo Type 5 to exit.
	echo ==============================
	echo Your choice?
	}

```

i need help at this part, right after this:
```

echo goat_spirit@hotmail.com

echo ==============================

```

i need some function that will goto menu(),

like in windows u type

```

echo goat_spirit@hotmail.com

echo ==============================
goto menu

:menu
echo bla blah

```

any1 help??

---

### Post by mostwanted on 2006-07-16
How about just calling the function with

```
menu
```

?

---

### Post by Ben Sprinkle on 2006-07-16
typing menu doesnt do anything i tried

---

### Post by mostwanted on 2006-07-16
I think it needs to say

```
function menu() {
...
..
}
```

not just menu() like you have now. Then it should work.

You might also try renaming it, menu sounds like a dangerously common name for a function, it might interfere with something else you install in the future.

---

### Post by Ben Sprinkle on 2006-07-16
nope didnt work either hmm i got
```

lol()

function lol() {
echo "lol"
}

```

---

### Post by Ragazzo on 2006-07-16
> **Goat Spirit said:**
> nope didnt work either hmm i got
```

lol()

function lol() {
echo "lol"
}

```

You must define the function before using it. Write "menu" at the bottom of your first script.

---

### Post by Ben Sprinkle on 2006-07-16
oh i see now but didnt work i got this error

/home/endar/Desktop/Endar - Linux Version/Endar Main Startup.sh: line 28: syntax error: unexpected end of file
endar@ubuntu:~/Desktop/Endar - Linux Version$

---

### Post by Ragazzo on 2006-07-16
> **Goat Spirit said:**
> oh i see now but didnt work i got this error

/home/endar/Desktop/Endar - Linux Version/Endar Main Startup.sh: line 28: syntax error: unexpected end of file
endar@ubuntu:~/Desktop/Endar - Linux Version$

Did you accidentally remove the ending brace?

---

### Post by Ben Sprinkle on 2006-07-16
no i didnt just forget this post plz help on next

---

