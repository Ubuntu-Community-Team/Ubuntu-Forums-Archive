---
title: "Shell script syntax and other stuff"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-21
Ok, I'm making this script and would like to know what I would do/what to put if I wanted to detect if a key is pressed (like 'cin' and then a variable in C++)?

---

### Post by MEW on 2007-06-21
```

echo -n "What is your name? "
read Name
echo Hello, $Name

```

Afterwards, you can access what the user typed as $Name (it's case-sensitive, IIRC).

The "-n" switch to echo makes it not print a newline after its text; the text doesn't really need to be in quotes, but if the trailing space isn't printed otherwise.

---

### Post by ryanVickers on 2007-06-21
Perfect!  Now, how would I say "if an answer is 'y', delete the files in a previously collected list (used 'find'), else, quit"?

---

### Post by MEW on 2007-06-22
```

echo -n "Are you sure (y/n)? "
read Sure

if [ $Sure == "y" ]
then
     rm $ListOfStuffToDelete
fi

```

If-statements are a bit odd in bash - you have to have a semicolon or newline between if and then. You can put any command after 'if'.

The square brackets are actually a command of their own -- "[" is another name for the "test" command -- see man test or man [ for more syntax information. Important to note is that == is the operator for testing string equality, while "-eq" tests equality of integers.

---

### Post by ryanVickers on 2007-06-22
Thanks alot1  this will really help alot of my stuff!  But how would I turn the list that I got using 'find' into the variable?

And I just tested it, and it seems to not like the rm command, says "missing operand":

Here's my code so far:
```

#!/bin/bash
echo
echo "=================================="
echo "= Will now display all '~' files ="
echo "=================================="
echo
find . -name "*~" $list
echo
echo "=================================="
echo "=    End of list of '~' files    ="
echo "=================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
rm $list
echo
echo "================="
echo "= Files deleted ="
echo "================="
echo
fi
if [ $sure == "n" ]
then
echo
echo "===================================="
echo "= Script aborted - Files were kept ="
echo "===================================="
echo
fi

```
yeah, it finds everything ok, but it won't delete them.  Perhaps I'm not adding the list to the variable right?  So, like I said, how to do this?

---

### Post by MEW on 2007-06-24
```

#!/bin/bash
echo
echo "=================================="
echo "= Will now display all '~' files ="
echo "=================================="
echo
find . -name "*~"               # I changed this
echo
echo "=================================="
echo "=    End of list of '~' files    ="
echo "=================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
find . -name "*~"  | xargs rm {}            # I changed this
echo
echo "================="
echo "= Files deleted ="
echo "================="
echo
else                    # I changed this
echo
echo "===================================="
echo "= Script aborted - Files were kept ="
echo "===================================="
echo
fi

```

I changed a few things -- here is my modified version of your script. I used "else" instead of checking if $sure == "n", because that means that the user will see the message "Files were kept" instead of nothing, if s/he types something other than 'y' or 'n'

It is possible to store the output of a command in a variable, such as List=$(find . -name "*~") , but the filenames will be separated by spaces if you do it that way. That means that the printed list of files will be hard to read. It seemed easier to run find twice instead.

A note about variable names -- if you are assigning a value to a variable, you do *not* put a dollar-sign in front of the variable name. That is only done when retrieving the value.

By the way, this script will not delete files with spaces in their names. rm will think that A File With Spaces.odt is four separate files -- "A", "File", "With", and 'Spaces.odt", none of which actually exist.

---

### Post by ryanVickers on 2007-06-24
Oops, this is actually really old code!  my new copy is this - see what you think of it:

```

#!/bin/bash
echo
echo "=============================================="
echo "=     Will now display all useless files     ="
echo "=============================================="
echo
find $HOME -name "*~"
find $HOME -name "Desktop.ini"
find $HOME -name "Thumbs.db"
echo
echo "=============================================="
echo "=        End of list of useless files        ="
echo "=============================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
find $HOME -name "*~" -print0|xargs -0 /bin/rm -f
find $HOME -name "Desktop.ini" -print0|xargs -0 /bin/rm -f
find $HOME -name "Thumbs.db" -print0|xargs -0 /bin/rm -f
echo
echo "=============================================="
echo "=     Answer is yes - Files were deleted     ="
echo "=============================================="
echo
elif [ $sure == "n" ]
then
echo
echo "=============================================="
echo "=      Script aborted - Files were kept      ="
echo "=============================================="
echo
else
echo
echo "=============================================="
echo "=   Not a proper answer! - Files were kept   ="
echo "=============================================="
echo
fi

```

By the way, I tested finding and removing a file with a space in the name and it worked fine (using this code)

---

### Post by ryanVickers on 2007-06-24
Ok, what is the setup of and infinite loop that does something every loop?  So far, an 'until' loops works fine by going until [ 5 == 2 ] :), but it looks kinda dumb! :p

---

### Post by MEW on 2007-06-26
'while true' or 'until false' -- there are programs /bin/true and /bin/false that always return true and false, respectively.

By the way, nice find about 'xargs -0' -- I'll have to remember that :)

---

### Post by ryanVickers on 2007-06-26
Ok, good, that'll be useful, and look better than "until [ 5 == 2 ]" :p


> 
By the way, nice find about 'xargs -0' -- I'll have to remember that :smile:I have no idea what it means! :)

I just took one look at that and laughed so much!  I wanted to do a search and find, then possible remove, and the code was "dash 'print' zero bar xargs space dash zero space slash bin slash rm dash f!  Well, it got the job done nicely, and thanks for getting that for me FuturePast, but it just looked hilarious

---

### Post by Nekiruhs on 2007-06-26
> **ryanVickers said:**
> Ok, good, that'll be useful, and look better than "until [ 5 == 2 ]" :p


I have no idea what it means! :)

I just took one look at that and laughed so much!  I wanted to do a search and find, then possible remove, and the code was "dash 'print' zero bar xargs space dash zero space slash bin slash rm dash f!  Well, it got the job done nicely, and thanks for getting that for me FuturePast, but it just looked hilarious
Well, I just did a Wikipedia on xargs. Apparently, xargs takes the output of one command, and uses its as command line parameters for the next. For example
```
ls -R "~/My Music" | grep "Fields of Despair" | xargs rm 
```
Would list the files recursively in ~/My Music, search for a line containing fields of despair, and tell rm to delete it. Also i could exchange the last part (after the last | ) with xargs -i { } ~/.Trash. The -i tells xargs to replace { } with the output passed to it, this time the script would move the file to the trash, instead of deleting. Pretty useful.

---

### Post by ryanVickers on 2007-06-26
Huh, I guess that makes sense.  It would be useful, I can just imagine!...

---

