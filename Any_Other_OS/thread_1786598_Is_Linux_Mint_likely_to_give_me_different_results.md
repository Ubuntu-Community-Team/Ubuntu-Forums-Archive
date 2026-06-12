---
title: "Is Linux Mint likely to give me different results?"
date: 2011-06-19
forum: Any Other OS
---

### Post by Roasted on 2011-06-19
I'm working with a CR-48 laptop from the Google pilot program. I've installed Ubuntu 11.04 on it and I used the instructions on AskUbuntu to upgrade to Gnome 3 and install Gnome Shell via the official Gnome 3 PPA.

I had ran into some qwirkiness, where the laptop will randomly freeze in the middle of suspending or resuming. There are times I go to suspend, the screen goes blank except for the background, and it just never powers off. It sits there doing nothing, forcing me to shut it off manually, which of course loses anything that's running. Likewise, there are times my menus with text turn to squares, and nothing is selectable. It's like the system goes into some sort of shutdown/lock mode. Icons disappear, text changes to squares, etc.

I installed Linux Mint 11 and installed the Gnome 3 and Gnome Shell PPA using the same instructions. While I only ran Linux Mint for a matter of 4 hours or so, it ran flawless for me, and I used it kind of hard.

This time I want to get a better idea, so I made a Clonezilla backup image of my Ubuntu 11.04 install with Gnome Shell, and I'm on Linux Mint now with the same setup as before. I'm going to use it extensively to see if I run into any issues.

To resolve my issues, I've ran a hard drive test, memtest for 12 hours, redid the partition table when I formatted, and ensured the laptop was cool at all times to make sure it wasn't doing a thermal shutdown.

All this being said, I'm curious. I had no issues in the few hours I ran Linux Mint. Why? I don't know. Ubuntu sometimes surprised me and ran flawless, but then I would run into issue after issue. Part of me wonders if it's a hardware issue, but part of me also wonders if it's because of the fact I'm patching Ubuntu from Gnome 2.X to Gnome 3 and installing the PPA on top of it.

Anyway, this being said, is there anything about Linux Mint that could suggest I may have no issues with it? Or is Mint and Ubuntu so similar that it's not worth the time to compare? I'm just trying to get an idea if there's a high chance for different results.

I'm hoping this goes away with the release of 11.10 where Gnome 3 is installed by default, and I can just install Gnome Shell after installing. Likewise, it still might be a hardware issue, but if it is I'm clueless as to what.

---

### Post by dFlyer on 2011-06-19
If you want to run gnome3 now, why don't you try fedora 15 which has gnome3 as it's default desktop environment.

---

### Post by Roasted on 2011-06-19
> **dFlyer said:**
> If you want to run gnome3 now, why don't you try fedora 15 which has gnome3 as it's default desktop environment.

Well, that's an option, but I really like the .deb thing that Mint/Ubuntu/Debian has going on. I guess I'm trying to jump the gun with using Gnome 3 so soon on these distros since their release cycle in Mint/Ubuntu was April and Gnome 3 came out in May...

Perhaps Fedora 15 would give me a better all-around experience since Gnome 3 is installed by default. 

That said, wouldn't the Debian Mint rolling release give me Gnome 3 or would Debian have to publish Gnome 3 before it comes down to the rolling repos?

Likewise, do you guys have any insight about Mint vs Ubuntu? Is it likely I'll see the same results, or different?

---

### Post by snowpine on 2011-06-19
Ubuntu 11.04 is not designed or tested to work with Gnome 3. If Mint gives you better results, enjoy! :)

---

### Post by dFlyer on 2011-06-19
> **Roasted said:**
> Well, that's an option, but I really like the .deb thing that Mint/Ubuntu/Debian has going on. I guess I'm trying to jump the gun with using Gnome 3 so soon on these distros since their release cycle in Mint/Ubuntu was April and Gnome 3 came out in May...

Perhaps Fedora 15 would give me a better all-around experience since Gnome 3 is installed by default. 

That said, wouldn't the Debian Mint rolling release give me Gnome 3 or would Debian have to publish Gnome 3 before it comes down to the rolling repos?

Likewise, do you guys have any insight about Mint vs Ubuntu? Is it likely I'll see the same results, or different?

I don't blame you. I like the deb file format myself. That's the main reason I've stayed with debian/ubuntu since 2004. In the past I use to use Caldera, RedHat, SuSE, and several other rpm distro but hated dealing the rpm lib hell. The deb file format makes it so easy. If I understand the next version of ubuntu will include a gnome3. Just hang in there a few more months.

