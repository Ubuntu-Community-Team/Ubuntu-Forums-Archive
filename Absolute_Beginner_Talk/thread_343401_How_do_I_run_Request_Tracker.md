---
title: "How do I run Request Tracker"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by gyalakias on 2007-01-21
I just installed Request Tracker through the Synaptic Package manager.

It installed OK, but I can't seem to find it on the menu.

So I went to the Package Manager again and saw where it was installed. I typed
```

rt-crontool

```
and I got this:
```

Can't locate /etc/request-tracker3.4/RT_SiteConfig.pm in @INC (@INC contains: /usr/local/share/request-tracker3.4/lib /usr/share/request-tracker3.4/lib /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/request-tracker3.4/lib/RT.pm line 131.

```

I also tried to type:
```

rt-setup-database

```
and I got this:
```

Can't locate /etc/request-tracker3.4/RT_SiteConfig.pm in @INC (@INC contains: /usr/share/request-tracker3.4/lib /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/request-tracker3.4/lib/RT.pm line 131.

```

What am I doing wrong? ](*,)

---

### Post by silurius on 2007-04-02
Did this get resolved?  I'm about to explore RT and am curious to know if there's anything I should be aware of going in.

---

### Post by Divan Santana on 2007-06-12
[http://ubuntuforums.org/showthread.php?t=202397&highlight=request+tracker](http://ubuntuforums.org/showthread.php?t=202397&highlight=request+tracker)

I install rt3.6 and am going to try the above link. Think you need to do all that first.

Will give it a try... :)

Wonder if I should go for this or otrs2...?

---

### Post by Divan Santana on 2007-08-22
Am happy with rt3.6 got it working nicely on feisty with apache2 but still struggling to get email interface mail gateway working...

---

