---
title: "Help running .exe with Wine"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-06
I downloaded an exe file from the lenovo website to determine whether or not something is wrong with my battery. The instructions say that I should install it and it will immediately open a browser with a window telling me if there is anything wrong. I ran the exe file under wine and installed the file but nothing happened. What do i do?

EDIT: the instructions can be found here, if you need reference 

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=BATT-LENOVO#details](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=BATT-LENOVO#details)

---

### Post by philinux on 2008-01-06
With wine installed I normally download the exe to my desktop and double click the exe file to install the program.

Unfortunately not all apps work with wine.

There is an app from synaptic called battery-stats

Not sure if this is what your needing.

---

### Post by JoshuaRL on 2008-01-06
Doesn't look like it Philinux.  I think from the link that this is a way to see if he has a recalled battery.

I hate to ask this, but do you dual boot?  If so just try it there.  If not, well, I'm not sure.  

There's a couple things you could try.  When you first ran Wine you configured it, right?  You'll probably want to run it as an XP machine for this I would guess.  You could go to the WINE website and download the newest version to make sure you have the freshest release.  And if it's really that important, you could try running a virtual machine with XP.

---

### Post by mister_pink on 2008-01-06
If this is something thats meant to be looking at the hardware then a virtual machine is going to get you nowhere - virtual machines have virtual hardware. I doubt wine will work with this either. I would think dual boot or use some other method of finding what you want from this program. What exactly is it meant to tell you?

---

### Post by philinux on 2008-01-06
> Doesn't look like it Philinux. I think from the link that this is a way to see if he has a recalled battery.

Your right.

I'd use option 2 and find the battery code. Much simpler.

---

### Post by intense.ego on 2008-01-06
I installed battery stats but do not know how to open it. It will be useful but it is not what I am looking for. The exe i am talking about determines whether or not my battery needs to be recalled. Perhaps this is happening because there is no web browser under wine?

EDIT: Sorry, I had the window open and didn't refresh before posting. I think i will either try option 2 or I will boot into my windows partition (it will be my first time in 7 months since I installed ubuntu). But, for now, I am going to sleep.

---

### Post by JoshuaRL on 2008-01-06
Yeah I agree that's about the only option short of installing Windows on a dual boot just for this.

That would be a huge waste.  But kind of funny.

And points to mister_pink for remembering that virtual machines run virtual harware too.  Man, I totally forgot that.  And I think the app is to check to see if the laptop battery is one that was recalled so it can be replaced.

Or maybe you're really fortunate and you just need to configure WINE a little differently.  Let's hope.

EDIT
Oh man, just boot into Windows if you have it already.  That will be MUCH easier.  This kind of hardware utility never runs well in WINE.  I'm the second to last person to tell anyone to go to Windows (well, there is RMS afterall) but I would totally do it if I was you.
/EDIT

---

### Post by mister_pink on 2008-01-06
Wine has a browser of sorts, but I would expect it to use your normal browser anyway. I suspect that the problem here is simply that the program won't work with wine, which isn't that surprising given what its trying to do. Can you not just look at the serial code written on the battery and type it into that website to see if you need to send it back? Its option 2 on the site and doesn't sound too difficult!

---

