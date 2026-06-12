---
title: "Shell Scripting"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by J05HYYY on 2008-04-17
Hello, I have just started to write a small program in bash for the first time. Does anyone know the equivalent for the instr function (vb.net) in the terminal? ... Thanks in advance

Josh:)

---

### Post by quirks on 2008-04-17
Hi J05HYYY,

you can use the following command to test if a string is contained in another string:

```
echo "Mary had a little lamb." | grep -c "little"
```

The above command sequence returns 1, because "little" is contained in "Mary had a little lamb.". It would return 0, if the word "little" was not contained in the string. (Warning: the command counts the lines matching the argument of the grep command. When there are more than one line matching, it returns some value greater than 1).

You can capture the result of the command with a shell variable:

```
INSTR=`echo "Mary had a little lamb." | grep -c "little"`
```

Then you can do a test on the result:

```
if [ "$INSTR" = "0" ]; then
  # string not found
else
  # string found
fi
```

Hope, this helps. If anything should not work, just ask again. I wrote this from my mind. And you can easily make mistakes when not testing properly.

I could imagine that there is an easier solution to that, but this is what I normally use.

quirks

---

### Post by J05HYYY on 2008-04-17
No sorry i think you misunderstood the question. Let me rephrase it: 

If I had the phrase "Mary_had_a_little_lamb", and I wanted to find the position of "little" the result would be 11 as this is the beginning of the word "little" ... if you catch my drift?

---

