---
title: "Sending mail in PHP with Ubuntu"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by alecwh on 2008-03-31
Hello!

I'm using Ubuntu 7.10 Gusty, and I'm trying to send mail with PHP on my localhost, but it's not working. I'm not getting any error messages or anything.

Can someone help me out? What should I do?

---

### Post by hyper_ch on 2008-03-31
do you have a mail server installed? sendmail/postfix for example?

---

### Post by alecwh on 2008-03-31
I have sendmail installed (i think). How do I check?

---

### Post by alecwh on 2008-03-31
Ok, I just installed sendmail, and now when I go to my PHP mail(); page (that sends mail), the page just sits there, loading. Here is my code:

[PHP]<?php

$to = 'aleckjwh@gmail.com';
$subject = 'subject goes here';
$body = 'body goes here';
$header = 'From: me@domain.com';
$params = '-fme@domain.com';

$success = mail($to, $subject, $body, $header, $params); 

?>[/PHP]

---

### Post by hyper_ch on 2008-03-31
to check use a simplified version:
```

<?php
$to = 'recipient@mail.com';
$subject = 'subject';
$message = 'message';

mail($to, $subject, $message);
?>

```

and if that does not work, look at the apache logs and whether phpinfo() says mail is loaded...

---

