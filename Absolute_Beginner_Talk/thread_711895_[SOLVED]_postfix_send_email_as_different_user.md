---
title: "[SOLVED] postfix send email as different user"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by ralphz on 2008-03-01
Hi

I configured postfix just fine. it sends emails. 

I use php to send emails but all sent emails have field from: www-data <myaccount@myprovider.com>.

How can i change www-data to be for example: php-test or something else.

Thanks Ralph

PS: I'm using postfix as a relay.

---

### Post by ctyc on 2008-03-02
yes

php.net/mail

---

### Post by zazuge on 2008-03-02
well not sure but you can use alias maps or canonical adress maping
[http://www.postfix.org/rewrite.html#canonical](http://www.postfix.org/rewrite.html#canonical)
hope that help

---

### Post by ralphz on 2008-03-02
Thank you all.

I had to create custom headers using additional_headers parameter for mail()

Ralph

---

