---
title: "more basic cli help"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-03-08
k i just copies the whole thing... i created the following script in gedit... my problem is at the bottom when the author says "when you run the script..."... i cant run the script... or more appropriately, i dont know how.... if i type the file name 'trouble.bash' in the terminal i get an error message... how do i run scripts?



Stay Out Of Trouble

by William Shotts, Jr.

Now that our scripts are getting a little more complicated, I want to point out some common mistakes that you might run into. To do this, create the following script called trouble.bash. Be sure to enter it exactly as written.

#!/bin/bash

number=1

if [ $number = "1" ]; then
    echo "Number equals 1"
else
    echo "Number does not equal 1"
fi
       

When you run this script, it should output the line "Number equals 1" because, well, number equals 1. If you don't get the expected output, check your typing; you made a mistake.

---

### Post by glennric on 2008-03-08
First you will have to make the file executable.  To do this type
```
chmod +x filename
```
Then to execute the file, assuming you are in the directory that you created the file in, type
```
./filename
```

---

### Post by taurus on 2008-03-08
Open a terminal, Applications -> Accessories -> Terminal, and do

```
chmod 755 trouble.bash
./trouble.bash
```
assuming that you are in the directory where trouble.bash is located.

---

### Post by Nythain on 2008-03-08
first ya have to make it executable
```

sudo chmod a+x filename

```
then, to run it...
if you are in the directory its in
```

./filename

```
should do the trick
if you put the file somewhere in your $PATH you can run it by just typing the file name
```

sudo cp /path/to/filename /usr/bin

```
usually does the trick for me, once its in /usr/bin all you have to do is type the filename from anywhere in a terminal :)

---

### Post by LuisGMarine on 2008-03-08
to run a scrip make it executable with the following command:

```
chmod +x name_of_scrip.sh
```

Also name your scripts with the extension [COLOR="Red"]**.sh**[/COLOR], not .bash I dunno but I never heard of .bash.

to run the scrip just type in
```

./name_of_script.sh
```

or 

```
sh name_of_script.sh
```

---

### Post by glennric on 2008-03-08
It is better to put a script into your users bin directory with
```
cp filename ~/bin/
```
You may need to add
```
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```
to your .bashrc file to add this directory to your path.  It is probably already there, but commented out.

---

### Post by ghostdog74 on 2008-03-08
> **LuisGMarine said:**
> 

Also name your scripts with the extension [COLOR="Red"]**.sh**[/COLOR], not .bash I dunno but I never heard of .bash.
[/CODE]

the file extension doesn't matter at all. in fact you can call the script anything you like.

---

### Post by manicmailman on 2008-03-08
sweet thanks... my biggest beef with the tutorial is that it doesnt answer the 'why' question very much... but these forums do... nice work..

---

