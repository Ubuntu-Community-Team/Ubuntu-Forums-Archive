---
title: "re: ati X*** video cards"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by pcrussell50 on 2007-09-09
i have one of the aforementioned ati X*** series vidoe cards that is referenced in the sticky.  it is specifically an ati radeon x200 that came onboard my asus AMD mainboard.  others have mentioned problems with it too.  my problems are like everyone else's...my screen will go randomly white while surfing or anything that requires a re-draw of the screen.  and it is a hard lock...nothing will unlock it except a hard reboot.

sooo, i have two questions:

1]will this be fixed in gutsy?  i can wait till mid-oct for it if it will be fixed.

2]i don't mind buying a new card, but every single video card at newegg.com is either an nvidia or a radeon, and every radeon begins with an "X".  does that mean that you can't run a radeon video card with ubuntu?  ok, above the $50 price point there are some radeons that don't begin with "X".  put another way, unless i'm missing something, it looks like i'll have to get a geForce card to run ubuntu problem-free. can this be for real?

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609641&bop=And&Pagesize=50]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609641&bop=And&Pagesize=50")

-peter

---

### Post by overdrank on 2007-09-09
> **pcrussell50 said:**
> i have one of the aforementioned ati X*** series vidoe cards that is referenced in the sticky.  it is specifically an ati radeon x200 that came onboard my asus AMD mainboard.  others have mentioned problems with it too.  my problems are like everyone else's...my screen will go randomly white while surfing or anything that requires a re-draw of the screen.  and it is a hard lock...nothing will unlock it except a hard reboot.

sooo, i have two questions:

1]will this be fixed in gutsy?  i can wait till mid-oct for it if it will be fixed.

2]i don't mind buying a new card, but every single video card at newegg.com is either an nvidia or a radeon, and every radeon begins with an "X".  does that mean that you can't run a radeon video card with ubuntu?  ok, above the $50 price point there are some radeons that don't begin with "X".  put another way, unless i'm missing something, it looks like i'll have to get a geForce card to run ubuntu problem-free. can this be for real?

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609641&bop=And&Pagesize=50]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609641&bop=And&Pagesize=50")

-peter

Hi as you can see in my signature I have a x300 and it runs fine. If you search the forums that the x300 and x600 and x700 run well also. But I have nvidia cards install also with the geforce 4 series and  they run well also.

---

### Post by [Alsharifi] on 2007-09-09
i have a x300 fglrx+xgl+compizfusion+AWN+ect...  and it runs great!

---

### Post by pcrussell50 on 2007-09-09
> **'[Alsharifi] said:**
> i have a x300 fglrx+xgl+compizfusion+AWN+ect...  and it runs great!

i'm sorry, i vaguely know what you're talking about because i followed the directions in the sticky, but  most of what you said is totally confusing to me. can you elaborate?

-peter

---

### Post by Faud on 2007-09-09
Maybe this thread can help ?

[http://ubuntuforums.org/showthread.php?t=190133&highlight=X200](http://ubuntuforums.org/showthread.php?t=190133&highlight=X200)

---

### Post by [Alsharifi] on 2007-09-09
> **pcrussell50 said:**
> i'm sorry, i vaguely know what you're talking about because i followed the directions in the sticky, but  most of what you said is totally confusing to me. can you elaborate?

-peter

i was just stating the fact that,even with various 3d effects and programs,my comp runs great..so the problem is not the card its the configuration..

are you using Xgl or aiglx?....raedon or fglrx drivers?

---

### Post by pcrussell50 on 2007-09-10
> **'[Alsharifi] said:**
> i was just stating the fact that,even with various 3d effects and programs,my comp runs great..so the problem is not the card its the configuration..

are you using Xgl or aiglx?....raedon or fglrx drivers?

ummm...i followed the directions in the sticky about ati x*** series cards.  does that mean i have xgl or aiglx?  or radeon or fglrx drivers?

remember, i'm willing to buy an nvidia card if they don't have the white-screen, hard-lockup problem.

peter

---

### Post by kellemes on 2007-09-10
I have my x1650 (ATI/Radeon that is) working fine on GNU/Linux.
It seems to be hit or miss with videocards.. You better google for experiences with videocards (preferably NVidia) and go from there..

---

### Post by kellemes on 2007-09-10
Couple of links that may be of interest..
[http://ubuntuforums.org/showthread.php?t=528427&highlight=x200]("http://ubuntuforums.org/showthread.php?t=528427&highlight=x200")
[http://ubuntuforums.org/showthread.php?t=341149&highlight=x200]("http://ubuntuforums.org/showthread.php?t=341149&highlight=x200")
[http://ubuntuforums.org/showthread.php?t=190133&highlight=x200]("http://ubuntuforums.org/showthread.php?t=190133&highlight=x200")

If you need support post /etc/X11/xorg.conf and /var/log/Xorg.0.log (using the [CODE]-tags please.)

---

### Post by pcrussell50 on 2007-09-10
> **kellemes said:**
> 

If you need support post /etc/X11/xorg.conf and /var/log/Xorg.0.log (using the [CODE]-tags please.)

this is a good idea.  since i am an "absolute beginner", can you tell me the _exact_ terminal commands to run, and i will post the output for you to look at.

thanks for the links, btw. very informative. 

it's funny, the variety of problems people are having with their graphics cards.  some folks get a white screen with a working mouse as soon as they log in. some can't even install ubuntu.  my problem is slightly different.  i can install ubuntu with no problems.  i can log in with no problems.  it's just that sometimes while surfing or downloading packages, my screen turns white, with NO mouse pointer, and the whole system is locked solid.  no ctrl-alt-* keys will work.  nothing but a hard reboot.  a few other folks have this, but not many.

Oh, and liveCD works just fine, too.  this makes me think that if i do the "vesa" mod, at least my system will be stable.  does this make sense?

---

