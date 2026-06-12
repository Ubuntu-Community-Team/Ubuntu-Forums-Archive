---
title: "PHP mail() not working. Php.ini config?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jodyflorian on 2007-07-17
Hi,

I'm a total beginner *nix, and okish at PHP.

I had my development server on a 5.x ubuntu, now moved to 6.06 on recommendations.

I can run php scripts, and access the mysql database, pages serve fine from apache2. 
However, mail() returns false.

I didn't realise this but sendmail isn't available on 6.06? I tried aptitude, it wasn't listed. And postfix is automatically installed? (Well, it seems I have got it anyway).

I assume either postfix's configurations, php.ini or both need configuring?

I was hoping someone could help? what might need changing? And would be really good if you know what to change it to!

Thanks

Jody

---

### Post by tarek on 2007-07-18
I used postfix to send emails. I used my ISP's SMTP service.

Reconfigure postfix:
```
sudo dpkg-reconfigure postfix
```

Choose **Internet with smarthost** and hit enter until you get to: **SMTP relay host** and enter your smtp service.
For example: my ISP is eastlink.ca so the smtp service is **smtp.eastlink.ca** and enter ... to the end.

I had to restart the computer in order to get it to work. Try the mail function now.

TK

---

