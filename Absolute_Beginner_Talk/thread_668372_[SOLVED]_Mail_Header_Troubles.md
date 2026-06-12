---
title: "[SOLVED] Mail Header Troubles"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by mrhinman on 2008-01-15
I'm having trouble with a PHP mail script not doing things right.

My code is:

```
$headers = "From: $office\n\rContent-type: text/html; charset=iso-8859-1";

mail($mailto, $msgSubject, $msgBody, $headers);
```

Where $msgBody is HTML code.  All the recipient gets is the code, not the formatting.

Is there something I'm missing in my Apache installation?

Apache 2/ PHP 5/ Ubuntu 6.06 Server

--
Matthew

---

### Post by mrhinman on 2008-01-15
Oh, and I'm using PostFix.

---

### Post by mrhinman on 2008-01-15
Okay, I rearranged the code a bit, but now I can't get the "From" field to go with the header.  It's either the "Content" or the "From" but not both!  I'm going crazy here.

```

$headers = "Content-type: text/html; charset=iso-8859-1\n\r";
$headers .= "From: $office\n\r";

```

---

### Post by mrhinman on 2008-01-15
I realized the "\n\r" should have been "\n".

---

