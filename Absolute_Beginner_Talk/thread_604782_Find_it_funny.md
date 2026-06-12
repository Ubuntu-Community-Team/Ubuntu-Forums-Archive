---
title: "Find it funny"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-11-06
While I already posted about 2 issues in another thread, 

1. can't upgrade to 7.10, after 2 weeks, I give up... believe me, I tried, and I think, tried everything.

2. Can't install Gimp2.4 in Fiesty

Now, i find it very ironic that Gimp is open source, yet can't install it in Ubuntu BUT I installed in Windows without needing another update or anything. 

I think Ubuntu really needs to get some things together. While I have been with it for 7 going on 8 months, I doubt I'll be making the year mark. Don't get me wrong, I think the world of Ubuntu "well up to Feisty" anyway, but it's getting to be quite the headache doing anything and have far less trouble in Windows or Fedora. Based on user friendly linux? Supposed to be right? Lately, I think it took a step down, and fell a few more stairs. 

 So really, there is no need as I use Gimp mainly for everything and feel I have a right to use the new version and in all my years, never had this issue, so it's to the point of , hey, I can't upgrade Ubuntu, can't upgrade Gimp in ubuntu, why use ubuntu?  So hopefully things will change so I can be happy with my Ubuntu one day again.

---

### Post by twiceasworn on 2007-11-06
Are you even looking for help?  Or are you just venting?  Trust me, I understand, I ended up going back to feisty too.  What is happening when you try to upgrade gimp?

---

### Post by gimpguy2000 on 2007-11-06
> **twiceasworn said:**
> Are you even looking for help?  Or are you just venting?  Trust me, I understand, I ended up going back to feisty too.  What is happening when you try to upgrade gimp?

No, I'm completely venting but at the same time, trying to give feedback... I have looked for help many times but I feel Ubuntu should also be aware of user frustration and what may cause one to possibly never use it.  "especially with someone like me who wants to use it"

Just to explain, I have tried numerous times to upgrade 7.10 both over internet and disc, neither will work. Two weeks of reading fixes, hopes, dreams, finally, nothing. It won't upgrade from disc do to not recognizing and after 3 discs with 3 different iso's I give up. Internet, well, it gets so far and says there was some problem and quits. It's not my downloading because I can download the iso fine. 

Gimp won't install at all and some have posted some fixes for 2.4 but it won't work or the instructions are hairier than big foot. 

Of course it's not so black and white as posted, but crammed two weeks of 7.10 into a sentence. So while eventually i'm sure there will be methods, I am surprised at the lack of structure and it has since really turned me off to Ubuntu in general. 

Thanks for the help though... and I cringe as I sit here in Windows just to use the new Gimp....:(:(

---

### Post by sailor2001 on 2007-11-06
did you sudo apt-get update && sudo apt-get upgrade?

---

### Post by gimpguy2000 on 2007-11-06
> **sailor2001 said:**
> did you sudo apt-get update && sudo apt-get upgrade?

Yep did that, didn't matter. It says I have the current version which of course is 2.3 :confused: I also tried other aptitude commands that were suggested and it still only gives me 2.3 .  So now I am using it in Windows and back to crashing every stinking 5 min, lol.

---

### Post by rudeboyskunk on 2007-11-06
You could always try uninstalling Gimp from Synaptic then installing Gimp from source from the website.

---

### Post by Taters on 2007-11-06
I am equally annoyed. 

7.10 refuses to install for me even when I do what it tells me to. And I had 2.4 through a special version, but I lost that on one of my many failed attempts to upgrade to 7.10. Now whenever I try to install the 2.4 upgrade it says it conflicts with gimp, I delete gimp, its says it can't find gimp. See my point? Ubuntu is a fun, fast OS, but really unfriendly sometimes despite being "for humans."


Also, why can't I upgrade? Its available for the 7.10 users, why not us? I shudder to think what the 6.06 users have to deal with.

---

### Post by crjackson on 2007-11-06
Has anybody tried to install Gimp from here?

[http://www.getdeb.net/app.php?name=Gimp]("http://www.getdeb.net/app.php?name=Gimp")

---

### Post by tlages on 2007-11-06
It will be easier to help you if you give us more details.

---

### Post by Maestro23 on 2007-11-06
> **crjackson said:**
> Has anybody tried to install Gimp from here?

[http://www.getdeb.net/app.php?name=Gimp]("http://www.getdeb.net/app.php?name=Gimp")

Yes. Installed all 4 packages this morning(64-bit Gutsy version).  Install went without a hitch and Gimp 2.4.1 is running just fine.

---

### Post by jordanmthomas on 2007-11-06
gimpguy2000, it sounds like you'd be happier with a rolling-release distro.
No need to wait for "the next version" to come out.  Just keep yourself updated and you're always running the latest (as in bleeding edge OR latest stable, your choice)

Try looking into something like Arch or Gentoo (although I hate Gentoo with a passion) because they may be more what you're looking for.

---

### Post by crjackson on 2007-11-06
> **Maestro23 said:**
> Yes. Installed all 4 packages this morning(64-bit Gutsy version).  Install went without a hitch and Gimp 2.4.1 is running just fine.

Cool.  Will it upgrade the currently installed version (on Gusty 64)  or do you have to remove the old version 1st?

Also does the order of which packages you install 1st matter?

---

### Post by Maestro23 on 2007-11-06
> **jordanmthomas said:**
> gimpguy2000, it sounds like you'd be happier with a rolling-release distro.
No need to wait for "the next version" to come out.  Just keep yourself updated and you're always running the latest (as in bleeding edge OR latest stable, your choice)

Try looking into something like Arch or Gentoo (although I hate Gentoo with a passion) because they may be more what you're looking for.

Arch would probably be good for the OP.  I agree with you on Gentoo.  I run it on my laptop.

---

### Post by Maestro23 on 2007-11-06
> **crjackson said:**
> Cool.  Will it upgrade the currently installed version (on Gusty 64)  or do you have to remove the old version 1st?

Also does the order of which packages you install 1st matter?

I uninstalled the Synaptic version of GIMP first.  Then you install (in order, if I remember correctly)

1. Gimp-data
2. libgimp-2.0
3. Gimp
4. gimp-python

*You can isntall the .deb's with the Gdebi package installer (right-click on the package).  It will tell you the order they need to be installed.

---

### Post by Taters on 2007-11-06
Tried it, didn't work. 

Keep in mind that myself and gimpguy2000 are using 7.04

Also, if anyone has the modified version of gimp from [gimpusers.com]("www.gimpusers.com") please post it (the older, no longer available 7.04 version). It works fine on 7.04 without any errors.

---

### Post by gimpguy2000 on 2007-11-07
It's only Gutsy release which as stated....I , can't, install the updated version of Gutsy and have tried every method under the sun. 

Sure..I can do a fresh install I suppose but with how quirky it's been already, do I want to chance losing everything I have working? Nah.  

So I not only can I not install Gutsy, I can't install Gimp because there is no 2.4  install for Feisty  

Good point Taters and Gimp 2.4 didn't work for me either which as you stated, we are in 7.04.

---

