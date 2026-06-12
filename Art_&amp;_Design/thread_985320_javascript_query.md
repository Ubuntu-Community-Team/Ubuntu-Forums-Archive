---
title: "javascript query"
date: 2008-11-17
forum: Art &amp; Design
---

### Post by maclenin on 2008-11-17
Essentially, I am trying to understand how to locate the position of a number (0-9) in a string (e.g.)...

**onceuponatime.com/little_brown_monkeys_009.html**

...using lastIndexOf (or some other method)?

I have used lastIndexOf to pluck out other non-numeric pieces of the string, but I can't figure out how to locate the numbers (i.e. lastIndexOf(any numeric character)) - directly - without having to "bookend" the numbers - i.e. locate non-numeric characters ("_" or ".") on either side of the numbers.

This "bookending" method, though effective for the "monkey" example, as well as for others, would require constant maintenance as the strings changed (e.g.)...

**abcd123esdf.html**

For this reason (as well as just to know), I would like to find a single (lastIndexOf?) statement to locate numbers in any string.

I have tried...

```
var a=(monkey_string.lastIndexOf(/\d/));
document.write(a);
```

...on the "monkey" with -1 as the result....

Thanks for any guidance!

---

### Post by banago on 2008-11-18
Your site is down.

---

