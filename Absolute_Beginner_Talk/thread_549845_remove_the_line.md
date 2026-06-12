---
title: "remove the line"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by munna_dude on 2007-09-13
hi all
how to remove the line
first we have to search the line 
if the line exist remove the line
else
dont do anything.

for example "disable_from_plugins" , this is the word containing the line
search the line and delete.. programatically

can you please help me 

thank you in advance

---

### Post by Wim Sturkenboom on 2007-09-13
Your question fits better in the [programming](http://ubuntuforums.org/forumdisplay.php?f=39) section.

In C, you can use *strstr* to find a substring, terminate the string at that point and you have the first part. Increment the pointer (the length of the substirng positions (*strlen*)) and you have the beginning of the second part. Next glue them togetter with *strcat*.

Another solution is to use regular expressions. Most languages support this (C, TCL, PHP,...) or you can use SED or AWK (not sure if they are considered programming languages).


OOPS, did not read properly (thought you had to remove the word). SED would be perfect for this. But the other options still work as well.

Some pseudo code
```

while_there_is_a_line
{
    if(strstr(yourline,yourword))
        next line
    else
        write to new file
}

```

---

### Post by munna_dude on 2007-09-13
> **Wim Sturkenboom said:**
> Your question fits better in the [programming](http://ubuntuforums.org/forumdisplay.php?f=39) section.

In C, you can use *strstr* to find a substring, terminate the string at that point and you have the first part. Increment the pointer (the length of the substirng positions (*strlen*)) and you have the beginning of the second part. Next glue them togetter with *strcat*.

Another solution is to use regular expressions. Most languages support this (C, TCL, PHP,...) or you can use SED or AWK (not sure if they are considered programming languages).

thank you for your kind replay..
i dont know where to post this querry...

if anyone please help me ..

otherwise send this querry to programming section..

thank you in advance

---

### Post by ukripper on 2007-09-13
What programming language are you using, just out of curiousity?

---

### Post by munna_dude on 2007-09-13
> **ukripper said:**
> What programming language are you using, just out of curiousity?

u may provide in c or bash script..
i have to search the word
and remove the total line that containg the word
then save the file 
this all can be done at a time...

please help me 

thank you inadvance

---

### Post by munna_dude on 2007-09-13
hi i tried up to this
```

cat munna.c | grep disable_from_plugins

```
the output is 
> 
g_ref(disable_from_plugins);

then hoe to remove the line that containing "disable_from_plugins".

and save the file..(munna.c)

and
if the word not find....
dont do any thing..

i prefer c or script.

please help me 

thank you in advance

---

### Post by ubuntukerala1980 on 2007-09-13
As i understood you need to delete lines from a file with a specific word and then save it into another file
cat filename | grep  -v "word_you_search_for"  > newfile

Please let me know the result

---

