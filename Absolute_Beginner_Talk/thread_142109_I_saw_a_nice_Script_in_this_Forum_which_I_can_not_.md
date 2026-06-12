---
title: "I saw a nice Script in this Forum which I can not Find..."
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-09
Hello All !!!

I saw a nice Script the other day, which I can NOT find:
It was 4-5 lines & Started with:


if ...blah ...blah

... blah
... blah

else echo "Sorry only the root user can do this"

fi


What it did was, check if somebody is root:
If YES, continue running the script commands.
If NOT, just print a message "Sorry only the root user can do this".

I saw it in this Forum, but I can not find it...

It somebody finds it, can you please provide the article# or just copy & paste here?

Thanks.

---

### Post by Pragmatist on 2006-03-11
This will do it:

#!/bin/sh

# Test to determine who is firing this script

set USER = whoami

if [ $USER = "root" ]; then
   echo do a bunch of stuff for root
else
   echo Only root can do that
fi

---

