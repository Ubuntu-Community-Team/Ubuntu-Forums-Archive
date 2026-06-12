---
title: "a few beginners questions"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by vincentvega_1985 on 2008-04-07
hey everyone!

last week i've finally decided to switch to linux! i have tried fedora in the past, but never really got into it. i needed to reinstall windows, because it was completely screwed up. so i figured, what the hell... went online and found out about ubuntu. i was really exited about it, like a small kid in a candy store :)

installed ubuntu 7.10, read a lot about it, and just finished reinstalling it to my needs, i didn't have the partitions the way i wanted, cause i was planning on running XP aside linux, but changed my mind.
i now have a 25gig partition for my / directory, a 1gig for swap and roughly 50 for /home
it's running on a toshiba satellite m100
first impression: i'm loving it!

so anyway, i have a few questions. i didn't really find much to help me on this online, so if anyone could help me, or direct me to a place i could find howtos or whatever on any of these subjects, i would really appreciate it.

1. when i have a few tasks open in firefox, or a few windows, sometimes i get lag. i looked that up on this forum, but all i found was someone with the same problem, who figured out, that that was the case, when there were a lot of flash banners on the pages. which probably is the problem here too. his solution was to remove flash. but i really need flash, so that's out of question. anyone got any ideas what i could do about that?

2. i've always had my startmenu bar up top. so i really want all of that at the top of the screen here too. but when i minimize a window, it minimizes to the bottom, how can i change that? i know it doesn't really matter, but i want everything too look good ;)

3. where can i find good tutorials for making custom themes for everything. i want all of my apps etc. to look good and really want to do it myself, only i havn't found a good tutorial on it. if possible, for beginners, but i'll take what i get!

4. on other peoples desktop screenshots, i've seen a bar where every technial detail on the machine is displayed, cpu usage, hdd usage, temperatures, upload, download, etc.etc.etc. where can i get that? i found a screenlet for screenlets, but that doesn't show temperatures.

5. i've read, that graphics drivers aren't always installed right on ubuntu. how do i know if mine is or isn't. everything seems to be alright, but i've only had it for 2 days. my machine has an ATI Mobility Radeon X1300.

i think that's it for the beginning.

cheers, Vincent

---

### Post by hyper_ch on 2008-04-07
> **vincentvega_1985 said:**
> but i really need flash, so that's out of question. anyone got any ideas what i could do about that?
Don't visit those sites ;) well, you could tell Adobe to create better flash plugin for linux ;)

> **vincentvega_1985 said:**
> but when i minimize a window, it minimizes to the bottom, how can i change that? i know it doesn't really matter, but i want everything too look good ;)
You're using Ubuntu or Kubuntu or Xubuntu? I'm sure it can be made but first we need to know what you use ;)

> **vincentvega_1985 said:**
> 
4. on other peoples desktop screenshots, i've seen a bar where every technial detail on the machine is displayed, cpu usage, hdd usage, temperatures, upload, download, etc.etc.etc. where can i get that? i found a screenlet for screenlets, but that doesn't show temperatures.
Conky does that... there's a huge thread with conky configs somewhere... just search the forums for it and you'll find it ;)

---

### Post by jkeyes0 on 2008-04-07
I agree 110% about adobe needing to create a better flash plugin. That's one of the things I'm most disappointed with about using Linux in general.

As far as the firefox issue, part of that is flash and part of that is firefox 2.0. Firefox 3.0 is coming soon, and it's supposed to be much less bloated and run a bit faster. I managed to get the beta installed on my home Ubuntu machine, but I don't have the tutorial here (it may have been in the repo's...).

If you want your windows to be at the top, you can edit your gnome bars, just right click on a panel and select "Add to panel". I think the one you're looking for is "Window List". After you have it in the appropriate place, you can right click the one in the bottom bar and remove it from the panel.

As far as the graphics drivers, you can check the status by going to System -> Administration -> Restricted Drivers Manager and see if the ATI driver is enabled (if you want to use the proprietary, non-free drivers, that is)

---

### Post by vincentvega_1985 on 2008-04-07
wow, thanks for the quick reply!


> **hyper_ch said:**
> You're using Ubuntu or Kubuntu or Xubuntu? I'm sure it can be made but first we need to know what you use ;)

