---
title: "How can I get this bash script to work?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Troubled on 2007-02-10
I'm rather new to Linux and I'm trying to write some scripts to help me run commands at startup. A portion of one is posted below:

```

#!/bin/bash
# Generates a random name.

#Let's create an alphabet matrix:
ABC="ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"
MATLEN=${#ABC}	#Gets length of ABC

#Now generate a random name:
RUNS=0		#Runs of the loop
LENG=8		#Length of the name

while [ $RUNS -le $LENG ]		
do
	POS=$RANDOM%$MATLEN+1
	GET=${ABC:$POS}
	NOM=$NOM$GET
	let "RUNS += 1"
done

#Finally, display the result:
echo $NOM

```

I also have one that generates a hex string, using some code from [http://linuxreviews.org/beginner/abs-guide/en/a16272.html#PW:](http://linuxreviews.org/beginner/abs-guide/en/a16272.html#PW:)

```

#!/bin/bash
#Let's create a hex matrix:
MAT="0123456789ABCDEF"

#Now generate a random hex string:
RUNS=0		#Actual runs of the loop
COLN=:		#Use this for a colon

while [ $RUNS -le 10 ]			#Make ten pairs of hex values
do
	while [ "${x:=1}" -le 2 ]	#Make the actual pairs
	do
		PAIR=$PAIR${MAT:$(($RANDOM%${#MAT})):1}$COLN
		let x+=1
	done
HEX="$HEX$PAIR"
let RUNS+=1
done

#Finally, display the result.
echo $HEX

```

Apparently the stuff inside the while loop is a bad substitution, but I have no clue as to how to fix it -- I'm directly following the Advanced Bash-Scripting Guide from [http://linuxreviews.org/beginner/abs-guide/en/index.html](http://linuxreviews.org/beginner/abs-guide/en/index.html).

Any help is appreciated. Thanks!

---

### Post by nickoli_02 on 2007-02-10
Not really sure, but you may get a better response in one of the dev forums if no one answers here. Just a thought ;)

---

### Post by jpkotta on 2007-02-10
For the first one, you should change the first two lines in the body of the while:
```
	POS=$(($RANDOM%$MATLEN+1))
	GET=${ABC:$POS:1}
```

So that GET is a single character and POS is a number instead of a string.

For the second, the main problem is that PAIR should be set to nothing before the inner while, so that it's different every time.  Also, COLN should be appended to HEX, not PAIR.

---