---

### Post by wildmanne39 on 2011-06-19
Hi, unity and gnome3 can not be on the same system, if you installed gnome3 you should have had instructions to uninstall unity, a lot of people have trouble using gnome3 it is still a new release like unity both have issues to work out. Also gnoime3 runs on gtk3 and sometimes you end up with gtks still there also and it causes problems.

---

### Post by Roasted on 2011-06-20
> **wildmanne39 said:**
> Hi, unity and gnome3 can not be on the same system, if you installed gnome3 you should have had instructions to uninstall unity, a lot of people have trouble using gnome3 it is still a new release like unity both have issues to work out. Also gnoime3 runs on gtk3 and sometimes you end up with gtks still there also and it causes problems.

Of all of the guides I read about installing Gnome Shell, I've never seen anything about actually uninstalling Unity. All I've seen is notations saying that you'll break Unity. On accident I've tried to log into Unity after doing this and sure enough, it's borked. I can only imagine it's due to Unity being Gnome 2.X based whereas Gnome Shell is Gnome 3.0 based.

I'm going to back up my Linux Mint image and check it out later today, but I'm doubtful I'll stay with it. 

So far in the limited time I used Linux Mint for the 2nd go around, the only positive thing I noticed is how the lock screen appears when you resume. Sometimes, maybe 1/6 times on Ubuntu with Gnome Shell, I'll resume and I'll see my windows active, THEN I'll get the lock screen. Kind of not-secure if you're trying to block out the windows you're working on, but a minor issue at that. Mint hasn't done this so far, and I suspend/resume quite a lot, but it's been a short amount of time.

Today I plan to use it heavier and really try and break it, though I'm somewhat doubtful it'll happen. I heard rumors on some Google sites that Mint 11 comes with Gnome 3, but not Gnome Shell. Can anybody confirm this? When I ran system profiler on this system with Mint 11 it came back as Gnome 2.32 or something. But anyway, like I said, I just wasn't sure if it's normal to see differences in these distros. I know Mint is different, but it's still heavily Ubuntu based... That's what makes me wonder.

---

### Post by mastablasta on 2011-06-20
no something really got messed up in 11.04 on certain hardware (yet another recursive bug?!). to me too Mint works ok while 11.04 (any kind of DE) can't even boot on it.

---

### Post by Roasted on 2011-06-20
> **mastablasta said:**
> no something really got messed up in 11.04 on certain hardware (yet another recursive bug?!). to me too Mint works ok while 11.04 (any kind of DE) can't even boot on it.

I'm not thinking that's the issue here, because other users confirmed 11.04 working flawlessly on the CR-48. And quite honestly, it does. So my question about this is in regard to Gnome Shell specifically, since most people that are running 11.04 on a CR-48 are either running Unity or dropped back to Gnome Classic.

What hardware issues do you speak of? I have yet to hear this.

---

### Post by Roasted on 2011-06-20
Has anybody else out there put the Gnome 3 PPA on their Ubuntu 11.04 systems? If so, what kind of results have you had with it? Has it worked for you without issue or have you ran into some bumps? If so, what kind of bumps have you ran into?

I've ran into random "Oh no! Something happened..." screens at times when logging in to Gnome Shell. This has happened on 3 different systems. A home built desktop, a Latitude E5500 laptop, and a CR-48 Google laptop. All 3 of these were with Ubuntu 11.04.

The other issue I run into is resuming/suspending without issue, however that's only come up on the CR-48. Sometimes if I suspend, it'll just stay there, blank screen, backlight on, literally forever. Other times resuming it locks it up somehow. I have NOT exhibited this on my desktop or my E5500 laptop.

All of this said, I have yet to see it with my CR-48 laptop on Mint 11. I did make an image of Fedora 15 on my laptop along with Mint 11/Gnome Shell + Ubuntu 11.04/Gnome Shell, just so I can bounce around easier if I run into issues.

That said, who's running the Gnome 3 PPA? What are you finding? I'd like to know the good, bad, and ugly.

---

### Post by tgalati4 on 2011-06-20
If you are using Mint 11 based on Debian, then there will be differences over Ubuntu which is Debian with a lot of Ubuntu patches.  Obviously, you should choose a distro which works best with your hardware.  But don't expect stability when using a new framework such as Gnome3.

---

### Post by Bapun007 on 2011-06-20
> **Roasted said:**
> Has anybody else out there put the Gnome 3 PPA on their Ubuntu 11.04 systems? If so, what kind of results have you had with it? Has it worked for you without issue or have you ran into some bumps? If so, what kind of bumps have you ran into?

