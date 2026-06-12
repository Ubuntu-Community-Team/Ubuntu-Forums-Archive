---
title: "bad package build?"
date: 2014-05-20
forum: Any Other OS
---

### Post by LastDino on 2014-05-20
I downloaded flareget from their website and when I tried to install it, software center gives me this error shown in screen-shot, any ideas?

[ATTACH=CONFIG]253312[/ATTACH]

---

### Post by buzzingrobot on 2014-05-20
That's a locale issue, as reported here ([http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue](http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue)) along with solutions that worked for some people and did not work for others.

Here's the documentation on locales, which sadly begins by admiting there's "precious little" documentation on locales:  [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale).

Wild guess:  Click on Systems Settings->Language Support.  If it complains that language support is incompletely installed, allow it to complete  the install.

---

### Post by LastDino on 2014-05-21
> **buzzingrobot said:**
> That's a locale issue, as reported here ([http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue](http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue)) along with solutions that worked for some people and did not work for others.

Here's the documentation on locales, which sadly begins by admiting there's "precious little" documentation on locales:  [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale).

Wild guess:  Click on Systems Settings->Language Support.  If it complains that language support is incompletely installed, allow it to complete  the install.

That is what I thought to so I looked up my locale settings by typing locale in terminal.

```
&#9492;&#9472; $ &#9654; locale
LANG=en_IN
LANGUAGE=en_IN:en
LC_CTYPE="en_IN"
LC_NUMERIC="en_IN"
LC_TIME="en_IN"
LC_COLLATE="en_IN"
LC_MONETARY="en_IN"
LC_MESSAGES="en_IN"
LC_PAPER="en_IN"
LC_NAME="en_IN"
LC_ADDRESS="en_IN"
LC_TELEPHONE="en_IN"
LC_MEASUREMENT="en_IN"
LC_IDENTIFICATION="en_IN"
LC_ALL=

```

I didn't see anything odd, and yes, I did complete the installation of language support from settings as well. Problem still persists.

Do I need to change anything in particular from above?

---

### Post by adnan-kamili on 2014-05-21
It is actually not a locale issue. It seems Google chrome or chromium is not installed on your Linux distro. You can ignore the warning or use GDEBI to install the pkg. Alternately, from command line: 

```
sudo dpkg -i package-name-of-flareget
```

---

### Post by LastDino on 2014-05-21
> **adnan-kamili said:**
> It is actually not a locale issue. It seems Google chrome or chromium is not installed on your Linux distro. You can ignore the warning or use GDEBI to install the pkg. Alternately, from command line: 

```
sudo dpkg -i package-name-of-flareget
```

There is chromium installed on system.

---

