---
title: "Why is the main distro Gnome? Is there something wrong with KDE?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-04
I'm been using Ubuntu for a while now, and often use KDE apps, and I like the way they look and was thinking of just switching to KDE. 

IS there any problem with KDE? 

Is there any problem with installing KDE w/ gnome? How much extra files does it actually add.
Ithink I tried downloading once before and it looks liked it was installing apps I already had like OpenOffice. Can it not use the apps I've already downloaded?

Is using a dual boot with Kubuntu and Ubuntu better than having both Gnome and KDE together?

Thanks!

---

### Post by Bachstelze on 2007-05-04
Because it is the choice of the developpers. No, there is nothing wrong with KDE, if you want to install it :

```
sudo apt-get install kde
```

(replace kde with kde-core for a minimal but faster KDE)

---

### Post by dpzektor on 2007-05-04
There is a Kubuntu distro as well, that is basically Ubuntu with the KDE interface. I am personally happy that Gnome is the default interface that comes with Ubuntu. I am learning Linux with this interface with no problems at all (another newbie here). I have had experience with KDE (ran SUSE with it for a little while before Ubuntu) and while the interface is nice, there just seems to be "too much going on" for me...if that makes any sense. Gnome just feels more responsive, and I can get around and get my work done with little to no questions asked.

---

### Post by Xarok on 2007-05-04
> **HymnToLife said:**
> Because it is the choice of the developpers. No, there is nothing wrong with KDE, if you want to install it :

```
sudo apt-get install kde
```

(replace kde with kde-core for a minimal but faster KDE)

OK, here it goes!

ooo 69th post

---

### Post by teddybairs1 on 2007-05-04
Don't bother with dual booting. You don't need to. Just go to Synaptic and search for "kubuntu-desktop" find it and mark it for install. It'll pull down the entire Kubuntu kde desktop. It pulls down about 3-400MB and installs about twice as much or so. Then you can switch sessions at the login screen between gnome and kde. I do it all the time. It'll only pull down the files you don't already have installed. the reason is that the kubuntu-desktop package has all of the packages normally found in the kubuntu install disk as it's dependencies. Synaptic just checks to see what dependencies you have and don't have. If you already have openoffice, it won't bother with it.

Another guy tried dual booting with Kubuntu and Ubuntu because he didn't understand how they worked. As a result, his GRUB screen only recognizes the fresh install and not his original install. so he's got a partition he can see but not boot into.

As to why Gnome is chosen as default, I guess Shuttleworth just liked it better. I tend to prefer some KDE apps over Gnome ones, but I have to admit, Gnome 2.18 does seem more stable at times than KDE. I have fewer problems with programs crashing on me, and it seems to work better with beryl than KDE does. KDE is nicer to look at, and is more customizable, but I'm getting to appreciate Gnome as well.

---

### Post by Xarok on 2007-05-04
Thanks guys!

> **HymnToLife said:**
> Because it is the choice of the developpers. No, there is nothing wrong with KDE, if you want to install it :

```
sudo apt-get install kde
```

(replace kde with kde-core for a minimal but faster KDE)

I did as you said... 
it downloaded things
I rebooted
nothing changed
:confused: 

I will try GUI install way now....

---

### Post by Bachstelze on 2007-05-04
> **teddybairs1 said:**
> As to why Gnome is chosen as default, I guess Shuttleworth just liked it better.

Actually, Mark is said to personnally prefer KDE, I guess he just thought Gnome would suit the needs of Ubuntu better...


Xarok > you should have a "KDE" option in the "Sessions" menu of your login screen.

---

### Post by Xarok on 2007-05-04
> **teddybairs1 said:**
> Don't bother with dual booting. You don't need to. Just go to Synaptic and search for "kubuntu-desktop" find it and mark it for install. It'll pull down the entire Kubuntu kde desktop. It pulls down about 3-400MB and installs about twice as much or so. Then you can switch sessions at the login screen between gnome and kde. I do it all the time. It'll only pull down the files you don't already have installed. the reason is that the kubuntu-desktop package has all of the packages normally found in the kubuntu install disk as it's dependencies. Synaptic just checks to see what dependencies you have and don't have. If you already have openoffice, it won't bother with it.

Another guy tried dual booting with Kubuntu and Ubuntu because he didn't understand how they worked. As a result, his GRUB screen only recognizes the fresh install and not his original install. so he's got a partition he can see but not boot into.

As to why Gnome is chosen as default, I guess Shuttleworth just liked it better. I tend to prefer some KDE apps over Gnome ones, but I have to admit, Gnome 2.18 does seem more stable at times than KDE. I have fewer problems with programs crashing on me, and it seems to work better with beryl than KDE does. KDE is nicer to look at, and is more customizable, but I'm getting to appreciate Gnome as well.

Ok after trying the terminal way, nothing happened, now i'm trying to install kubuntu desktop and it's dling a lot of things again.

Did I just f*%*&g instal KDE twice!? oh shi...

They look like the same damn things that installed in the terminal

I hope I'm mistaken

---

