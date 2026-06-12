---
title: "ubuntu booting slowws so much"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-02-20
I noticed that on my grub menu there are three ubuntu kernel things as well as three safe modes for each, also before it boots it says something about a maximum cylinder for the grub.  I have no idea wat this all means but i think it also correlates to why my ubunut takes sooo much longer now to boot. before it would be like 30 secs, now its about 2-3 minuts.  I have a fairly new laptop, toshiba satellite m55.  1.6ghz, 1gRAM, 100G HDD. anyone have any idea of why ubuntu slows down so much and how i can go about deleting like 2 extra kernels on the grub? 

thanks!!!:guitar:

---

### Post by po0f on 2007-02-20
Hmarroqu,

Do you boot with the quiet option on, ie does usplash show any text or does it show just a progress bar when booting?  If we could find the step it's stalling on, maybe we can get it fixed.

---

### Post by BarfBag on 2007-02-20
Not sure about the slow booting, but I can help you remove those extra entries.

Open Terminal.  It's in Applications -> Accessories.  The Grub config file is located at /boot/grub/menu.lst.  You should back it up before making changes.

> cp /boot/grub/menu.lst /home/**Your User Name**/menu.lst

Then, edit it.

> gksudo gedit /boot/grub/menu.lst

Just find the extra entries and delete them.

Hope this helps.

---

### Post by po0f on 2007-02-20
BarfBag,

Or, the OP could just uninstall the unneeded kernels.  :)

---

### Post by zachalekos on 2007-02-20
I've had the same problem for the lat couple of days. Before it used to load very quickly but now it takes up to 3 mins. Any help would be appreciated.

---

### Post by TheWizzard on 2007-02-20
as suggested before. boot without quit mode and look where it stalls

---

### Post by zachalekos on 2007-02-20
I just did it. It's booting alright now, but somehow i don't think it'll be the same later on. It's  weird, when i turn the laptop on in the morning it takes so long, but when i do it later on the day, it's not a problem.

---

### Post by Hmarroqu on 2007-02-20
WTF! as soon as i rebooted to see what it slowed down on it went normal.! its fukin with me! but, i can recall it usually getting stuck on "reading files needed to boot" and im also pretty sure its on "loading hardware drivers"

---

### Post by rusty4r on 2007-02-20
It's just an opinion but I would keep the last kernel before the one you are using as another boot option. Instead of deleting it I would just put one of these # in front of the lines for that kernel.

I downloaded a program called Bum which had boot options that enabled me to turn off some services that were starting at boot and wasting my time. For example blue tooth services when I have no bluetooth devices.

This post is where I learned about it.
[URL="http://www.ubuntuforums.org/showthread.php?t=345235&highlight=bum"]http://www.ubuntuforums.org/showthread.php?t=345235&highlight=bum
[/URL]

Hope it helps.

---

### Post by zachalekos on 2007-02-21
I've got BUM installed but can't find anything that might be slowing down the lappie. BTW, I just turned it on and it was, again, really slow, but when i restart it's normal, it seems like it's only happening when the lapppie is cold and off for a few hours. It beats me.

---

### Post by zachalekos on 2007-02-23
I just found out that the system is stalling when it says, "Reading files needed to boot..."

Anyone help, pls?

---

### Post by gigaferz on 2007-02-23
Actually its kinda sad to see my and old gateway with kubuntu boots in 1 minute10 sec, and the computer i use here it (its just a 3year old) takes 6 to 8, but sometimes it boots normally.

i thought It was the hard drive but , I have been seeing a few threads with the same problem, so it could be software related

In my situation it happens when preparing restricted drivers, keep an eye on it everyday....It could change

Hopefully somebody might help us.

---

### Post by TheWizzard on 2007-02-23
> **zachalekos said:**
> I just found out that the system is stalling when it says, "Reading files needed to boot..."

Anyone help, pls?

no clue, sorry.

---

### Post by Hmarroqu on 2007-02-25
a shot in the dark here, i crinch to compare buntu w/ windoze but could it be taht the files needed to boot need to be organized or somethings, kinda like the whoel disk defrag nonsense ur supposed to do with windoz?:confused::(

---

### Post by gigaferz on 2007-02-27
Increrdible the real speed of linux over windows!!

Real multitasking power!!!!


Too bad it's just today....

Has anybody else fixed their problem????

Anybody there???

---

### Post by ubuntwerreulover0.023.231 on 2007-02-27
do you have windows?

---

### Post by gigaferz on 2007-02-27
yeah

on a laptop and in my computer at home.

The laptop has windows 2000, and in my house its windows xp home.

and i have a kubuntu hardrive at here at work, and a 800mhz kubuntu at home.

Why do you ask?

Almost every computer ,either, has it or had it.

Remember, there are many things that will keep you on windows, wireless internet, networking, and gaming and one or 2 applications with no substitute for linux.

Im trying to make my wireless usb card to work to I will get rid of win2k, but no luck yet. 

And im thinking to make my main computer pure linux, but I need to work many things out before doing that.

---

### Post by zachalekos on 2007-03-01
Well. I just reinstalled Ubuntu (without Beryl) and everything seems to be fine, just the way it used to be, so I guess, I'll keep you posted if something is up.

---

### Post by dannyboy79 on 2007-03-01
this is awesome, I just did this and it helped tremendously but it doesn't work for edgy I believe because of edgy not using init.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by gigaferz on 2007-03-03
ill try it on monday,,,But any idea why it happened, It was booting fine one day then later, it went slow,

The last couple of days my machine has been stating in less than 2 minutes, ..but Ill do it just to prevent  it  for the future.

---

