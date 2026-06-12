---
title: "Can't login to online bank."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by bjstabio on 2007-11-26
I can't login to my online banking with Ubuntu.  After I enter my username, a second screen is displayed where I should be able to enter my password, but the main body of the screen is blank with just the name of my bank displayed at the top.  Login works with windows.  Please help.

---

### Post by LaRoza on 2007-11-26
It might be using flash or Java. Are they installed?

---

### Post by smartbei on 2007-11-26
The problem is almost certainly not OS related, but rather browser related. I assume you are using Firefox, and that it doesn't work for you. Try opera (available from the repos) with the same site. If that still doesn't work, you can use ies4linux to install Internet Explorer 6 on Ubuntu. See [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation) for ie4linux.

---

### Post by bjstabio on 2007-11-27
thanks smartbei.  your were right, it was browser related.  i hated to but i had to download IE.  i don't like using anything related to MS, but it appears, at least in this instance, that i have no choice.  thanks for all the help!

---

### Post by Mithrilhall on 2007-11-27
Did you try the agent switcher for Firefox? I use this on my banks website.


[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by Daveski on 2007-11-27
I hope you are both contacting your Banks and asking why they do not support Firefox seeing as it is one of the most popular browsers.

---

### Post by philinux on 2007-11-27
I have numerous accounts and not one complains about firefox. :confused:

---

### Post by ukripper on 2007-11-27
Most banks do support firefox and moreover they prefer firefox transactions between accounts

mozilla claims it is more secure than IE  [http://www.mozilla.org/support/firefox/faq#mozvsie](http://www.mozilla.org/support/firefox/faq#mozvsie)

i personally use this noscript to make it more secure [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

---

### Post by Mithrilhall on 2007-11-28
I've called my bank in the past.

They fixed it a while ago and it now works with Firefox. Actually, the tech from the bank is the one that originally recommended using the agent switcher.

---

### Post by bjstabio on 2007-11-28
Tried it.  Didn't work.

---

### Post by ukripper on 2007-11-28
> **bjstabio said:**
> Tried it.  Didn't work.

phone your bank or pay them a visit and ask why there is no support for firefox?

---

### Post by Znort_Ubern00b on 2007-11-28
which bank is it?  i use the three i use all work fine with FF.

---

### Post by DugieHowsa on 2007-12-07
I am having trouble with Citizens bank.  The odd thing is that it actually worked for a little while in Feisty,  But I have not been able to get it to work ever since I upgraded to Gutsy.  I know the browser was updated during the upgrade, but it was just a minor version upgrade to firefox, wasn't it?

And to add my two cents, I tried the user agent switcher and it didn't work either.  Where it appears to be failing is on the main page, when it executes a java script to do an http redirect, that is where I am running into problems.

---

### Post by DugieHowsa on 2007-12-15
Finally... it looks like everything is now working.

First, I went to the about:config page in firefox and set the following value to true:

plugin.expose_full_path

Next, I went back to the about:plugins page in firefox.

Upon further review, I found that I had 2 instances of java plugins, both trying to execute from different directories.

The official Ubuntu sun-java6 binaries are installed in /usr/lib/jvm . I deleted the other java directory from my machine.

I then confirmed that all the java plugin links were pointing to the remaining java plugin binary.  This included the following:

```

/usr/lib/mozilla/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/mozilla/plugins/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/usr/lib/firefox/plugins/libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/firefox/libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

/etc/alternatives/firefox-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/etc/alternatives/mozilla-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Finally, I restarted firefox, and went back to the about:plugins page to confirm there was only one instance of the java plugin installed.  Upon revisting the Java test pages, the java plugin was recognized successfully.

---

