---
title: "Bash scripting 'test' command problem."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by montigomo on 2008-02-23
I am trying to teach myself Linux bash scripting and I run into a problem with 'test' command execution.

This is my script:

#!/bin/sh
echo “Is it morning? Please answer yes or no”
read timeofday
echo $timeofday
if [ $timeofday = “yes” ]; then
  echo “Good morning”
else
  echo “Good afternoon”
fi
exit 0
 
And these are the results of its execution:

“Is it morning? Please answer yes or no”
**yes**
yes
“Good afternoon”

As you can see the if statement in my script doesn't test the entered value correctly.
What might be a problem?

Thank you.

---

### Post by jordanmthomas on 2008-02-23
You need to do it like this:
```
if [ $timeofday=&#8220;yes&#8221; ]; then
```
Note the lack of spaces in the test

---

### Post by montigomo on 2008-02-23
This seems to fix one part of the problem. "yes" branch executes correctly now, but "no" is still problematic.

&#8220;Is it morning? Please answer yes or no&#8221;
**no**
no
&#8220;Good morning&#8221;

---

### Post by rodo-&gt;dave on 2008-02-23
```

#!/bin/sh
echo “Is it morning? Please answer yes or no”
read timeofday
echo "["$timeofday"]"
if [ "$timeofday" = yes ]; then
    echo “Good morning”
else
    echo “Good afternoon”
fi
exit 0

```

---

### Post by jordanmthomas on 2008-02-23
edit
nevermind, rodo->dave has it

---

### Post by montigomo on 2008-02-23
rodo->dave's corrected script runs just fine! Thank you very much.

It is worth mentioning that the original problematic script was taken from a textbook "Beginning Linux programming" 4th edition by N.Matthew and R.Stones.

---

### Post by rodo-&gt;dave on 2008-02-24
You can submit errata via: 
[http://www.wrox.com/WileyCDA/WroxTitle/productCd-0470147628,descCd-view_errata.html](http://www.wrox.com/WileyCDA/WroxTitle/productCd-0470147628,descCd-view_errata.html)

or perhaps the publisher site (this is the only place I found with a quick google though).

---