### Post by quirks on 2008-04-17
Ah, sorry. Now I understand. I have programmed in quite a number of languages and all of them implement it a little differently. For your problem, you can use the following command (I didn't know it until now either):

```
expr index "Mary had a little lamb." "little"
```

This would return 12.

I found it here: [http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

Hope, this helps,
quirks

---

### Post by ScorpKing on 2008-04-17
look at [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by J05HYYY on 2008-04-17
when i search for "had" in the sentence
It finds the first instance of the any letter in the word "had"
eg. the letter "a"
and results in 2
whereas
i want to search for the whole word
giving the result as 6

... can this be done? :(

---

### Post by mbadawi23 on 2008-04-17
> **quirks said:**
> Hi J05HYYY,

You can capture the result of the command with a shell variable:

```
INSTR=`echo "Mary had a little lamb." | grep -c "little"`
```

Then you can do a test on the result:

```
if [ "$INSTR" = "0" ]; then
  # string not found
else
  # string found
fi
```



Is it possible to pass in the string as parameters to the code you provided?

---

### Post by ghostdog74 on 2008-04-17
```

# echo "Mary_had_a_little_lamb" | awk -F"_" '{ match($0,"lamb");print RSTART}'
19

```

---

### Post by quirks on 2008-04-18
> Is it possible to pass in the string as parameters to the code you provided?
That should be fairly easy: just introduce two more variables:

```
SEARCH_STRING="Mary had a little lamb."
SEARCH_FOR_PATTERN="little"
```
and replace the hardcoded strings with these variables in the command I gave to you:

```
INSTR=`echo "$SEARCH_STRING" | grep -c "$SEARCH_FOR_PATTERN"`
```
If you want, you can write a bash function for that, too. You will find plenty of tutorials on how to do that on the Internet.

---

### Post by J05HYYY on 2008-04-18
Thank you everyone!

it seemed to work with the :)

# echo "Mary_had_a_little_lamb" | awk -F"_" '{ match($0,"lamb");print RSTART}'

---

### Post by J05HYYY on 2008-04-18
Couldn't get the following to work though :S
```

lambstring="lamb"
sentence="Mary_had_a_little_lamb"
echo "$sentence" | awk -F"_" '{ match($0,"$lambstring");print RSTART} '

```

... whoops double posted

---

### Post by ghostdog74 on 2008-04-18
> **J05HYYY said:**
> Couldn't get the following to work though :S
```

lambstring="lamb"
sentence="Mary_had_a_little_lamb"
echo "$sentence" | awk -F"_" '{ match($0,"$lambstring");print RSTART} '

```

... whoops double posted

awk's variable is not the same as shell. you have to go through another layer of interpolation, or use the -v option of awk
```

echo "$sentence" | awk -F"_"  -v lambstring=$lambstring '{ match($0,lambstring);print RSTART} ' 

```

---

### Post by J05HYYY on 2008-04-19
that certainly did the job, cheers :)

---

### Post by Testing_Yorsh on 2008-05-13
Hey Everyone:

I'm trying to do something similar here, let know if you can help me out.

I'm looping thru a data file looking for corrupted files using the checkfile.x utility.

So I'm using the following script:

[B]# Goes thru the data files
for FILE in *.df
do

    # Checks each of the files and stores the result
    FILE_W_ERR=`checkfile.x $FILE`

    #Looks for the Err message in the return value of checkfile
    INSTR=`echo "$FILE_W_ERR" | grep -c "Err"`

    # Validate if the checkfile found any errors
    if [ "$INSTR" -ne "0" ]
    then

        # Display file with possible Error
        echo $FILE_W_ERR
        echo #INSTR

    fi

done[/B]

And as a result it displays all the data files (with their respective result), but what I'm trying to do is that the script only displays the files with "Error". That's what it's all about.

It obviously not working, I need assistance. :confused:

Can anyone help ???

Thanks for your time.

---

### Post by ghostdog74 on 2008-05-15
first, what is checkfile.x?? is it a shell script?? or a compiled program? Secondly, you don't have to specifically check for error using extra if/else because grep already gives you that.
```

checkfile.x $FILE | grep -c "Err"

```

---

### Post by Testing_Yorsh on 2008-05-15
checkfile.x is a compiled programm not a shell script, it returns a string like this:

File: kapyhour.df - start search
File: kapyhour.df - Last record is NOT a ZZZ record
File: kapyhour.df has 90 records
File: kaseitem.df - start search
File: kaseitem.df has 176 records
File: kasvehcl.df - start search
File: kasvehcl.df has 570 records

And i'm trying to find those files that have an "Error" message or a "NOT a ZZZ" message. After I find them I need to displayed them. So the user knows which files need to be fixed.

Thanks for you time !

---

### Post by husseincoder on 2008-05-15
> **J05HYYY said:**
> Thank you everyone!

it seemed to work with the :)

# echo "Mary_had_a_little_lamb" | awk -F"_" '{ match($0,"lamb");print RSTART}'

u can use the expr command to do so

index=y=$(expr match "Mary_had_a_little_lamb" '.*little' - $(expr match "little" '.*'))
echo $index # 11

---

### Post by ghostdog74 on 2008-05-16
> **husseincoder said:**
> u can use the expr command to do so

index=y=$(expr match "Mary_had_a_little_lamb" '.*little' - $(expr match "little" '.*'))
echo $index # 11

little starts from index 12. A shorter version
```

# s=Mary_had_a_little_lamb
# echo `expr index "$s" little`
12

```

---

### Post by Testing_Yorsh on 2008-05-16
hhhmm !

Well it's returning "0", check this out.

[B]for FILE in *.df
do

FILE_W_ERR=`checkfile.x $FILE`

echo `expr index "$FILE_W_ERR" ZZZ`

done[/B]

 .. . . . . .  :  S

---

### Post by Testing_Yorsh on 2008-05-16
Oh and BTW, this is what I get from the checkfile.x:

0
File: kcapo.df - start search
File: kcapo.df has 665 records
0
File: kcardbin.df - start search
File: kcardbin.df has 13 records
0
File: kcasister.df - start search
File: kcasister.df - Last record is NOT a ZZZ record
File: kcasister.df has 1 records


It should had only displayed this record :
File: kcasister.df - Last record is NOT a ZZZ record

---

### Post by J05HYYY on 2008-06-09
> **husseincoder said:**
> u can use the expr command to do so

index=y=$(expr match "Mary_had_a_little_lamb" '.*little' - $(expr match "little" '.*'))
echo $index # 11

plus one to the result and it works - black box tested with lamb and little

here is the ["non-linux specific"]("http://cr.yp.to/docs/unixport.html") version which takes this into account:

```

index=$(expr "Mary_had_a_little_lamb" : '.*little' - $(expr "little" : '.*') + 1)
echo $index

```

---

