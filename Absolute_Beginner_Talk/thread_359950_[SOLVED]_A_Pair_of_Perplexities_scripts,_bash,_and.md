---
title: "[SOLVED] A Pair of Perplexities: scripts, bash, and $RANDOM"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Troubled on 2007-02-12
I've stumbled across an additional couple of roadblocks on my road to script functionality.

The first is easy:
I'd like to run commands that require root privileges from a script at startup; how would I go about doing this? Appending 'sudo' to the start of the lines doesn't seem to help a lot.

The next one is a bit baffling for me:
Though in the bash tutorials I've read online, $RANDOM generates a random value, when used in a bash script, it only returns a null value. However, I've tried it in the terminal and $RANDOM works fine! Why doesn't edgy want to generate a random value my scripts?


Any solutions?

---

### Post by jordanmthomas on 2007-02-12
I had problems with $RANDOM as well (on my Arch Linux install)
So, I wrote a c program to generate them for me:
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX 5000000

int main(int argc, char *argv[])
{
        long howMany = atol(argv[1]);
        int i;
        for (i = 0; i < howMany; i++)
        printf("%d\n",rand() % MAX);
}

```
You can change the MAX to the highest number you want to generate, and then compile it:
```
gcc -o generateRandoms generateRandoms.c
```
You'd run it like this:  
```
./generateRandoms *numberOfRandomsYouWant*
``` and you can pipe it to whatever needs the randoms

---

### Post by jordanmthomas on 2007-02-12
A "solution" to the sudo problem could be to run 
```
gksudo /path/to/script
```
as the command in the startup 

It would prompt you any time you log in (annoying), but should work.

---

### Post by Troubled on 2007-02-12
Great, thanks!

I've managed to resolve my $RANDOM troubles; it turns out that I've been using 'sh' to run the scripts instead of './'.

---

