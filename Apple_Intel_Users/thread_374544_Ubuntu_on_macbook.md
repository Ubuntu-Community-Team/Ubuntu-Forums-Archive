---
title: "Ubuntu on macbook"
date: 2007-03-02
forum: Apple Intel Users
---

### Post by mR. GULEROD on 2007-03-02
Does ubuntu works on a intel macbook?
And if it does, then do every thing works, like GMA 950 and wireless?

Also can you remove mac s x from a mac book and then use ubuntu instead?

---

### Post by oskarloko on 2007-03-05
yes, yes, yes.

See on [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
And search within forum...

---

### Post by mustang on 2007-03-05
> **mR. GULEROD said:**
> Does ubuntu works on a intel macbook?
And if it does, then do every thing works, like GMA 950 and wireless?

Also can you remove mac s x from a mac book and then use ubuntu instead?

Video works. For wireless, you will need ndiswrapper if you are using a second generation macbook. Many key features such as power management and suspend do *not* work without significant tweaking and even then, you have to get lucky. So no, I wouldn't say everything works.

You can remove mac osx and just run ubuntu. This would not be recommended since you can only get firmware updates through osx.

---

### Post by ouilsen on 2007-03-05
After days of testing many distributions, I have to say that Feisty is the only one where _everything_ works.  Suspend f.ex. works out of the box.

I followed this [guide]("https://help.ubuntu.com/community/MacBook"). Some steps  were different.

1) Ndiswrapper. I had to download the newest version (1.38 ) and use the lenovo driver.
2) The trackpad. You have to get the appletouch module to load before usbhid. I found this [guide]("http://wiki.debian.org/MacBook"). This initramfs stuff was important.

Now if I had skype with webcam working I could ditch OS X.

Btw... I'm using a C2D.

---

### Post by Movi on 2007-03-07
Well then you got lucky, because Suspend DOESN'T work for me - even though i even tried to make my own kernel using the mactel-linux site. Maybe ill try to reinstall using a more recent livecd (rather than updating). Are you using refit or just plain Boot camp?

---

### Post by ouilsen on 2007-03-08
I use both refit and bootcamp. Bootcamp to resize my hfs+ partition and refit to have a nice boot menu and the bios simulated.

Maybe your kernel wasn't updated because you built your own one? I did a fresh install with herd 5 and suspend has never crashed.

---

### Post by Movi on 2007-03-08
No, the updates got thru - i tried both .20-8-generic and .20-9-generic, and again my custom one (which btw i never bothered to install "The debian way" making a deb). Im getting the daily cd now, and gonna start anew. If it wont work then ill just wait till feisty is released (not much to go).

---

### Post by bsantos on 2007-03-28
I also had success with suspend and hibernate on a C2D. Suspend is flawless and fast, hibernation takes a little more and looks way too "dirty" right now. It drops to console, a bunch of debug information shows up, there's no pretty usplash, nothing. On boot the usplash seem to hang at the beginning and all of a sudden you get your state back. It works, at least on my system, but it is an ugly process. :)

---

### Post by mustang on 2007-03-28
bsantos,

did you make any changes/tweaks to get suspend working or did it work out of the box? Any boot parameters?

---

### Post by bsantos on 2007-03-28
Nop, just lpj=8000000. It's a C2D.

---

### Post by mustang on 2007-03-28
Hm I don't have that but it any case, it's not related to suspend. That's really weird--why would suspend work okay for the c2d's but not the cd's?

edit: has anyone tried their macbook with fedora? is it any better?

---

### Post by fredronn on 2007-03-29
Has anyone gotten suspend (to ram) to work reliably on a Macbook cd (not c2d)? I've gotten suspend to disk to work once (out of a few attempts). Even so, I don't know how or why it worked.

Seconding the fedora question, I've come across sentences on the web that it works (Macbook CD on Fedora supporting suspend to ram), but unfortunately nothing confirmed. I'm hesitant wasting my time without confirmation. And I really prefer ubuntu.

Some clarification: The machine falls asleep, but will not respond to any input making it wake up; Lid opening, keyboard, power button...

---

### Post by mustang on 2007-03-29
> **fredronn said:**
> Has anyone gotten suspend (to ram) to work reliably on a Macbook cd (not c2d)? I've gotten suspend to disk to work once (out of a few attempts). Even so, I don't know how or why it worked.

Seconding the fedora question, I've come across sentences on the web that it works (Macbook CD on Fedora supporting suspend to ram), but unfortunately nothing confirmed. I'm hesitant wasting my time without confirmation. And I really prefer ubuntu.

Some clarification: The machine falls asleep, but will not respond to any input making it wake up; Lid opening, keyboard, power button...

Fredconn--I'm having the same problem as you. 

I actually gave fedora a try last night and suspend to ram still doesn't work before and after package updates. We'll just have to wait patiently and hope it gets resolved.

---

### Post by fredronn on 2007-03-29
> **mustang said:**
> Fredconn--I'm having the same problem as you. 

I actually gave fedora a try last night and suspend to ram still doesn't work before and after package updates. We'll just have to wait patiently and hope it gets resolved.

Thanks for posting that piece of info, saves me the time to try out fedora myself. I'm actually considering giving gentoo a go.

---

