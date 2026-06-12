---
title: "[SOLVED] Enable sending mail"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Roanoke on 2008-02-03
I am using the latest version of all my software and I would like to know how I can send email from PHP using the mail() function. Before I installed sendmail, I got the error "Sending mail to remote domains is unsupported", now I get "The IP you're using to send mail is unauthorized."

---

### Post by oerd on 2008-02-04
Do you connect to localhost when you are sending the mail through php?

Other than that you could try:

1. Is sendmail in /usr/sbin/sendmail (where I believe php tries to find it)?
2. Is sendmail at least in your path?
3. Is php allowed to run sendmail?

---

### Post by Roanoke on 2008-02-05
> **oerd said:**
> Do you connect to localhost when you are sending the mail through php?

Other than that you could try:

1. Is sendmail in /usr/sbin/sendmail (where I believe php tries to find it)?
2. Is sendmail at least in your path?
3. Is php allowed to run sendmail?

1. Yes. If I type that in the command line, it shows a blank screen.
2. Yes.
3. Not sure how to check that.

---

### Post by emarkd on 2008-02-05
Can you use sendmail to send from the terminal?  Testing that will at least allow you to narrow your problem to either sendmail or php?

---

### Post by Roanoke on 2008-02-05
> **emarkd said:**
> Can you use sendmail to send from the terminal?  Testing that will at least allow you to narrow your problem to either sendmail or php?

Sorry, but I'm not sure how I should test that.

Edit: If I type

echo xyz | sendmail --@-.-

With a real email address it tells me:

/home/roanoke/dead.letter... Saved message in /home/roanoke/dead.letter.

---

### Post by emarkd on 2008-02-05
Well, I'm not either. :)  If I've used sendmail it's been a long time and I don't remember the syntax.  Maybe check the man page?

```
man sendmail
```

---

### Post by dcstar on 2008-02-05
> **Roanoke said:**
> I am using the latest version of all my software and I would like to know how I can send email from PHP using the mail() function. Before I installed sendmail, I got the error "Sending mail to remote domains is unsupported", now I get "The IP you're using to send mail is unauthorized."

If that is a local message, then you have a configuration issue.

I use **postfix** rather than sendmail, it seems easier to work with.

---

### Post by Roanoke on 2008-02-06
I realize where the problem is, however, I don't realize how to correct it.

---