### Post by Xarok on 2007-05-04
> **HymnToLife said:**
> Actually, Mark is said to personnally prefer KDE, I guess he just thought Gnome would suit the needs of Ubuntu better...


Xarok > you should have a "KDE" option in the "Sessions" menu of your login screen.

Nope I don't think it was there. 

My power button from the logout menu disappeared a while ago (i've been having to shutdown through the terminal), so maybe this is something buggy too.


Mmmmm, this steak burrito tastes good.

---

### Post by teddybairs1 on 2007-05-04
kubuntu-desktop, oddly enough doesn't have "kde" as one of it's dependencies if I remember right. Let it finish it's downloading. Like I said, if it's already on your system, it won't install it twice.

As to how to switch, go back to your login screen by logging out of Gnome. Don't select restart or shutdown, select logout. "Sessions" should be somewhere on your screen. click it. It should say something like "change session" or something to that effect and should give you a list of either KDE, Gnome, Default, etc. It will boot to whichever desktop you select.

---

### Post by Billy McCann on 2007-05-04
Just relax.  You haven't broken anything.  :)

When you login, just choose KDE as your Session.  Remember, it's an option that you choose at the login screen.  If you auto-login, just ctrl-alt-bckspace to get back to the login screen.

---

### Post by Bachstelze on 2007-05-04
> **teddybairs1 said:**
> kubuntu-desktop, oddly enough doesn't have "kde" as one of it's dependencies if I remember right.

Yep, that's because they're both metapackage which install a different set of packages.

---

### Post by Xarok on 2007-05-04
OK, now it work! Thanks guys!

I see what you mean about clutter.

And that bounce icon is...How can I put it with out saying the word... gay?

I think one of the greatest things about Ubuntu and Mac OSX is that they hide most of the funtions that people don't use often so that your eyes spend less time looking for what you need.

Some people like the "My system looks like it does a lot of **** 'cause it has a lot of buttons" look though.

I personally like systems that look minimalistic but actually do more. 

Just like the apple mighty mouse. A normal fool would look at it and think it only has one button when it actually has 5. It's a ninja tell you. That's why you can't judge a system by just using ti for a few days...

I think a cross between gnome and KDE would be best for me.

Beryl is hot, but still I find the standard look and feel of gnome and KDE is not so hot in comparison to OSX or Windows VIsta.  I know you can change the themes, but every time I've done so it hasn't work out so well.

---

### Post by teddybairs1 on 2007-05-04
Agreed. Like I said, I use a mixture of both Gnome apps and kde apps. I experiment with all the different choices I have with Ubuntu and find what I like and don't like. Since I can launch either Gnome or Kde apps in either desktop, I can have my cake and eat it too.

I've found the theme editor in Gnome 2.18 in feisty is a lot more stable than it was under edgy. Also, you can install new themes and theme components from gnome-look.org.

Take a look at my gnome desktop:

---

### Post by disturbedite on 2007-05-04
> **Xarok said:**
> I think one of the greatest things about Ubuntu and Mac OSX is that they hide most of the funtions that people don't use often so that your eyes spend less time looking for what you need.

some ppl see that as a weakness (linus & myself included).  (some ppl refer to it as "dumbing down" the interface).   i don't have anything against gnome  (i'm on kubuntu) and use some gnome apps.  they live happily together so all is well.

---

### Post by Bachstelze on 2007-05-04
> **Xarok said:**
> 
I think one of the greatest things about Ubuntu and Mac OSX is that they hide most of the funtions that people don't use often

That's exactly what I dislike about them...

---

### Post by Kobalt on 2007-05-04
> Is there something wrong with KDE? 
You could start a war with such post titles my friend :D

---

### Post by disturbedite on 2007-05-04
> **HymnToLife said:**
> That's exactly what I dislike about them...
me too.

> **Kobalt said:**
> You could start a war with such post titles my friend :D

i know that wasn't directed at me, but i was thinking the same thing.  ;)  i was careful to not try to start one myself with my previous post.

---

### Post by haku.spejsr on 2007-05-06
my 2 cents ..

I've been using ubuntu as a primary OS for no longer then 2 months now, and I just switched to kde.

I had some problems with loading gnome (it used to send be back to login screen), amarok was not behaving nicely (which I really like and I do not wan to switch to other ones) and now since I installed kde-dektop, everything runs smoothly, even beryl, so I'm gonna stick with K. apart for being more functional for me, it also seems more fresh and edgy (even though it's on feisty, lol)

kubuntu ftw

---

### Post by neodarksaver on 2007-05-06
getting KDE installed doesnt mean it will boot to it.

---

### Post by bobplano on 2007-05-06
you can change the default session to kde though so then when you login it will default to kde

---

### Post by ubnewbie2 on 2007-05-06
> **HymnToLife said:**
> That's exactly what I dislike about them...

I used to be like that, always used KDE, but I have changed my opinion.  I have come to appreciate a clean uncluttered interface that lets me do my daily things easily.

If I want to dive under the hood, I certainly can, but I don't need KDE, necessarily, to do that.

---

