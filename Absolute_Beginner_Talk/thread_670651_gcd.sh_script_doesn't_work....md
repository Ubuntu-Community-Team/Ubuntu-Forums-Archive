---
title: "gcd.sh script doesn't work..."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kantze on 2008-01-17
Hi there. I'm new to scripting in bash shell and I have this problem.
I'm trying to make a script that returns the greatest common divisor of two integer numbers according to Euclid's algorithm...

Here is, what I've done:
```

#!/bin/bash

m=$1
n=$2

while [ "$n" != 0 ]
do
if [ "$m" -gt "$n" ]; #line 8
then m=$m-$n
else n=$n-$m
fi
done
echo $n

```
and I get an error message: line 8:integer exrpession expected
I run the gcd.sh writing in the terminal
```
 ./gcd.sh 14 28 
``` where 14 and 28 are integers, right?
So, what's the problem? Could you please tell me what should I write?

---

### Post by PeterJS on 2008-01-17
You've got a few problem.

The first one is just a stylistic critique, generally when doing bash scripting you want your variable names to be in all capital letters so they stick out and are easy to see, so using N and M instead of n and m.

Second and this is one is your biggest, bash (itself) doesn't do arithmetic. So the expression:
```

M=$M-$N

```
is processed as: set the string M equal to the string containing the characters 1,4 (by variable substitution for $M), - (from the literal character in the script), 2,8 (from the variable substitution for $N), for a final string of "14-28" which is not a number.

To get bash to do arithmetic you want to use the mathematic expression program expr. expr takes 3 parameters: LeftValue Operator RightValue. expr writes it's answer to standard output, so to capture that to put back in to a variable, wrap the whole expression in back ticks.

And lastly you've got a logic bug in your final output. Since N is going to zero the answer you want is going to be in M.

Final product:
```

#!/bin/bash

M=$1
N=$2

while [ "$N" != 0 ]
do
if [ "$M" -gt "$N" ]; #line 8
then
M=`expr $M - $N`
else
N=`expr $N - $M`
fi
done
echo $M

```

---

### Post by Hospadar on 2008-01-17
A script like this might be better written with perl or python, although I suspect you're just doing it to learn more about bash, so that's kind of a moot point I suppose.

---

