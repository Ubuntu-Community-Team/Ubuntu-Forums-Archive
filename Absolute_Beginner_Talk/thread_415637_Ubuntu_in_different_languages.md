---
title: "Ubuntu in different languages"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by jpvdk on 2007-04-20
Hi folks

I installed the new Feisty Ubuntu OS on my PC.
Everything works fine. Great!
The problem now is that my wife is Spanish. (this is not a problem for me :-) )
I installed the OS in English and I added my wife's account to the system.
Is it possible that when I log on to Ubuntu that I get my settings automatically in English
and when my wife logs on she gets it in Spanish.
I know that you can change the language before logging in but I want that my wife
doesn't have to do all this. She's not that familiar with computers as I am.

thx in advance

Jp

---

### Post by jpvdk on 2007-04-20
Hi folks

I installed the new Feisty Ubuntu OS on my PC.
Everything works fine. Great!
The problem now is that my wife is Spanish. (this is not a problem for me :-) )
I installed the OS in English and I added my wife's account to the system.
Is it possible that when I log on to Ubuntu that I get my settings automatically in English
and when my wife logs on she gets it in Spanish.
I know that you can change the language before logging in but I want that my wife
doesn't have to do all this. She's not that familiar with computers as I am.

thx in advance

Jp

---

### Post by oilchangeguy on 2007-04-20
please DO NOT create two posts on the same subject! 
is there a reason why your wife can't use english? is she still learning? if so wouldn't it be better for her to use english on the computer, rather than spanish?
in version 6.06 (don't know about 7.04) click system, admin, language support. from there you should be able to configure another language for different users.

---

### Post by jpvdk on 2007-04-20
sorry, I just clicked twice on my post.
My fault

Never the less, your reply doesn't answer my question.
Ubuntu means that it's for everybody, that's why all the languages are in it.
thx for the reply but I want a more fundamental answer

Jp

---

### Post by oilchangeguy on 2007-04-20
i've added to my first post. please read it again.

---

### Post by jpvdk on 2007-04-20
yep, read it.
want to know HOW it's fixed for the other account(s)
my children speak dutch, so ... other language settings for them too

I downloaded all the language support languages I need
 then what?
JP

---

### Post by jpvdk on 2007-04-20
so far, don't know how!
JP

---

### Post by userundefine on 2007-04-20
I'd be interested in hearing the answer to this too...

---

### Post by freebird54 on 2007-04-20
Not having done this, I an not sure.  However I would assume that a script running on startup in that user's account with locale=sp_sp.utf8  (or whatever the actual is!) should do the job.  Sorry not to be more specific - but not having needed this in a long time :)

Should give you a startng point though - and I'll have google out there too.  Patience!

---

### Post by freebird54 on 2007-04-20
On further research it appears that if you set environment variables to the appropriate values in the user's .bashrc (or somewhere else definitely executed) that should cause the system to respond in that language.  Here is a list of relevant variables (see man locale)

 ```
      LC_CTYPE
              Character classification and case conversion.

       LC_COLLATE
              Collation order.

       LC_TIME
              Date and time formats.

       LC_NUMERIC
              Non-monetary numeric formats.

       LC_MONETARY
              Monetary formats.

       LC_MESSAGES
              Formats  of  informative and diagnostic messages and interactive
              responses.

       LC_PAPER
              Paper size.

       LC_NAME
              Name formats.

       LC_ADDRESS
              Address formats and location information.

       LC_TELEPHONE
              Telephone number formats.

       LC_MEASUREMENT
              Measurement units (Metric or Other).

       LC_IDENTIFICATION
              Metadata about the locale information.

       This environment variable can switch against multiple locale database:

       LOCPATH
              The  directory  where  locale  data  is  stored.   In   default,
              /usr/lib/locale is used.

```

I would expect that only some of them should be changed in your situation, as money and time and such would be for your country, not your language?  Hope this helps.

EDIT:  Example would be adding a line to /home/username/.bashrc

```
LC_MESSAGES=sp_sp.utf8
```

That would be my first try anyway. Let me know how it goes!

Here is a link with more expertise than I have :)

[https://wiki.ubuntu.com/environment_variables#head-5acb6412a6617ddff48fc43614b9535e54d8d67d](https://wiki.ubuntu.com/environment_variables#head-5acb6412a6617ddff48fc43614b9535e54d8d67d)

---

### Post by vanadium on 2007-04-20
That is one of the great features in GNU/Linux: you install one OS and all your users can have their custom language.

On the log-on screen, there is an Options button. This will allow you to change the language for the user who is going to log in. Next time, that language will automatically be used each time that user logs in, although the login-screen stays in the "default" language, which is the language in which you performed the install (likely this can also be changed, but I don know how).

---

### Post by jpvdk on 2007-04-20
ok
will try it 2morrow, first let attend our 'ubuntu' --spanish friends 
I'll let u know it this works 

grtz

Jp

---

### Post by RCC2k7 on 2007-04-22
I just tried it in Ubuntu 7.04 and it worked. I have my main user account and the OS default in Spanish, and another user account with English.

---

### Post by userundefine on 2007-04-22
Cool, thanks for that info RCC.

---

### Post by jpvdk on 2007-04-23
Yep, it worked fine.
I installed the 3 languages (English, Dutch & Spanish).
While logging in with another account I changed the language (Options in left corner of the logon screen)
and put it to 'spanish'.
Then the system asks if this will be only for this session or default for that user.
Select Default and the user will always get his session in the selected language.

Changed back to my login and I got it in English again.

Thanks for your help all

JP

---

