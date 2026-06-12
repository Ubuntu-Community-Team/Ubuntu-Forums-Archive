---
title: "Some sort of text-based install?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by mdvigi7536 on 2007-01-28
One more question...

Is there a way to install the operating system without going all the way to the desktop?  Between the slow computer and the slow CD drive, it takes 15, 20, 30 minutes inbetween every time I move the mouse or click on something.  Is there some sort of text-based installation or any alternate installation without the whole desktop thing...just to get started?

I've tried Ubuntu, Xubuntu, and the "alternate" Xubuntu and haven't had any luck yet.

--Mike

---

### Post by MkfIbK7a on 2007-01-28
for this you will have to either burn or order an alternate install cd which only does text install

sadly the live cd cant do a text install

wert

---

### Post by taurus on 2007-01-28
You can also try the server CD and then install XFce4 with (after you have installed the server on your machine)

```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by mdvigi7536 on 2007-01-28
Is there something I'm supposed to do before I install this?  I erased the hard drive that had Windows on it...perhaps that was a mistake?  It just thinks and thinks and thinks and doesn't do anything.  I know something is wrong, I just don't know what.

---

### Post by MkfIbK7a on 2007-01-28
in the case that you do what taurus suggested you may also want to install a few programs normally shipped with the desktop

gimp
firefox
...

---

### Post by riven0 on 2007-01-28
> **mdvigi7536 said:**
> Is there something I'm supposed to do before I install this?  I erased the hard drive that had Windows on it...perhaps that was a mistake?  It just thinks and thinks and thinks and doesn't do anything.  I know something is wrong, I just don't know what.

What kind of computer are you running? What's the CPU and RAM? 

I'm guessing you're in the alternate cd installation? If it's giving you problems, make sure you burn the .iso at a low speed: 4kbs is good. And make sure you do a verification.

---

### Post by mdvigi7536 on 2007-01-28
It has 128 MB of ram...no idea about the CPU but it's old old old...say 7 years.  It was advanced when I got it.  

Like I said in the original post, I've tried Ubuntu, Xubuntu, and now I'm on the "alternate" Xubuntu.  The desktop loads from the CD after about ten minutes or so.  I click on the Install icon there and it takes about another ten minutes for the next screen to come up.  It says Install and that it's step one of six (I'll be here a while...).  It asks me to pick the language but the box never has anything in it and the "Forward -->" button is greyed out.  Usually at this point it stops working and just kind of gives up.  I've also tried going to Install through the menu at the top of the screen but if I do that after I've given up on the first install icon I get a "Missing Command" something or other.

Sorry, I don't know codes or anything.  I'm just trying to fix up this old computer and maybe give it to my sister.  When it comes to programming and all that I'm just about as green as they come.

Thanks for any help.  --Mike

---

### Post by MkfIbK7a on 2007-01-28
yes with 128mb of ram you are DEFINETLY going to need to install the xubuntu alternate cd

perhaps even fluxbuntu...

---

### Post by aysiu on 2007-01-28
> **mdvigi7536 said:**
> 
Like I said in the original post, I've tried Ubuntu, Xubuntu, and now I'm on the "alternate" Xubuntu.  The desktop loads from the CD after about ten minutes or so.  If the desktop loads, then you're not using the **Alternate CD**. You're using the Xubuntu **Desktop CD**.

You want to use the **Alternate CD**.

You can see the differences here:
**Alternate CD** - [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
**Desktop CD** - [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

