---
title: "Maildrop/Procmail Complete confusion"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-02-18
Why do the scripting languages for these have to be so wierd. What does all the 
*():! / \ || &&  actually do? There appears to be no logical guide anywhere,


For example:```

# .forums
if (/^From:.*site@ubuntuforums.org/ || /^From:.*ubuntu.org/)
{
    exception {
        to $DEFAULT/.Forums-Ubuntu/
    }
}
```

This means absolutely nothing to me, for example if i wanted all mail from [email]anaddress@emal.com[/email] containing the phrase "Topic reply notification" in subject but not something else etc etc, how could ido it? 

Why cant it be logical ie:
```

If (from ="*ubuntuforums*") or body contains("ubuntu|Ubuntu|UBUNTU"))
{
     to $DEFAULT/.Forums-Ubuntu/
}


```

Or even better have a frontend (like the one in thunderbird)

---

### Post by justleen on 2008-02-18
it depends what language you use, but in most languages his is waht the logical operators (thats what they're calles :) ) do:

||     =>  OR
&&   =>  AND
!      =>  NOT 
==  => EQUALS
*     => regual expression wildcard
( )   => mostly precedence operators   1 * (2+8)
/     => depends.. nothing, or preceding newline, TAB chars (like  \n \t)
\     =>  escape special char   ( if you need a litteral !   your woudl type /!  so the programm wond use is as a NOT)


again, depnas on the language..

---

### Post by dgrafix on 2008-02-18
Thanks :)

I will try looking at it again with those in mind.

Still wish there was a frontend available :(

---

### Post by dgrafix on 2008-02-19
SO if i wanted all with the words "Order" and "Sample" for example i could use:

When the mail comes in the subject could be "Order 19276: Samples"

can i use:

if (/^Subject:.*(Order)/:h )&&(/^Subject:.*(Samples)/:h )

Would that work?

---

### Post by dgrafix on 2008-02-21
Ah no, that give an error.

anyone?

---

