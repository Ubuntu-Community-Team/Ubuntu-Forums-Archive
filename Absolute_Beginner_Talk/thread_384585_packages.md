---
title: "packages"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by gos1 on 2007-03-14
I am getting this error whenever I try to install a package...

--------------------
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

---

### Post by Arby on 2007-03-14
Hi,

Quite a few people come across this problem. This blog post has a fix [http://codepoets.co.uk/lc_ctype_lc_messages_lc_all_locale_ubuntu](http://codepoets.co.uk/lc_ctype_lc_messages_lc_all_locale_ubuntu).

It seems you are missing a language pack, you need to install it with ```
sudo apt-get install language-pack-en
```. If that doesn't work, check the comments on that blog post. A few people make some other suggestions.

Hope that helps

Arby

---

### Post by gos1 on 2007-03-18
thanks a lot it solved my problem...

---

