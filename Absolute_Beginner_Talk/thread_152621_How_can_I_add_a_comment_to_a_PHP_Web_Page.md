---
title: "How can I add a comment to a PHP Web Page?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-30
Hello!

I have the following Web Page I created:

<html>

   <head>
        <title> A PHP script including HTML </title>
   </head>

   <body>
        <b>
                <?php echo "hello world"; ?>
        </b>
   </body>

</html>

I want to Add the following comment: "A script from my Book - page 81."

I have tried using:

1. # A script from my Book - page 81.
2. // A script from my Book - page 81.
3. /* A script from my Book - page 81. */

None of the above 3 commenting methods work!!!

What "sign" should I add in front of the Text, so that the Text does NOT get printed on my PHP Web Page?

Thanks.

---

### Post by Zeroangel on 2006-03-30
php code is something like this
[php]<?php
global $stuff
// this is a comment
/* this is a multi-line comment
   P.S. Ubuntu rocks! */
function usebrowserhacks() {
if $stuff { do things }
else
{ do other things }
?>[/php] Inside of *that* type of code is where you use the // and /* */ comments. But what you're trying to do is add comment inside of HTML code. In that case use
```
<!-- this is my comment -->
```

---

### Post by dvarsam on 2006-03-30
Thank you for your Reply!!!

You were right!!!

By mistake, I was adding the comment to the "html" part of my Web page.

Thanks!

---

