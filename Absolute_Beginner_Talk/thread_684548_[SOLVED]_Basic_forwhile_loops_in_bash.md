---
title: "[SOLVED] Basic for/while loops in bash"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by satman-ga on 2008-02-01
I'm totally new to bash scripting and have very little scripting experience in general. As part of teaching myself for and while loops it thought I'd write a script that generates 100 random numbers between 1 and 1000 and check each one against a number of my choice to see if it matches and how many times. I thought the following code (probably horribly constructed) would do the job. However, only one number is generated as opposed to the 100 samples I want. Suggestions?
```
#!/bin/bash
FLOOR=1
RANGE=1000
MATCH=0
number=0  
echo $1
for ((i=0;i<=999;i+=1))
	do

	while [ "$number" -le $FLOOR ]
	  do
	  number=$RANDOM
	  let "number %= $RANGE" 
	  echo $number    #see which numbers are generated
	  done

	if [ "$number" = "$1" ] 
	then let "MATCH += 1"
	fi

	done
echo $MATCH
```

---

### Post by firestormx37 on 2008-02-01
Well I am no shell script expert, but I was able to pick out a few things that may get you closer to success.

1.  You are putting " " in a lot of places that they shouldn't be.
Ex:  while [ "$number" -le $FLOOR ] --->   while [ $number -le $FLOOR ]
Ex:   if [ "$number" = "$1" ]  --->   if [ $number -eq $1 ] #also note the -eq instead of =

2.  It does not seem to like the %= that you are using.  I'm not sure what the correct syntax would be to accomplish what you are trying to do.

So, I was able to fix some things, but it doesn't work yet.  Maybe someone with more experience will be able to help you out.  Anyway, here is what I have now, after making some fixes:

#!/bin/bash
FLOOR=1
RANGE=1000
MATCH=0
number=0  
echo $1
for ((i=0;i<=999;i+=1))
	do

	while [ $number -le $FLOOR ]
	  do
	  number=$RANDOM
	  let number %= $RANGE #one error seems to be here
	  echo $number    #see which numbers are generated
	  done

	if [ $number -eq $1 ]
	then let MATCH += 1
	fi

	done
echo $MATCH

Hope this helps.

---

### Post by satman-ga on 2008-02-01
Thanks for clearing up some syntax errors there. I finally figured it out. Stupid mistake.
The while loop which generated the numbers depended on the *number* variable to be less than the *FLOOR*. Once a number was generated once that condition was not met. So, I moved the 'number=0 line'.

```
MATCH=0
REV=0
 #### number=0 was here ###
echo $1
for ((i=0;i<=999;i+=1)); do
	number=0
	while [ $number -lt $FLOOR ]; do
	  number=$RANDOM
	  let "number %= $RANGE" 
	  echo $number    #see which numbers are generated
	  let "REV += 1"
	  done
```

Now it all works

---

