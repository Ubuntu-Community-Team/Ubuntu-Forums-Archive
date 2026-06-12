---
title: "Slow Browser?"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by kenh2os on 2006-01-01
Hi All,

   I have just loaded Ubuntu, am I am really pleased.. It works well. I am trying to learn linux, I like this distro the best.

But, to the point.... The Firefox is sluggish. I was wondering if there is a network card settings, to look at for Half, or full deplex type settings? Or is there something else I should look at.

  Please remeber I am learning this. So step by step would be nice.  Or a link, either way.

Thanks so much.... Thanks to all the programers too. This is  a very good distro.

Ken W.

---

### Post by Perfect Storm on 2006-01-01
FF is  sluggish on Ubuntu, but you should take a look here: [http://ubuntuforums.org/showthread.php?t=79283](http://ubuntuforums.org/showthread.php?t=79283)


Or if you don't mind not having Extensions but a lightweighted browser you should try Epiphany.


```

sudo apt-get install epiphany epiphany-extensions

```

Also the right kernel and 3D acc. card driver can speed things up.

---

### Post by earobinson on 2006-01-01
I searched for (speed up firefox) on the forums and found this [http://www.ubuntuforums.org/showthread.php?t=107370&highlight=speed+firefox](http://www.ubuntuforums.org/showthread.php?t=107370&highlight=speed+firefox)

---

### Post by mcduck on 2006-01-01
The first thing I'd try is disabling IPv6 DNS:

-type about:config in the address bar.
-type IPv6  into the filter bar and you'll get a line like 'network.dns.disableIPv6'
-right-click that and select 'toggle' to change it's value to 'true'
-restart Firefox and try if it works any faster.

Then I'd suggest installing Fasterfox extension too.

---

### Post by Mustard on 2006-01-01
[QUOTE=mcduck]The first thing I'd try is disabling IPv6 DNS:

-type about:config in the address bar.
-type IPv6  into the filter bar and you'll get a line like 'network.dns.disableIPv6'
-right-click that and select 'toggle' to change it's value to 'true'
-restart Firefox and try if it works any faster.

Then I'd suggest installing Fasterfox extension too.[/QUOTE]

Agreed. I would disable IPv6 first, as that is a common problem that cause slow performance with Firefox.

---

### Post by byen on 2006-01-01
[QUOTE=earobinson]I searched for (speed up firefox) on the forums and found this [http://www.ubuntuforums.org/showthread.php?t=107370&highlight=speed+firefox](http://www.ubuntuforums.org/showthread.php?t=107370&highlight=speed+firefox)[/QUOTE]

I second that link. With the changes mentioned there... you would see a decent change in speed. But again You also might wanna try epiphany, galeon ( used it for the first time yesterday .wow - talk about fast) and also opera.

Now epiphany and galeon do not have all the themes and plugins like firefox ..but they are good browsers and can be further tweaked by using the methods mentioned in the thread for firefox on these browsers as well.

Hope it helps.goodluck.

---

### Post by kingsidy on 2006-01-01
there is a firefox extension called fasterfox. it basically does all the settings for you, instead of doing them one by one. You then disable ipv6 in the about:config menu.
the other option is to install opera. it is much faster than FF. Epyphany is all really fast, but lack all the extension we have gotten used to in firefox.

---

