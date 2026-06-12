---
title: "[SOLVED] echoing something before and after every listed item"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by mouseboyx on 2008-01-17
Im trying to echo :

echo <a href="{ls}">{ls}</a>

How would i do something like this?

---

### Post by asmoore82 on 2008-01-17
> **mouseboyx said:**
> Im trying to echo :

echo <a href="{ls}">{ls}</a>

How would i do something like this?

all special charaters need to be "protected" from the SHELL parsing;
encase them in single quotes to do this:

```
echo '<a href="{ls}">{ls}</a>'
```

single quotes offer 100% protection;
while regular qutoes still do some processing such as shell variables:

```
**asmoore@ubuntu-thinkpad:~$** echo '$SHELL'
$SHELL
**asmoore@ubuntu-thinkpad:~$** echo "$SHELL"
/bin/bash
```

if you ever need an actual single quote or apostrophe;
protect it by a preceding it with a backslash.
The tricky part here is that if you are already within a
single quoted block, you must stop and restart it:

```
echo 'Single Quotes('\''s) can get tricky!'
```

---

### Post by The Cog on 2008-01-17
for x in $(ls) ; do echo "<a href=\"$x\">$x</a>" ; done

---

### Post by asmoore82 on 2008-01-17
if you are tying to echo a listing with HTML markup to link to each item:

i think the quickest way to do it would be to skip actually using the ``ls'' command
and exploit the BASH shell's natural wildcard(*) abilities:

```
for filename in *
do
  echo -n '<a href="'
  echo -n "$filename"
  echo -n '">'
  echo -n "$filename"
  echo '</a>'
done
```

also you can note that the '-n' switch causes **echo**
to **not** automatically add **newline** charaters.
That way, you can break up stuff into multiple ``echo'' statements for code clarity.
This accomplishes exactly the same thing but is a Dog to look at:

```
for filename in *
do
  echo '<a href="'"$filename"'">'"$filename"'</a>'
done
```

^^too much singledouble,doublesingle quote magic!

---

### Post by mouseboyx on 2008-01-17
Thanks!

---

