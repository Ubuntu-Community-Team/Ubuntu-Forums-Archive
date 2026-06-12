---
title: "Firefox freezes"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-12-08
I'm using Firefox 2 beta2, and it has worked amazing for the past month that I've had it. But yesterday, it froze for the first time. I didn't think much of it, but then today it froze again...and again...and again. It's frozen probably 4 maybe 5 times already today. I haven't downloaded or installed a single thing in over a week. 

I'm using dapper on a gateway SOLO 5350 Laptop, 256 MB RAM, 20 GB HD. I know that doesn't mean much in this situation, but can't hurt.

---

### Post by taurus on 2006-12-08
I assume you installed firefox v2 by hand, right!!!  How did you install it?

---

### Post by voodoonirvana on 2006-12-08
> **taurus said:**
> I assume you installed firefox v2 by hand, right!!!  How did you install it?

Yeah I'm pretty sure I did. Can't remember for sure though. Should I switch to just plain old Firefox 2, from beta2?

---

### Post by taurus on 2006-12-08
They call it beta for a reason.  If you don't want to fill out bug reports, should stick with the stable version.  ;)

---

### Post by voodoonirvana on 2006-12-08
> **taurus said:**
> They call it beta for a reason.  If you don't want to fill out bug reports, should stick with the stable version.  ;)

Gotcha.

Could you guide me to how I would go about switching from this beta2 to 2? Along with all my bookmarks and addons.

---

### Post by taurus on 2006-12-08
All your bookmarks should be in ~/.mozilla/firefox/**random numbers & letters**/bookmarks.html.  So, may want to make a backup copy of that directory, ~/.mozilla/firefox...  Then, remove the beta version and install the stable version.

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Cardmaster91 on 2006-12-08
you may also want to look into swiftfox, its like 3 times as fast for me than firefox

---

### Post by voodoonirvana on 2006-12-08
> **Cardmaster91 said:**
> you may also want to look into swiftfox, its like 3 times as fast for me than firefox

...but the catch is?


Oh and I'm really confused. I just did a "sudo aptitude remove firefox" and it went through the process. Then I went into aptitude and unchecked the firefox stuff. But how come I can still start Firefox up just fine? It still even says Mozilla Firefox Beta 2 at the top.:confused:

---

### Post by taurus on 2006-12-08
Because you installed it by hand since Dapper comes with version 1.5, not 2, or beta...  Therefore, you need to know where you installed it and remove it by hand first!

```
locate firefox
-or-
sudo find / -name firefox -print
```

---

### Post by voodoonirvana on 2006-12-08
> **taurus said:**
> Because you installed it by hand since Dapper comes with version 1.5, not 2, or beta...  Therefore, you need to know where you installed it and remove it by hand first!

```
locate firefox
-or-
sudo find / -name firefox -print
```

Okay, I'm feeling really retarded right now because I haven't done anything like this in so long. How do I move the Firefox folder to the trash? I don't have permission I guess because "Move to Trash" is not an option when I right click.

---

### Post by Cardmaster91 on 2006-12-08
> **voodoonirvana said:**
> ...but the catch is?



no catch :)
just get [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38"), install swiftfox, and run it. but if ur looking for speed w/o swiftfox, you may also try [this thread]("http://ubuntuforums.org/showthread.php?t=202838"). i recommend you do this after you have firefox working :)

---

### Post by voodoonirvana on 2006-12-08
So can someone help me manually remove this without removing my bookmarks and addons please?

---

### Post by slicker on 2006-12-09
> **voodoonirvana said:**
> ...but the catch is?


Oh and I'm really confused. I just did a "sudo aptitude remove firefox" and it went through the process. Then I went into aptitude and unchecked the firefox stuff. But how come I can still start Firefox up just fine? It still even says Mozilla Firefox Beta 2 at the top.:confused:

The catch is that Swiftfox isnt free as in freedom software. Its been benchmarked and it has a fraction of a second speed improvement. So it may not be worth it.

---

