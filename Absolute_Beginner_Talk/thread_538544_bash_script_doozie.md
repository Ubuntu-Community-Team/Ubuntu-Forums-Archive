---
title: "bash script doozie"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by ronald.higgins on 2007-08-30
Quick Q for you chaps.

i'm playing with "seq" in a for loop but i need seq to pad a '0' to the single digits ie.

for var in `seq 1 10'; do echo $var;done

1
2
3
4
5
6
7
8
9
10

But i actually need the output to be 

01
02
03
04
05
06
07
08
09
10

Any ideas ?

rH

---

### Post by yabbadabbadont on 2007-08-30
Short answer, "man seq".  :D

Long answer "seq -w 1 9" does no padding, "seq -w 1 99" pads with one zero if needed, "seq -w 1 999" adds two leading zeros if needed.

---

### Post by bashologist on 2007-08-30
Use printf? Printf is more portable and it's in other languages as well. [http://www.cplusplus.com/reference/clibrary/cstdio/printf.html](http://www.cplusplus.com/reference/clibrary/cstdio/printf.html)
```
for i in $(seq 10); do printf "%02d\n" $i; done
```

---

### Post by ronald.higgins on 2007-08-30
:P

Thanks... been there already :)

Yep, padding with the -w works when the end point has 2 digits ie. 14, but this doesnt work when
the start and end are both single digits ie. 1 -> 9.

Which is how the question came about :)

---

### Post by yabbadabbadont on 2007-08-30
> **ronald.higgins said:**
> :P

Thanks... been there already :)

Yep, padding with the -w works when the end point has 2 digits ie. 14, but this doesnt work when
the start and end are both single digits ie. 1 -> 9.

Which is how the question came about :)

Use bashologist's solution then.  ;)

---

### Post by ronald.higgins on 2007-08-30
> **bashologist said:**
> Use printf? [http://www.cplusplus.com/reference/clibrary/cstdio/printf.html](http://www.cplusplus.com/reference/clibrary/cstdio/printf.html)
```
for i in $(seq 10); do printf "%02d\n" $i; done
```
printf is more portable and it's in other languages as well.

rockstar!!!

thanks ;)

---

### Post by ronald.higgins on 2007-08-30
Well ... it almost worked ;)

```


#!/bin/bash
                                echo -e "Enter Month:\n";
                                read month;
                                echo -e "Enter Start Day:\n";
                                read start;
                                echo -e "Enter End Day:\n";
                                read end;

                                month=`printf "%02d\n" $month`;

                                for dates in `seq -w $start $end`;
                                do
                                dates=`printf "%02d\n" $dates`;
                                echo "$month/$dates";
                                done;

```

results in the below output

> 

00/01
00/02
00/03
00/04
00/05
00/06
00/07
./debug.sh: line 13: printf: 08: invalid number
00/00
./debug.sh: line 13: printf: 09: invalid number
00/00
00/10
00/11
00/12
00/13
00/14
00/15



The numbers entered for the above output was 08 for month, 1 for start date & 15 for end date.

A little googling noted that it is a bug in "printf" and the number 08 & 09 being octal something something.

So if anyone can think of another way to achive the same desired result speak away ;)

rH

---

### Post by ronald.higgins on 2007-08-31
*bump*

:)

---

### Post by ronald.higgins on 2007-08-31
nvm ;)

Fixed it with a couple if's.


> #!/bin/bash
        echo -e "Enter Month:\n";
        read month;
        echo -e "Enter Start Day:\n";
        read start;
        echo -e "Enter End Day:\n";
        read end;

        if [ $month -lt 10 ]
                then
                        month="0$month";
                else
                        :;
        fi;

        for dates in `seq -w $start $end`;
                do
                        if [ $end -lt 10 ]
                                then
                                        dates="0$dates";
                                        echo "$month/$dates";
                                else
                                        echo "$month/$dates";
                         fi;
                done;

---

### Post by mudo on 2007-09-07
printf is the function I was looking for too. Problem solved. Thank you!

---