### Post by mouseboyx on 2008-01-17
See your help here: [http://mouse.homelinux.com/search.html](http://mouse.homelinux.com/search.html)

<?php
$cmd = shell_exec('for x in $(ls *' . escapeshellcmd($_POST['q']) . '*) ; do echo "<br><a href=\"$x\">$x</a>" ; done');
echo $cmd;
?>

---

### Post by asmoore82 on 2008-01-17
> **The Cog said:**
> for x in $(ls) ; do echo "<a href=\"$x\">$x</a>" ; done

^^ this **[COLOR="Red"]Breaks[/COLOR]** if there are any filenames with spaces in them.

---

### Post by asmoore82 on 2008-01-17
just for fun :popcorn:

```
for filename in *
do
        color="black"
        if [ -d "$filename" ]; then
                color="blue"
        elif [ -x "$filename" ]; then
                color="green"
        elif [ -L "$filename" ]; then
                color="red"
        elif [ ! -r "$filename" ]; then
                color="gray"
        fi
        echo -n '<a style="color: '
        echo -n "$color"
        echo -n ';" href="'
        echo -n "$filename"
        echo -n '">'
        echo -n "$filename"
        echo '</a><br>'
done
```

---

### Post by asmoore82 on 2008-01-17
If you want to turn your labor into an executable shell script,
you just have to put the commands into a plain text file
with this as the very first line:
```
#!/bin/bash
```
and then set its executable permission bits:
```
chmod +x <myscriptname>
```

---

### Post by mouseboyx on 2008-01-17
Yeah, i know, i prefer just to get the basic thing so that i can play with it untill it works properly.  I learn better that way...

---

### Post by The Cog on 2008-01-18
> **asmoore82 said:**
> 
> for x in $(ls) ; do echo "<a href=\"$x\">$x</a>" ; done
^^ this **[COLOR="Red"]Breaks[/COLOR]** if there are any filenames with spaces in them.

Ooh-er! So it does. The two halves are treated as separate words. How would you overcome that?

---

### Post by asmoore82 on 2008-01-18
> **The Cog said:**
> Ooh-er! So it does. The two halves are treated as separate words. How would you overcome that?

Again, I would have to say that the most proper way to do the job is with
shell wildcard(*) expansion. But, I've been in this mindset so long; that
I was really quite surprised at how wonderfully tidy your solution seemed
at first(until I noticed the bug).

But, as a matter of "UNIX/Linux/BASH can do anything" exercise;
If you really wanted to achieve the goal with command substitution of $(ls),
you could manipulate the IFS(Internal Field Separator) Environment Variable:

```
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png
**asmoore@ubuntu-thinkpad:~/test$** ln colortest.png "space test.png"
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** for file in $(ls); do echo "$file"; done
colortest.png
space
test.png
**asmoore@ubuntu-thinkpad:~/test$** IFS_BACKUP="$IFS"
**asmoore@ubuntu-thinkpad:~/test$** IFS='
> '
**asmoore@ubuntu-thinkpad:~/test$** for file in $(ls); do echo "$file"; done
colortest.png
space test.png
**asmoore@ubuntu-thinkpad:~/test$** IFS="$IFS_BACKUP"

```

But, even this has a bug, albeit a much more obscure one:
What if a filename actually has a newline in it?

```
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** ln colortest.png 'newline
> test.png'
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  newline?test.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** IFS_BACKUP="$IFS"
**asmoore@ubuntu-thinkpad:~/test$** IFS='
> '
**asmoore@ubuntu-thinkpad:~/test$** for file in $(ls); do echo "$file"; done
colortest.png
newline
test.png
space test.png
**asmoore@ubuntu-thinkpad:~/test$** IFS="$IFS_BACKUP"

```

the wildcard approach successfully handles all of the above;
although for the newline in a filename it appears to be broken,
you can see that it's actally not by making echo put a marker before each filename:

```
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** for file in *; do echo "$file"; done
colortest.png
space test.png
**asmoore@ubuntu-thinkpad:~/test$** ln colortest.png 'newline
> test.png'
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  newline?test.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** for file in *; do echo "$file"; done
colortest.png
newline
test.png
space test.png
**asmoore@ubuntu-thinkpad:~/test$** for file in *; do echo '>>' "$file"; done
>> colortest.png
>> newline
test.png
>> space test.png
```

And finally; if this is a concern(it's usually not with scripts);
anytime you can use some builtin shell abilities instead of calling an external command,
the result is a much more effecient and slightly faster program(script):
(for timing purposes, we won't waste time sending output to the screen;
we will just redirect output to "The Abyss!")

```
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  newline?test.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** time for file in $(ls); do echo "$file" >/dev/null; done

real    0m0.008s
user    0m0.004s
sys     0m0.004s
**asmoore@ubuntu-thinkpad:~/test$** time for file in *; do echo "$file" >/dev/null; done

real    0m0.001s
user    0m0.000s
sys     0m0.000s
```

LATE *Breaking* news - I thought I had found something too good -
command substitution protected by double quotes("s) appears to pass the
"space in filename" test(without IFS tricks); but upon closer inspection
(again, by using a '>>' marker) we see that it is, in fact, completely *broken*:

```
**asmoore@ubuntu-thinkpad:~/test$** ls
colortest.png  newline?test.png  space test.png
**asmoore@ubuntu-thinkpad:~/test$** for file in "$(ls)"; do echo "$file"; done
colortest.png
newline
test.png
space test.png
**asmoore@ubuntu-thinkpad:~/test$** for file in "$(ls)"; do echo '>>' "$file"; done
>> colortest.png
newline
test.png
space test.png
```

P.S. the IFS(Internal Field Separator) is used heavily by the Shell to parse commands
Its default contents can be hard to pin down; but we can "see" them here(in HEX):
```
**asmoore@ubuntu-thinkpad:~$** echo "$IFS" | hexdump
0000000 0920 0a0a                              
0000004
```

The output of `hexdump` is byte-swaped, so the contents of IFS are
Space(ASCII 0x20), Tab(ASCII 0x09) and Newline(ASCII 0x0a).
The second newline(0x0a) was produced by the `echo` command and is not
actually repeated in IFS. This tricky little script, which cannot be simply
typed in on the command line to an interactive Shell, shows IFS in a
"user-friendly" way:

```
**asmoore@ubuntu-thinkpad:~$** cat runme 

IFS_TEST="$IFS"

IFS_TEST="${IFS_TEST//  /[tab]}"
IFS_TEST="${IFS_TEST//
/[newline]}"
IFS_TEST="${IFS_TEST// /[space]}"

echo "$IFS_TEST"

**asmoore@ubuntu-thinkpad:~$** source runme 
[space][tab][newline]

```

P.P.S. Man, I have really forgotten how much I miss "nitty gritty" programming.

---

### Post by The Cog on 2008-01-19
I learned quite a bit from that. Thanks.
I never even know about hexdump. That's a handy filter.

---

### Post by The Cog on 2008-01-19
There is this one:
```
ls | sed 's:.*:<a href="&">&</a>:'
```
I only discovered sed a few weeks ago, and I love it.

---

