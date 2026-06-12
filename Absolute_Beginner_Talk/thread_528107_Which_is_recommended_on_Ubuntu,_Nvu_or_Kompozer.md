---
title: "Which is recommended on Ubuntu, Nvu or Kompozer?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-08-17
i've looked at the previous posts on this question but there was no satisfactory answer.

I'm not looking for opinions about features or intuitiveness, etc. I would like to know
1. Do the references to the "next version of Nvu" mean that a newer version is in the works?
2. Does Ubuntu recommend or endorse one over the other as most compatible with 7.04?
3. If the above cannot be answered, is there a recommended web site builder program that will run on Ubuntu (proprietary, costs $)?

---

### Post by stchman on 2007-08-17
> **rsnow said:**
> i've looked at the previous posts on this question but there was no satisfactory answer.

I'm not looking for opinions about features or intuitiveness, etc. I would like to know
1. Do the references to the "next version of Nvu" mean that a newer version is in the works?
2. Does Ubuntu recommend or endorse one over the other as most compatible with 7.04?
3. If the above cannot be answered, is there a recommended web site builder program that will run on Ubuntu (proprietary, costs $)?

As far as I know Nvu is no longer being updated.  Kompozer is an unofficial bug fix for Nvu.  They look nearly identical.

---

### Post by southernman on 2007-08-17
First off, fergetabout Nvu! It hasn't been dev'd since a short time after it's initial release.

If I remember correctly, Kompozer is built from Nvu with some fixes and tweaks... that's the gest of what I got at least.

Some people recommend Kompozer, others suggest Bluefish. Although Bluefish isn't a WYSIWYG editor, it seems to have a lot of potential... I've tinkered with it myself, but I've been leaning toward hand coding with gedit or nano.

Bluefish > Gnome
Kompozer > KDE
Although you could install either one, on either system... just have to have libs so they'll work cross platform. Synaptic will sort all that out for you.

If none of the above is what you wanted to know... disregard my post! :p

---

### Post by ddrichardson on 2007-08-17
nVu is no longer in development, hence kompozer but there is a deb file on their site. Personally I prefer Amaya which is in the repositories - it has much better support for standards and is WYSIWYG. It also doesn't stick CSS tags all over the place and bizarre formatting characters. It lets you have a dual pane view with WYSIWIG and source editing.

---

### Post by Pragmatist on 2007-08-17
> **rsnow said:**
> i've looked at the previous posts on this question but there was no satisfactory answer.

I'm not looking for opinions about features or intuitiveness, etc. I would like to know
1. Do the references to the "next version of Nvu" mean that a newer version is in the works?
2. Does Ubuntu recommend or endorse one over the other as most compatible with 7.04?
3. If the above cannot be answered, is there a recommended web site builder program that will run on Ubuntu (proprietary, costs $)?

1. From this I gather that neither is available for Feisty right now:
[https://wiki.ubuntu.com/WaitingForNvuFeisty?highlight=%28nvu%29](https://wiki.ubuntu.com/WaitingForNvuFeisty?highlight=%28nvu%29)

2. Ubuntu has official packages, if you use synaptic you will see the ubuntu icon next to those packages, and this is the extent of Ubuntu's "recommendations".

3.  There are many web site builder programs, both in the repositories and elsewhere.  You can find them using google. Many depend on your personal preferences or features needed.  If you just want to know what other people prefer, better questions would be "which web site builders do you use?" or "which web site builders do you prefer?".

---

### Post by Pragmatist on 2007-08-17
I use bluefish, and I use amaya for some testing.  Screem is available (too heavyweight for me).  Then there is eclipse which is an IDE.  As someone mentioned there are just regular editors with HTML support.  It just depends on what your looking for.  An IDE?  an HTML editor?

---

### Post by lgambett on 2007-08-17
Just adding my two cents here.... NVU is no longer included in Ubuntu because it is no longer included in Debian, and this is due to the fact the project is inactive. Kompozer is born from the ashes of NVU; it seems to me a little buggy (more than NVU), so for now I am sticking with NVU.
Sadly we have no Dreamweaver here....

---

### Post by Kilz on 2007-08-17
[The Nvu package for Edgy]("http://packages.ubuntu.com/edgy/web/nvu") installs nicely in Feisty and works just fine for the few simple pages I create.

---

### Post by silent1643 on 2007-08-17
screw either one of them and use wine to run dreamweaver.. its the only way i was happy :)

---

### Post by rsnow on 2007-08-17
One thing I really like about the Ubuntu forum is that there is no shortage of help or lack of enthusiasm. So, thanks to stchman, southernman, ddrichardson, Pragmatist, lgambett, Kilz and silent1643.

I already have Nvu installed because somewhere, somehow I came across it and figured it would do OK. Then while messing around on the web I came across info that led me to believe that Kompozer might be better.  I got confused because Nvu's website made it appear to be approved by Canonical and Kompozer could not be found by a search in synaptic package manager. Thus both appeared to be recommended but neither could be found with spm.

Now that ya'll have straightened that out for me, all I have left to do is check out Amaya and bluefish to see which looks best for my puposes. I won't bother with eclipse right now as it looks like it is intended for much more than just web pages.

Well, if I ever get through the checking and testing stage, I might even get my domain name and a host and a web site. 

Thanks, again.

---

