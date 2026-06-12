---
title: "parse error in a script i'm working on"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by EricJosepi on 2008-02-10
Hello again, community!

I have a quick question for someone who knows a thing or two about bash scripting.

Here's the code I have:
```
#! /bin/bash
#bashscript.s
clear
echo "Eric Kinch"
date
echo PI=3.14159

echo "Please enter the current year:"
read year
echo "Please enter the year you were born:"
read birth_year
age=$(($year - $birth_year))
echo "You were born in $birth_year and are (roughly) $age years old"
echo "Please input the radius of a circle:"
read rad
radius=$(($rad*$rad))
scale=5
area=$( echo "scale=5; (($PI * $radius))" | bc )
echo "The area is $area"

```

but when it goes to the second equation, it gives me this as the ouput
```
Please input the radius of a circle:
1
(standard_in) 1: parse error
The area is 

```

Can someone help me figure out where I'm making my mistake?

---

### Post by TheBoat on 2008-02-10
I think it has a problem with you trying to multiple. Try passing it to a calculator like this:
```
echo "$rad*$rad" | bc
```

---

### Post by EricJosepi on 2008-02-10
So let me see if i have this right.  It should be

```
radius= echo "$rad*$rad" | bc
```

---

### Post by TheBoat on 2008-02-10
I don't know if that will work, but this should work:```
radius=$(echo "$rad*$rad" | bc)
```

---

### Post by asmoore82 on 2008-02-10
you don't need to actually reference($) variable names within the ``$(( ... ))'' structure

the age line should be:```
age="$(( year - birth_year ))"
```

likewise, the radius line:```
radius="$(( rad * rad ))"
```

I can't tell exactly what the rest of the code is trying to accomplish.

---

### Post by TheBoat on 2008-02-11
He is computing the area of a circle and then printing it. Area = pi * radius^2  He first squares the radius and then multiplies it to pi.  Scale = 5 means that there will be 5 digits to the right of the decimal point in the output of bc.

---

### Post by asmoore82 on 2008-02-11
... reads the **man** page on `bc` ...
Ahh, I see, why not let the heavy hitting math program do all the work? ...

```

# moved this assignment to the top of the code for ease of future changes
scale=5

...

read radius

area="$( echo "scale=$scale; $PI * ( $radius ^ 2 )" | bc )"

echo "The area is $area"
...

```

EDIT: P.S. Your original parse error can be reproduced by radius being **null** when this line executes:
```
area=$( echo "scale=5; (($PI * $radius))" | bc )
```
effectively becoming this:
```
 echo "scale=5; ((3.1459*))" | bc
(standard_in) 1: parse error
```
EDIT2: FOUND IT!!
this line is causing the problem:```
echo PI=...
```
you cannot do assignments this way in scripts.
assignments must be the first command on the line and cannot have a space on either side of the equals sign(=).

---

### Post by EricJosepi on 2008-02-11
EDIT

Thanks asmoore82!  I just saw your solution after i posted and it worked perfectly :D

---

### Post by asmoore82 on 2008-02-11
```
#!/bin/bash
#bashscript.s

#moved this assignment up here for easy access
scale="5"

clear

echo "Eric Kinch"
date
echo

PI="3.14159"

year="$( date +%Y )"
echo "The current year is $year"

echo -n "Please enter the year you were born: "
read birth_year

age="$(( year - birth_year ))"
echo "You were born in $birth_year and are (roughly) $age years old."

echo -n "Please input the radius of a circle: "
read radius

echo "Pi     is equal to $PI"
echo "radius is equal to $radius"

area="$( echo "scale=$scale; $PI*$radius^2" | bc)"

echo "The area is $area"
echo

#End of File
```

:KS

The tricky, tricky thing to remember about shell scripting is that the shell has no knowledge of numbers;
with the exceptions of "$(( ... ))" and "[ -eq/-ne/-gt/etc...]",
it only deals in strings, but it is a string processing powerhouse.

strings! hence the quotation marks all over the place,
even on would-be number assignments like "PI=..."

---

### Post by EricJosepi on 2008-02-11
Here's a fun one and this is the last question:

Is it possible to parse a variable and select only certain characters i.e. i have a word or name like "Steve" and i want to only select the v.  Can I do this in bash script or no?

---

### Post by ghostdog74 on 2008-02-11
> **EricJosepi said:**
> Here's a fun one and this is the last question:

Is it possible to parse a variable and select only certain characters i.e. i have a word or name like "Steve" and i want to only select the v.  Can I do this in bash script or no?

state more clearly what you want to do. If you want to check if there is a "v" in that string
```

s="steve"
case $s in 
  *v*) echo "found"  
    ;; 
esac

```
or assuming you know where "v" is , and wanted to check that position
```

# if [ ${s:3:1} = "v" ];then echo "found"; fi
found


```
I suggest you read the 3rd link in my sig

---

