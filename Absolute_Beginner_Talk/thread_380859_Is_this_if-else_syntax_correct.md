---
title: "Is this if-else syntax correct?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-03-10
Here it is, trying to see if my entered value $command is equal to the two words: "My Calendar":

a="My Calendar"

if [ $command = $a ] ; then
   echo "This is my calendar"
else
   echo "nothing found"
fi

exit 0

It's not working, do I use single quotes somewhere?

---

### Post by colo on 2007-03-10
You'd want to quote $a ("$a$), since it contains a whitespace, which is a part of the default IFS (internal field separator). Thus, the variable evaluates to two distinct values for `test` (which is another name for "[" you're using to begin evaluation).

---

### Post by Bagboy23 on 2007-03-10
Sorry, a little confused; do I change the $a to "$a$" ? I'm writing a shell script in Linux so it should be ok right?

---

### Post by pveith on 2007-03-10
in other words: line

```
if [ $command = $a ] ; then
```

should read 


```
if [ "$command"  = "$a"  ] ; then
```

This is nessecary because there are white spaces in your variables. So without the Quotes they would be interpreted as two instances...

---

### Post by Bagboy23 on 2007-03-10
Crap, it still didn't work. It's giving me the else statement even if the words match.

I changed it exactly the same way.

I forgot to mention that my $command is also equal to two words, for instance:

$command = my calendar

---

### Post by pveith on 2007-03-10
It didn't work with my suggestion? I ran the script sucessfully with just adding a variable for commands...

```

#! /bin/bash
command="My Calendar"
a="My Calendar"

if [ "$command" = "$a" ];
then
	echo "This is my calendar"
else
	echo "nothing found"
fi

exit 0

```

---

### Post by Bagboy23 on 2007-03-10
Pveith, I am sure I have done something very wrong. I replaced my code with yours but it keeps giving me nothing found.

Can you please post your full code?

---

### Post by Bagboy23 on 2007-03-10
Sorry Pveith, I was being stupid and typing it all in lower case. Thank you guys it worked. :)

One other thing, how can I get the same script to run again after 10 minutes?

---

### Post by pandu.rs on 2007-03-10
even though the problem is solved, there is a nice way to debug a shell script. 

try running

bash -xv <script>

For more info
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_03.html)

---

### Post by pveith on 2007-03-10
Do you want the script to run erver 10 Minutes? Then cron is your friend. See cron howto at [http://www.deluxnetwork.com/linux/guides/crons.php](http://www.deluxnetwork.com/linux/guides/crons.php)

other than that you can use the sleep command to wait for 10 Minutes in the script.

---