### Post by TeaSwigger on 2007-08-17
Coming in a bit late but...

Besides the others mentioned above, there's also Quanta Plus.

I'm successfully running Macromedia Suite 8 via wine, thank goodness; needed for a collab. But it's huge, bloated IMH and quite slow, besides costing a small fortune.

When I want a quick and easy WYSIWYG instead of fussing about with code or the bigger stuff, for example a visually oriented hobby page, I like Composer / KompoZer / NVU. NVU still works in Fiesty (no reason it wouldn't) but I'd lean toward using the newest build of KompoZer or SeaMonkey's Composer. My impression was that NVU was forked from Mozilla Suite's Composer, and that its new versions are again integrated in the new Mozilla Suite, as SeaMonkey's Composer. Seems nobody has bothered telling everyone though. KompoZer took over for a bit but seemed to quit when SeaMonkey came along. Perhaps surprisingly, KompoZer project seems to have stirred back to some life; there's a recent version that quietly popped up at SourceForge. I've tried it; it works fine. One of the KompoZer packages is perfect for us on *buntus; just unzip, move to /etc and run it from there. No installation or anything else required. It doesn't get any easier. Nice to have around IMH.

Whatever you choose, there's no reason to shy from diving into web dev on *buntus. :)

---

### Post by Toadmund on 2007-08-17
There is something called 'codetch' [http://www.codetch.com/](http://www.codetch.com/) available in the firefox add-ons, you may want to check that one out, but ultimately I wanted Kompozer back as I was more familiar with it, so I went to the Kompozer website and downloaded it to feisty.

I am in the process of creating a new website using only Kompozer, when I was with M$ I used Coffee Cup html editor **and** Kompozer as I found Kompozer rendered better, yet coffee cup was more user friendly, but Kompozer is getting easier and easier for me.

Here is the website I am working on, a bit bare bones as of now, but I am woiking on it, Nyuk, Nyuk, Nyuk :)

[www.freshdumps.com]("www.freshdumps.com")

PS, Amaya was totally :confused::-k](*,) So I promply gave up on that one.

---

### Post by Pragmatist on 2007-08-17
I had a comp sci professor in grad school who swore by jedit:
[http://www.jedit.org/](http://www.jedit.org/)

---

### Post by stchman on 2007-08-18
> **southernman said:**
> First off, fergetabout Nvu! It hasn't been dev'd since a short time after it's initial release.

If I remember correctly, Kompozer is built from Nvu with some fixes and tweaks... that's the gest of what I got at least.

Some people recommend Kompozer, others suggest Bluefish. Although Bluefish isn't a WYSIWYG editor, it seems to have a lot of potential... I've tinkered with it myself, but I've been leaning toward hand coding with gedit or nano.

Bluefish > Gnome
Kompozer > KDE
Although you could install either one, on either system... just have to have libs so they'll work cross platform. Synaptic will sort all that out for you.

If none of the above is what you wanted to know... disregard my post! :p

Kompozer or Nvu is a not a KDE app.

---

### Post by southernman on 2007-08-18
> **stchman said:**
> Kompozer or Nvu is a not a KDE app.Your right. Thanks for the correction. Thought in my reading of it, allbeit some months ago, it was listed as KDE app. 

Nvu, never said it was.

---

### Post by stchman on 2007-08-19
> **southernman said:**
> Your right. Thanks for the correction. Thought in my reading of it, allbeit some months ago, it was listed as KDE app. 

Nvu, never said it was.

I was too also confused as a lot of KDE apps start with "K" something.

---

### Post by mitchlinux on 2007-08-31
I just downloaded the Amaya and Kompozer, at first sight Kompozer looks more user friendly.

BTW I'm loving this Synaptics download thing. Just search, click, apply, and that's it, everything is done for you.

Toadmund: GO RON PAUL!!! whoo hooo!!!

---

### Post by Toadmund on 2007-09-15
Ya, Ron Paul seems to have went alright, right off national exposure and hidden in a dark corner somewhere, his ideas are too radical for the powers that be, too,... shall I say, American citizen oriented, when those in the US gubberment look out for themselves, ideas like his are best kept out of site, and out of mind of the average American citizen.
So, for repulseicans,  er, ahem, repuls, I'm sorry, republicans, all that's left is Rudy Gluebagandi, er sorry Giuliani, and Fraud, er sorry Fred Thompsonofabi..., er Thompson.

What is wrong here :confused: !!!

Anyway, my website's are somewhat amateurish, but sincere, and done all by Kompozer!
Take a look at Kittens being born, be virtually there!
[SEE...The KITTENS!!!]("http://www.freshdumps.com/thenewkittens.html")

---

### Post by rsnow on 2007-10-14
Since I started this thread it seemed only right to update it and share my experience.

I took a look at Nvu, Bluefish and Amaya. I finally uninstalled Nvu and am mainly using Bluefish. I kept Amaya for possible future use but it seems to have a steeper learning curve than Bluefish.

I have a web site but used a template supplied by the host to start with. I have going through the tutorials at 3w.schools web site to gain some knowledge about html,  xml, css and javascript. It will be a while before I master all of this but it is fun learning and playing with it.

Don't expect to see much change any time soon but hopefully someday I'll start making my web site like I want it.
[www.jisc2day.org](www.jisc2day.org)

---

