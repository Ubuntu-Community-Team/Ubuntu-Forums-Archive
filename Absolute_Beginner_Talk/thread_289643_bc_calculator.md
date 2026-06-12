---
title: "bc calculator"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2006-10-31
How do I add the "+" to positive numbers?  Like when I do 1+1, it would give me 2.  How would I make it give me +2?

When I get a result as a fraction that is less than 0, the result would be .##, how do I make it 0.##?

---

### Post by newbie22 on 2006-11-02
Please help?

---

### Post by Klaidas on 2006-11-02
A workaround would be writing a script, which would use bc, and then on the end result, check if your result is >0 and add a "+" sign :|

---

### Post by amo-ej1 on 2006-11-02
man bc learns you the following:
```

e@lap:~$ bc
bc 1.06
Copyright 1991-1994, 1997, 1998, 2000 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
scale=10
1/3
.3333333333

```

---

### Post by newbie22 on 2006-11-02
> man bc learns you the following:
See original post again...

I did not ask about the scale.

---

### Post by bsussman on 2006-11-02
I think you might be asking too much of bc and should switch to awk or perl or another tool that has more sophisticated output capabilities

---

### Post by newbie22 on 2006-11-03
I do not think it is too much.  They are very basic functions.  awk is too complicated for a newbie like me.  perl is a full language.

Earlier, a user suggested writing a simple script.

How would I add the 0 in front of .## without affect others that do not require it (eg. 1.23 would not need a 0 in front of the period) in script form?

And how do I make it add a + if there is no - present?  Can this be done with sed?  Or some other simple program?

---

### Post by Arndt on 2006-11-03
> **newbie22 said:**
> I do not think it is too much.  They are very basic functions.  awk is too complicated for a newbie like me.  perl is a full language.

Earlier, a user suggested writing a simple script.

How would I add the 0 in front of .## without affect others that do not require it (eg. 1.23 would not need a 0 in front of the period) in script form?

And how do I make it add a + if there is no - present?  Can this be done with sed?  Or some other simple program?

```
$ cat /tmp/scr

scale=6
i=10
while(--i) {
 print 5/i - 2, "\n"
}

```
```
$ bc < /tmp/scr
-1.444445
-1.375000
-1.285715
-1.166667
-1.000000
-.750000
-.333334
.500000
3.000000
```

```
$ bc < /tmp/scr | sed -e 's/\(^\|[^0-9]\)\./\10./' -e 's/\(^\|[^0-9.-]\)\([0-9]\)/\1+\2/'
-1.444445
-1.375000
-1.285715
-1.166667
-1.000000
-0.750000
-0.333334
+0.500000
+3.000000

```

This looks quite horrible, but it seems to work. If you know more about the output, for example that all numbers are at the beginning of a line, the regular expressions can be made simpler. If you want to have the regulat expressions explained, ask.

If this is something you do often, I think it's worth writing a small program for it with a comment or two documenting what it does (program could be script too).

---

### Post by bsussman on 2006-11-03
> **newbie22 said:**
>   perl is a full language.


So?

I have years of regex experience.  And I dislike perl.

Just a theory, but I find 

```
printf("%+d", $num);
```a little easier to understand and maintain than

```
 sed -e 's/\(^\|[^0-9]\)\./\10./' -e 's/\(^\|[^0-9.-]\)\([0-9]\)/\1+\2/'
```But it's your system :)

---

### Post by newbie22 on 2006-11-03
Thanks, Arndt!

Oh, one last thing:

I tried to modify the code and get sed to add a 0 in front of single digits to make it two digits.  So I used [^0-9$], but it does not seem to work.  (Not related to the fraction one above.)

```
$ echo "1" | sed 's/\(^\|[^0-9$]\)/0\1/'
01
$ echo "12" | sed 's/\(^\|[^0-9$]\)/0\1/'
012
```
As you can see, even though the ^ and $ are present to mark the beginning and end, it still responded to "12" which is not suppose to respond to [^0-9$].  What did I do wrong?

---

### Post by Arndt on 2006-11-06
> **bsussman said:**
> So?

I have years of regex experience.  And I dislike perl.

Just a theory, but I find 

```
printf("%+d", $num);
```a little easier to understand and maintain than

```
 sed -e 's/\(^\|[^0-9]\)\./\10./' -e 's/\(^\|[^0-9.-]\)\([0-9]\)/\1+\2/'
```But it's your system :)

Nice. You mean %+f, though, not %+d.

---

### Post by Arndt on 2006-11-06
> **newbie22 said:**
> Thanks, Arndt!

Oh, one last thing:

I tried to modify the code and get sed to add a 0 in front of single digits to make it two digits.  So I used [^0-9$], but it does not seem to work.  (Not related to the fraction one above.)

```
$ echo "1" | sed 's/\(^\|[^0-9$]\)/0\1/'
01
$ echo "12" | sed 's/\(^\|[^0-9$]\)/0\1/'
012
```
As you can see, even though the ^ and $ are present to mark the beginning and end, it still responded to "12" which is not suppose to respond to [^0-9$].  What did I do wrong?

^ and $ mean other things within [] than outside. ^ first inside a [] means "not", and $ means itself, a dollar character.

---

### Post by bsussman on 2006-11-06
> **Arndt said:**
> Nice. You mean %+f, though, not %+d.


Actually I didn't but I should have  :-k

---