i think i mentioned it in my first post, but anyway, it's ubuntu 7.10


about the flash thing, thanks anyway, i guess i'll just wait and hope :)

thanks for the tip on conky.... just found that thread you mentioned, looks great!

> **jkeyes0 said:**
> If you want your windows to be at the top, you can edit your gnome bars, just right click on a panel and select "Add to panel". I think the one you're looking for is "Window List". After you have it in the appropriate place, you can right click the one in the bottom bar and remove it from the panel.

i think i didn't explain that properly. i already have the "Window List" at the top, that wasn't the problem. when i click the minimize button, the effect makes it minimize to the bottom, instead of the top, where the list is...do you know what i mean? the actual window kinda shrinks to where it is in the list, only i changed the position of the list, but the effect didn't change.
hope you understand me now!

thanks for the tip with the graphics driver, i guess i'll just stick with the one i have for now, as long as it doesn't give me problems

cheers

---

### Post by The Cog on 2008-04-07
Check out the flashblock extension for firefox. It replaces flash areas with a button that you have to click to start the animation. You can whilelist your favourite sites so they run unimpeded.

---

### Post by billgoldberg on 2008-04-07
> **vincentvega_1985 said:**
> hey everyone!

last week i've finally decided to switch to linux! i have tried fedora in the past, but never really got into it. i needed to reinstall windows, because it was completely screwed up. so i figured, what the hell... went online and found out about ubuntu. i was really exited about it, like a small kid in a candy store :)

installed ubuntu 7.10, read a lot about it, and just finished reinstalling it to my needs, i didn't have the partitions the way i wanted, cause i was planning on running XP aside linux, but changed my mind.
i now have a 25gig partition for my / directory, a 1gig for swap and roughly 50 for /home
it's running on a toshiba satellite m100
first impression: i'm loving it!

so anyway, i have a few questions. i didn't really find much to help me on this online, so if anyone could help me, or direct me to a place i could find howtos or whatever on any of these subjects, i would really appreciate it.

1. when i have a few tasks open in firefox, or a few windows, sometimes i get lag. i looked that up on this forum, but all i found was someone with the same problem, who figured out, that that was the case, when there were a lot of flash banners on the pages. which probably is the problem here too. his solution was to remove flash. but i really need flash, so that's out of question. anyone got any ideas what i could do about that?

2. i've always had my startmenu bar up top. so i really want all of that at the top of the screen here too. but when i minimize a window, it minimizes to the bottom, how can i change that? i know it doesn't really matter, but i want everything too look good ;)

3. where can i find good tutorials for making custom themes for everything. i want all of my apps etc. to look good and really want to do it myself, only i havn't found a good tutorial on it. if possible, for beginners, but i'll take what i get!

4. on other peoples desktop screenshots, i've seen a bar where every technial detail on the machine is displayed, cpu usage, hdd usage, temperatures, upload, download, etc.etc.etc. where can i get that? i found a screenlet for screenlets, but that doesn't show temperatures.

5. i've read, that graphics drivers aren't always installed right on ubuntu. how do i know if mine is or isn't. everything seems to be alright, but i've only had it for 2 days. my machine has an ATI Mobility Radeon X1300.

i think that's it for the beginning.

cheers, Vincent

1. Turn of compiz fusion off or use adblock plus (firefox add on) that will remove most flash banners. Or modify your /etc/hosts file with a list found on the internet.

Or use firefox 3 beta 5. It's already more stable and faster than firefox 2.

Instructions here:
[http://linuxowns.wordpress.com/2008/04/03/firefox-3-beta-5/](http://linuxowns.wordpress.com/2008/04/03/firefox-3-beta-5/)

2. On the top panel, right-click and choose :" add to panel". Pick "window list". It could be another one, but i'm pretty sure that's it. Remove the windows list on the bottom.

3. google? 

4. Could that be conky? 

A easy guide here:
[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/](http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/)

5. If it isn't installed right, you would know straight away.

---

