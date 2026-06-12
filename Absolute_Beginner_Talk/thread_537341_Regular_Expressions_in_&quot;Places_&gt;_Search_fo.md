---
title: "Regular Expressions in &quot;Places &gt; Search for Files...&quot;"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-08-28
So I'm looking for all my .tif(f) images in my photo directory and can't for the life of my figure out how to run 'locate' recursively or how to get Ubuntu's "Search for Files..." to run my regular expressions.

Yes, I found where "Search for Files..." has a 'Name matches regular expression: ________________' call, but I can't get it to work.

```
Expression Tried	Success/Failure		Notes
tif				S 			* searches inside the whole file name
/tif/				F			* don't regex expressions have to be inside two forward slashes?
$tif				F
.tif				S			* works exactly as 'tif'
$/.tif?/			F			* this one surely has to work!
```

While we're at it. How can I use 'locate' to do the same job?

I've tried:
```
~$ locate -d ./my_screenshots/ --regexp=$.tif?
```
> locate: fatal error: serach_db: read: './my_screenshots/': Is a directory
```
~$ locate -u ./my_screenshots/ --regexp=$.tif?
```
> locate: fatal error: You are not authorized to create a default slocate database!

---

### Post by Skrynesaver on 2007-08-29
your regexp is slighly incorrect. the 
[LIST]
[*]$ identifies the end of line
[*]. on its own signifies any character \. escapes this to signify the actual character "."
[*]* means any character at all[/LIST]Thus to find any tif or tiff file you could run with regexp='\.tif$' and then regexp='\.tiff$' locate's regexps are limited to basic Posix regexps and so extended regexp facilities such as {n} occurs n times, | OR etc. are unavilable.

Hope that helps

---

### Post by altonbr on 2007-08-29
> **Skrynesaver said:**
> your regexp is slighly incorrect. the 
[LIST]
[*]$ identifies the end of line
[*]. on its own signifies any character \. escapes this to signify the actual character "."
[*]* means any character at all[/LIST]Thus to find any tif or tiff file you could run with regexp='\.tif$' and then regexp='\.tiff$' locate's regexps are limited to basic Posix regexps and so extended regexp facilities such as {n} occurs n times, | OR etc. are unavilable.

Hope that helps

That makes perfect sense, thank you. It still doesn't show anything in "Places >> Search For Files..." though. Can you try running a regular expression in 'Name matches regular expression:' please?

---

