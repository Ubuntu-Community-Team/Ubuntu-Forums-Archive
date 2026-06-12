---
title: "Stressed Newbie! Mainly graphics problems"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by jcr1 on 2008-04-11
CANNOT DO ANYTHING!

Getting very stressed now. 

Graphics card : ATI RADION Mobility 9000

Detected as supported by legacy driver or something.

I think/want to upgrade the drivevr as I feel I am not getting the best out of it.

Just tried Envy and that couldn't do anything.

Looked on the ATI website and cannot see my model.

Dont know what to do now. Cannot get compiz-fusion to work, something to do with no xgl?

Really need help to sort this mess out...have installed and uninstalled and installed many things to do with compiz and nothing works. running compiz --replace and nothing happens (screen flickers)

There is a compiz config settings manager in my preferences menu but it does nothing

There is a compix settings manager and it opens but complains about no dbus??

Can anyone help please??

Many thanks.

Jon

---

### Post by Gulyan on 2008-04-11
I have an Ati 9000 card and after i got compiz runing my computer got problems with the display so bad that i had to reinstall.
My advice: stick with the standard effects :popcorn:

---

### Post by jcr1 on 2008-04-11
when I go into synaptic manager there are sooo many different things with compiz in the title...how do i know what i want or dont want...or how to return it to what it was..

I just tried installing fglrx or something...not sure what that did, but when i tried compix --replace it seemed to log me out ??

Hate it when I havent a clue what I'm doing and just hitting things randomly.

---

### Post by jcr1 on 2008-04-11
Don't know how to get back to standard settings now...

In preferences menu there's two compiz settings things..both dont work.

If I right click on desktop, go to Visual Effects, I cant click on any options other than OFF otherwise I get "Desktop Effects could not be enabled"

---

### Post by qamelian on 2008-04-11
You don't need XGL to run compiz on a Mobility Radeon 9000. It works on my laptop with this card out of the box except in Hardy. If you are running t he beta of Ubuntu Hardy Heron you need to do one quick tweak to get it to work as this is one of the blacklisted cards due to known issues with the current version(s) of compiz and many ATI cards. 

If you want the binary ATI drivers, you need to download and older version (8,28.someting) as ATI no longer offers driver support for this card. No big loss in my opinion as the open-source drivers have almost always out-performed the "official" ATI drivers on the Mobility 9000.

Which version of Ubuntu are you using?

---

### Post by jcr1 on 2008-04-11
ok in SPM I just uninstalled everything to do with compiz...which is ok.

So if I want to apply some simple effects (i.e. in visual effects anything other than "none") it says cant execute compix xhildren or something...so I need some part of compix installed.

Whats the minimum I should install?

---

### Post by jcr1 on 2008-04-11
Ubuntu 7.10 Gutsy Gibbon October 2007.

Still unsure what the differences betwen gutsy, hardy etc mean...Gusty just came when I went to the Ubuntu website and downloaded a CD.

Cheers for quick answers. Apoligies for my fast, barely legible previous posts

---

### Post by qamelian on 2008-04-11
> **jcr1 said:**
> Ubuntu 7.10 Gutsy Gibbon October 2007.

Still unsure what the differences betwen gutsy, hardy etc mean...Gusty just came when I went to the Ubuntu website and downloaded a CD.

Cheers for quick answers. Apoligies for my fast, barely legible previous posts
Very odd. I have the same video card in my Compaq Presario R3000 laptop and compiz worked immediately. The only thing I installed was the compizconfig-settings-manager and that was only so I could tweak settings without fiddling about with gconf-editor!

---

### Post by jcr1 on 2008-04-11
Do you know what the minimum compiz modules I should reinstall to get the basics back?  Compiz-core perhaps...that seems to drag a load of stuff with it.

Cheers

Jon

---

### Post by qamelian on 2008-04-11
> **jcr1 said:**
> Do you know what the minimum compiz modules I should reinstall to get the basics back?  Compiz-core perhaps...that seems to drag a load of stuff with it.

Cheers

Jon
Not sure what was installed by default. I just remember that I didn't need to install anything to make them work in Gutsy. In Hardy beta, I did need to edit the /usr/bin/compiz script to add one line near the beginning.

I think the package you need to install after removing compiz is compiz-gnome, which should install all the packages needed to integrate compiz with the Gnome desktop. Similarly, in Kubuntu, I believe it would be compiz-kde.

---

