---
title: "Howto Install Java and Flash"
date: 2006-10-13
forum: Apple PPC Users
---

### Post by ricanelite on 2006-10-13
Okay guys, I decided to make Ubuntu Linux my main OS on my Mac Mini. 

Now Ubuntu is running perfect on my mac, but I'm having a really and I mean a really hard time installing Java and Flash. Now I have followed so many sites. So please if anyone could help me out and bascially hold my hand that will  be great.

I'm a Linux Newbie and willing to learn as much as I can. I feel I have found a new home with this OS and I hope I could enjoy it some more. So if anyone could help me out please. Let me know, You could email me at **evazquez757@cox.net** or if you have AOL/AIM my screen name is **ricanelite757** thank you so much!!! I hope you all could guide me through this.

Thank you again!

---

### Post by ricanelite on 2006-10-13
Now, i follow some directions on how to get Java going on my machine now. When I head over to the test site which is

[http://serios.net/content/applets/viewinfoawt.php](http://serios.net/content/applets/viewinfoawt.php)

I get this message:

Loading of Applet Failed
Your browser failed to load the Java applet specified in this page. The most common causes are that you don't have a Java Runtime Environment installed, or that it is too old, or that it is not correctly configured. 

Now can someone please help me out! I'm getting so annoyed!!! LOL

Can someone guide me please!

Thank you!

---

### Post by miggi on 2006-10-13
You have to install the IBM Java developer kit, since Sun doesn't offer a JVM for PPC. Go to [http://www-128.ibm.com/developerworks/java/jdk/linux/download.html](http://www-128.ibm.com/developerworks/java/jdk/linux/download.html) 

What you're looking for is the 32 Bit iSeries/pSeries JVM. You'll first have to register at IBM to download the JDK.

---

### Post by ricanelite on 2006-10-13
Okay, well i did that now Firefox and Opera is not picking up when I do a Java Test.

What problems can it be? A nice and kind person helped my in IRC chat. 

But when I enter the path it says it is correct but still nothing happens when I do a Java Test at the website. But the KDE Browser works with no problem.

What can it be?

Also do you have AIM??? So you could help me out please.

Cause this all new to me!

My screen name is ricanelite755

hope you could help me out thanks alot for replying.

---

### Post by avtolle on 2006-10-13
I presume you installed the 1.5.0 version of Java from the IBM site. If so, you can get it to go in Firefox (don't know about Opera) by configuring it as follows:

```

mkdir -p~/.mozilla/plugins
cd ~/.mozilla/plugins
ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavapluging_oji.xo /usr/lib/mozilla-frefox/plugins

```

Obviously, you need to do the above at the command line, but if you downloaded and installed Java, you already know that. HTH.

---

