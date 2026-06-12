---
title: "Bash script your post."
date: 2009-10-25
forum: Cafe Games
---

### Post by dragos240 on 2009-10-25
echo "Hello"

echo "Make a few posts using your bash scripting skills"

---

### Post by Penguin Guy on 2009-10-25
echo 'Fail.'

---

### Post by tom66 on 2009-10-25
for i in "One" "Two" "Three" "Four" "Five"
do
    echo "A $i... "
done
echo "That is all."

---

### Post by RiceMonster on 2009-10-25
#!/bin/bash
THIS_THREAD="lame"
if [ $THIS_THREAD="lame" ]; then
echo lame thread is lame
fi

echo "What's with the random fi at the end of your post?"

---

### Post by dragos240 on 2009-10-25
> **RiceMonster said:**
> #!/bin/bash
THIS_THREAD="lame"
if [ $THIS_THREAD="lame" ]; then
echo lame thread is lame
fi

echo "What's with the random fi at the end of your post?"

No idea. I just put it there.

---

### Post by diesch on 2009-10-25
```
echo 'h+225 =582*A'|tr '[A-z!-@]' '[!-z]'
```

---

### Post by Joeb454 on 2009-10-25
```
#!/bin/bash

THREAD=http://ubuntuforums.org/showthread.php?t=1300739
FORUM="Cafe Games"

if [$FORUM == "Community Cafe"]; then
    echo "[noparse][Thread]($THREAD)[/noparse] moved to $FORUM"
fi
```

:)

---

### Post by Penguin Guy on 2009-10-25
> **diesch said:**
> ```
echo 'h+225 =582*A'|tr '[A-z!-@]' '[!-z]'
```
```
echo 'l52 M w582*G9 359: )5362/)':+* Gh+225 w582*G 685-8'3 +<+8N' | tr '[A-z!-@]' '[!-z]'
```

---

### Post by NoaHall on 2009-10-25
> **Joeb454 said:**
> ```
#!/bin/bash

THREAD=http://ubuntuforums.org/showthread.php?t=1300739
FORUM="Cafe Games"

if [$FORUM == "Community Cafe"]; then
    echo "[noparse][Thread]($THREAD)[/noparse] moved to $FORUM"
fi
```

:)

That wouldn't work ;) You've set the forum already, so you'd be comparing it to something which won't be true. And if it's equal to "Community Cafe", it would be moved to there ;)

---

### Post by Penguin Guy on 2009-10-25
> **NoaHall said:**
> That wouldn't work ;) You've set the forum already, so you'd be comparing it to something which won't be true. And if it's equal to "Community Cafe", it would be moved to there ;)
Not to mention the multiple syntax errors. :P Try this:
[PHP]#!/bin/bash

THREADURL="http://ubuntuforums.org/showthread.php?t=1300739"
THREADNAME="Bash Script Your Post"
OLDFORUM="Community Cafe"
NEWFORUM="Cafe Games"

if [ "$OLDFORUM" == "Community Cafe" ]
then
    echo "[$THREADNAME]($THREADURL) moved from $OLDFORUM to $NEWFORUM"
fi [/PHP]

---

### Post by Joeb454 on 2009-10-25
I didn't think it would work, so I sort of gave up half way through. Either way, you got the point

---

### Post by amingv on 2009-10-25
#!/bin/bash

#echo "Ha ha! You cannot see this message."
#echo "Finally, I managed to write a perfectly invisible post."
#echo "I bet you all must be wondering how I skipped the post minimun lenght filter."
#echo "I can taste the awe and disbelief in your faces already."

---

### Post by dragos240 on 2009-10-25
> **amingv said:**
> #!/bin/bash

#echo "Ha ha! You cannot see this message."
#echo "Finally, I managed to write a perfectly invisible post."
#echo "I bet you all must be wondering how I skipped the post minimun lenght filter."
#echo "I can taste the awe and disbelief in your faces already."

Orly?

---

### Post by Bachstelze on 2009-10-25
```
yes this thread is stupid
```

---

### Post by dragos240 on 2009-10-25
> **Bachstelze said:**
> ```
yes this thread is stupid
```

Orlynao?

---

### Post by amingv on 2009-10-25
> **dragos240 said:**
> Orly?

```
-bash: Orly: command not found
```

---

### Post by Penguin Guy on 2009-10-25
> **amingv said:**
> #!/bin/bash

#echo "ha ha! You cannot see this message."
#echo "finally, i managed to write a perfectly invisible post."
#echo "i bet you all must be wondering how i skipped the post minimun lenght filter."
#echo "i can taste the awe and disbelief in your faces already."&#65279;

---

### Post by Gwasanaethau on 2009-10-27
[php]#!/bin/bash
echo 'S;-{D}'
aplay ${HOME}/sounds/laugh.spx
exit 0[/php]

---

### Post by LinuxGuy1234 on 2009-10-27
```
#!/usr/bin/perl
##!/bin/bash

#echo I broke the rules
print "Hmmm";

#echo You suck
print "Dummy! Banned for 12 months!";

```

Coversation between Perl and bash.

---

### Post by dragos240 on 2009-10-28
Would making multiple programming languages in a post be better than just BASH?

---

### Post by jwbrase on 2009-10-30
#!/bin/bash
cat $0

---

### Post by jwbrase on 2009-10-30
> **Penguin Guy said:**
> ```
echo 'l52 M w582*G9 359: )5362/)':+* Gh+225 w582*G 685-8'3 +<+8N' | tr '[A-z!-@]' '[!-z]'
```

#!/bin/bash
sudo apt-get install malbolge
sudo apt-get install intercal

---

