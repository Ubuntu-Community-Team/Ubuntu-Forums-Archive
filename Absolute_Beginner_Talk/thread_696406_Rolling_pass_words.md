---
title: "Rolling pass words?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-14
so for ultimate security I would like to have a rolling pass word on my computer
(yes i know over kill but for fun :)  and latter who knows )
so some thing like depending on the date the time of the day. my password will always be different 
This way if i am bissy and my brother would like to get on my computer for me i can just tell him the pass word but an hour latter if he tries to get back on it will not work
because the pass word would have changed
also would like 2 user one for me set up just the way i have it now
the other one will log off of the computer after a set amount of time say a half hour 
in this way assuring that my brother will not be able to just stay on the computer
and this user would also have the same permitions and home as my user and the same rolling password just off by a letter so i dont have to figure out 2 skeems

---

### Post by marufaberlin on 2008-02-14
Hi,
You might like to write a bash script that changes the password, reading some random combination from /dev/urandom and stripping some non-ascii characters from that random string. Then have the bash script run daily by cron.
Everything clear so far?:-)

---

### Post by marufaberlin on 2008-02-14
Hang on - You want your own password changed as well?
Why don't you have a fixed password - you have to access the computer *somehow*. The bash script could write the rolling passwords into a log file, where you could look them up and give them to your brother. 
The log file should not be readable (or writable) by your brother:)

---

### Post by marufaberlin on 2008-02-14
A friend of mine, sandman94 in this forum, wrote a shell script that generates random passwords. You might want to have a look at it. 

 Here is an adapted version of it.

(adapted from [http://gnusecurity.wordpress.com/](http://gnusecurity.wordpress.com/))

```
#!/bin/sh
$PASS = dd if=/dev/urandom count=1 2> /dev/null | uuencode -m -| sed -ne 2p | cut -c-8
cat $PASS >> logfile
passwd yourbrothersusername $PASS

```

run that as a daily cron job and you'll be fine. Look up the password in the logfile and give it to your brother.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-14
i am sorry, should have been more clear
NOT random   want a system 
ex.
today is the 2/14/08 and the time is 7:22
so computer looks at list
months
1    bird
2    fly
3    cow
ext.

and then the day of the month, would like to just stick that on there but so 
1 = a
2 = b
3 = c
ext.
or some other system
so today the 14 is ad

and then they year just leave as 08

the time is 7 so just add a 7 on the end
or sumthing like that
and my pass word would be
flyad087
but this would only be the pass word for an hour an hour latter it would be
flyad088
and then on the day 3/1/09 @ 2
it would be 
cowa092
get the idea
so there will always be a new password that i could figure out easyly with out looking at a list and then give to my "brother" or if i need to tell someone what my password is over the phone or in a public place

This would have to run at startup so that

---

### Post by marufaberlin on 2008-02-15
OK... I get the idea.
You can find out the day of the numbers using
```

$DAYOFTHEMONTH=date +%d
$MONTHOFTHEYEAR=date +%m
$YEAR=date +%y
$HOUR=date +%H

```
You can replace these numbers with the following command:
```
head -nx filename |  tail -n 1
```
where you replace x with the number.

---

### Post by marufaberlin on 2008-02-19
I'm sorry, I should have made my meaning clearer. What I wanted to say is this:
You create a file, call it *dayofthemonths* and insert something like this:
```

a
b
c
d
e
f
g
h
i
aa
ab
ac
ad
ae
af
ag
ah
ai
ba
bb
bc
bd
be
bf
bg
bh
bi
ca
cb
cc
cd
ce
cf
cg
ch
ci
da

```
That gives you 31 lines (max. 31 days in the month).

Similarly, you create a file like this, call it *months*:
```

bird
fly
cow
...

```
with 12 lines.

Then use the command I described in my previous post to retreive the appropriate line, string these lines together, add the [COLOR="blue"]$YEAR [/COLOR]and the [COLOR="Blue"]$HOUR[/COLOR] variable to the end.

Pass that string to a passwd command in a bash script and run that by cron.

---

### Post by Golem XIV on 2008-02-19
I'm sorry if this is a stupid question, but why don't you just create an account for your brother on your computer?  Don't give him sudo powers and he won't be able to screw up anything outside of his $HOME folder...

---

### Post by marufaberlin on 2008-02-20
Read his first post. Maybe you can see his point about him overkilling??? :lol:

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-25
Thanks guys

---