I've ran into random "Oh no! Something happened..." screens at times when logging in to Gnome Shell. This has happened on 3 different systems. A home built desktop, a Latitude E5500 laptop, and a CR-48 Google laptop. All 3 of these were with Ubuntu 11.04.

The other issue I run into is resuming/suspending without issue, however that's only come up on the CR-48. Sometimes if I suspend, it'll just stay there, blank screen, backlight on, literally forever. Other times resuming it locks it up somehow. I have NOT exhibited this on my desktop or my E5500 laptop.

All of this said, I have yet to see it with my CR-48 laptop on Mint 11. I did make an image of Fedora 15 on my laptop along with Mint 11/Gnome Shell + Ubuntu 11.04/Gnome Shell, just so I can bounce around easier if I run into issues.

That said, who's running the Gnome 3 PPA? What are you finding? I'd like to know the good, bad, and ugly.

i triad to do the same and get the same result as yours .  i am not going to try that with my lucid install .

---

### Post by Roasted on 2011-06-20
> **Bapun007 said:**
> i triad to do the same and get the same result as yours .  i am not going to try that with my lucid install .

What exactly did you try? What results did you get? The "Oh no!" screens or the issues with suspending/resuming?


Ubuntu 11.04 + Gnome 3/Shell PPA?
or
Linux Mint 11 + Gnome 3/Shell PPA?


Anybody have any idea what the difference from Mint to Ubuntu would be? I'm hoping *all* of these issues go away with 11.10 where Gnome 3 is existent and Gnome Shell is easily installable from the repos... Wonder what the chances are of that?

---

### Post by sffvba[e0rt on 2011-06-20
I had no issues running Gnome 3 on Mint... removing it however resulted in a totally borked system for me...


404

---

### Post by Roasted on 2011-06-20
> **not found said:**
> I had no issues running Gnome 3 on Mint... removing it however resulted in a totally borked system for me...


404

Did you do the PPA purge and then remove it? Or did you just apt-get remove gnome-shell?

---

### Post by sffvba[e0rt on 2011-06-20
> **Roasted said:**
> Did you do the PPA purge and then remove it? Or did you just apt-get remove gnome-shell?

I cannot remember... I was using the same advice I had used to install it... I think it was from Ubuntu Answers but I can be mistaken...


404

---

### Post by Yellow Pasque on 2011-06-20
> **Roasted said:**
> That said, wouldn't the Debian Mint rolling release give me Gnome 3 or would Debian have to publish Gnome 3 before it comes down to the rolling repos?

Debian Mint is based on Debian testing, which has some gnome 3 stuff, but not a full DE, so if you want a Debian-based gnome 3 distro, your options are:
[LIST]
[*]Run aptosid xfce and enable experimental repos
[*]Run Ubuntu Oneiric
[*]Run Natty + Gnome 3 PPA
[*]Some other distro I haven't thought of
[/LIST]

---

### Post by Roasted on 2011-06-21
> **Temüjin said:**
> Debian Mint is based on Debian testing, which has some gnome 3 stuff, but not a full DE, so if you want a Debian-based gnome 3 distro, your options are:
[LIST]
[*]Run aptosid xfce and enable experimental repos
[*]Run Ubuntu Oneiric
[*]Run Natty + Gnome 3 PPA
[*]Some other distro I haven't thought of
[/LIST]

I didn't even think about running 11.10... but that may be kind of a stretch for now. However, I should install it just to see what's up.

Fedora 15 is the only "official" distro at the moment with Gnome 3 shipping by default. The only others I know of are Natty + Mint 11 via PPA.

EDIT - Well, just had the issue come up with Mint 11. I resumed and typed in my password. I was looking away as I typed it but I know I saw the login box. When I looked down, the login box was just disappearing and I had a blank screen with the top Gnome 3 panel. Mouse and keyboard gestures at this point did nothing. At one point I had gotten a whole list of terminal looking errors, something about read/write to EXT4 FS. I really wonder if it's something with this laptop though since this CR-48 is a repeat offender for issues. Not only that, but there HAS been maybe 5 times since I had this (early February) that I booted up and it said no hard drive detected... The only way to know for sure is to install Fedora, an officially supported Gnome 3 distro, and run that for a bit and see what happens. Guess it can't hurt to re-visit RPM land for a bit, right? :D

---

### Post by tgalati4 on 2011-06-21
dmesg | more

---

