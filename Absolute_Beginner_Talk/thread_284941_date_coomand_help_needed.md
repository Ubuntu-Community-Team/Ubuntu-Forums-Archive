---
title: "date coomand help needed"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by apjone on 2006-10-26
Hi I am trying to write a piece of code to check file's created in the last hour, I tried 
```

date --date=`1 hour ago` 

```

And that dosent work, just gives me todays date @ midnight

I have read the man page and done some googling , but have found nthing, pls help

---

### Post by bsussman on 2006-10-26
pure shell date arithmetic is cumbersome and ugly.  For more: [http://www.askdavetaylor.com/date_math_in_linux_shell_script.html](http://www.askdavetaylor.com/date_math_in_linux_shell_script.html)

You might be happier in perl, php, python or practically any other language.

Try searching for code already written - there are many solutions already coded

---

### Post by DevNull11 on 2006-10-26
Try using the find command.
> # find [directory] -mmin 60

---

