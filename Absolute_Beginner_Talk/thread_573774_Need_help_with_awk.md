---
title: "Need help with awk"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Simon1976 on 2007-10-12
I am finding this hard to word so here goes. I am relatively new to using awk and was wondering if someone could help with the following. Is there some way of getting awk to display eveything after a given value? For example, if I run a simple script that list every process a user is running and then write this out to a  flat file (I have called the file user1)  as below -

```
F S      UID   PID  PPID  C PRI NI     ADDR   SZ    WCHAN    STIME TTY       TIME COMD
  1 S   u08369  5114  5112  0 158 20  648b5c0   97  58ae040 04:03:45 pts/0     0:00 -sh
  1 S   u08369  5131  5114  1 158 20  6324d40  100  637d040 04:04:03 pts/0     0:00 -sh
2001 S   u08369  5112  5110  1 154 20  6227100  313   996000 04:03:44 ?         0:00 sshd: u08369@pts/0
  1 R   u08369  5132  5131  7 179 20  63f7080   46        - 04:04:07 pts/0     0:00 ps -xflu u08369
```

I can use awk '{print....  to extract the info I want. What I want to know is the user number ($3,) UID ($4) and then the command that's running ($15.) The problem I have is the command running could have many spaces in it (the delimiter being used) that the print command would need $15,$16,$17....using to display the full command that's running. Is there some way of saying display everything after $15 to remove the necessity of adding an indefinite amount of values in the print command? This is what I have so far - awk '{print $3,$4,$15}' user1 which displays the following -

```
UID PID COMD
u08369 5114 -sh
u08369 5131 -sh
u08369 5112 sshd:
u08369 5132 ps
```

As you can see it's missing a bit of info :( Can anyone help?

I think that's worded so it make sense. Thanks in advance for any help received.

---

### Post by Simon1976 on 2007-10-12
With a bit of experimenting I now have the following by running awk '{print $3,$4,$NF}' user1

```
UID PID COMD
u08369 5114 -sh
u08369 5131 -sh
u08369 5112 u08369@pts/0
u08369 5132 u08369
```

Slightly better but still not all the info I need.

---

### Post by ronald.higgins on 2007-10-12
Hmmm, 

I'm sure that someone else will know of a better method and they'll enlighten us both, 
but this is what i got.

ps -ef | grep 'user' | awk '{$3 ="";$4 ="";$5 ="";$6 ="";$7 =""; print }' | sed 's/ADD_5_SPACES_HERE//g'

---

### Post by nick_h on 2007-10-12
A different, but not necessarily better, method:
```
awk '{s = ""
for(i = 15; i <= NF; i++)
s = s " " $i
print $3 " " $4 s
}
' user1
```
(run from a shell script)

---

### Post by Simon1976 on 2007-10-12
Thanks to you both. Nick's suggestion seems the best option as I will be running it from a shell script. All I have to do now is figure out HOW it works ;) Cheers

---

### Post by nick_h on 2007-10-12
The script works using the fact that a field can be referenced using a variable as well as a constant.
```
i = 5
print $i
```
is the same as print $5

The script just builds up a string with a loop.  NF holds the number of fields for the record.

It might also be worth reading the manual page for ps.  The following also does what you want:
```
ps -o uid,pid,cmd -u user1
```

---

