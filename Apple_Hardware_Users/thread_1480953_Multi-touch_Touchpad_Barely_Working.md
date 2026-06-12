---
title: "Multi-touch Touchpad Barely Working"
date: 2010-05-12
forum: Apple Hardware Users
---

### Post by oscargodson on 2010-05-12
As you know the new MacBook Pros (Intel i5's / Generation 6's) dont have "buttons". The button is the entire touchpad, so, using the touchpad on Ubuntu is near impossible for real use. Like a normal laptop, I rest my thumb on the bottom of the touchpad where on a normal touchpad the button would be but when I do that the cursor doesn't move because it thinks there are two fingers on the touchpad.

And typing... well just the heat of my hand moves the cursor and clicks it while I type messing everything i typed up. I can't use Ubuntu like this. :(

Does anyone know of a driver yet for this like the ones that come with Snow Leopard for Windows with Boot Camp? Please, someone has had to have fixed this by now since the buttonless Macs have been around awhile now... :'(

---

### Post by jwbrase on 2010-05-12
The System76 Pangolin has a similar setup, touchpad with no buttons*, though the touchpad is smaller (I'm not sure if it's multitouch or not). 

I simply plug my normal mouse into a USB port and turn the touchpad off if there's at all enough room for the normal mouse, because I loathe and despise touchpads, buttons or no buttons, for many of the reasons you have described and a few others as well.

*Actually, I thought the touchpad didn't have buttons, but I just found out while writing this that they just don't stick out, but are there. But my point remains: Touchpads are a pain to use anyways (if I actually used my touchpad, I would have found out by now that there are buttons), so spare yourself the agony, turn the touchpad off, and use a real mouse. It's much more comfortable.

---

### Post by alexmurray on 2010-05-12
Try using the multitouch driver and the bcm5974-dkms driver from the mactel-support ppa - see this post [http://ubuntuforums.org/showpost.php?p=9193610&postcount=130](http://ubuntuforums.org/showpost.php?p=9193610&postcount=130) for more info on how to install it. Also post your thoughts etc in that thread too.

---

### Post by oscargodson on 2010-05-13
> **jwbrase said:**
> The System76 Pangolin has a similar setup, touchpad with no buttons*, though the touchpad is smaller (I'm not sure if it's multitouch or not). 

I simply plug my normal mouse into a USB port and turn the touchpad off if there's at all enough room for the normal mouse, because I loathe and despise touchpads, buttons or no buttons, for many of the reasons you have described and a few others as well.

*Actually, I thought the touchpad didn't have buttons, but I just found out while writing this that they just don't stick out, but are there. But my point remains: Touchpads are a pain to use anyways (if I actually used my touchpad, I would have found out by now that there are buttons), so spare yourself the agony, turn the touchpad off, and use a real mouse. It's much more comfortable.

For me, the MBP touchpads have always been awesome. Now, my HP Mini 1000, couldn't stand whatsoever, and my VAIO's was WAY to small and the scolling was finicky. But i have multitouch on my mac touchpads so, like, three fingers up shows all my windows, three fingers down hides them all, etc. So, I NEED multitouch :) it's become a way of life. Even with a mouse I see myself with one had on the touchpad to do gestures like that.


@alexmurray thanks, ill try it out and let everyone know :)

---

### Post by ticklecricket on 2010-05-14
Two things you can do to make life easier.

1) Go to touchpad settings and disable tap to touch, that will help you if the mouse seems t0o sensitive and jumpy. Though, maybe that's not the problem you have.

2) I haven't figured out how to make the multitouch work like it does in OSX. (Namely, I don't know how to configure compiz to do the things you can do in OSX like expose and such) But you can go to Mouse settings and the touchpad tab and enable two finger scrolling.

---

### Post by oscargodson on 2010-05-14
> **ticklecricket said:**
> Two things you can do to make life easier.

1) Go to touchpad settings and disable tap to touch, that will help you if the mouse seems t0o sensitive and jumpy. Though, maybe that's not the problem you have.

2) I haven't figured out how to make the multitouch work like it does in OSX. (Namely, I don't know how to configure compiz to do the things you can do in OSX like expose and such) But you can go to Mouse settings and the touchpad tab and enable two finger scrolling.

1) Thanks, but if I did that, I literally couldn't do certain things at all like highlight text, drag windows, etc because i need two fingers (one to click and one to move the cursor). Now i have to double tap to do anything. I just want my Ubuntu back!

2) Its not as big of a deal, two finger scrolling is the number 1 thing, the others i can live without as long as i had a working touchpad :)

---

### Post by tylerisfat on 2010-05-28
I've got expo set on button 9, or middle click, which is the top right of my touch pad. its definitely possible to assign different things like expo to button presses, but i don't know about gestures. maybe set 3 or 4 fingers to button 8 or 9, or something, then set expo to activate on that.

> **ticklecricket said:**
> Two things you can do to make life easier.

1) Go to touchpad settings and disable tap to touch, that will help you if the mouse seems t0o sensitive and jumpy. Though, maybe that's not the problem you have.

2) I haven't figured out how to make the multitouch work like it does in OSX. (Namely, I don't know how to configure compiz to do the things you can do in OSX like expose and such) But you can go to Mouse settings and the touchpad tab and enable two finger scrolling.

---

### Post by oscargodson on 2010-06-08
Still... no one knows? How are people using their 6th gen MBPs at all?!

---

### Post by alexmurray on 2010-06-08
> **alexmurray said:**
> Try using the multitouch driver and the bcm5974-dkms driver from the mactel-support ppa - see this post [http://ubuntuforums.org/showpost.php?p=9193610&postcount=130](http://ubuntuforums.org/showpost.php?p=9193610&postcount=130) for more info on how to install it. Also post your thoughts etc in that thread too.

As I said above, use the multitouch driver instead.

---

### Post by oscargodson on 2010-06-09
Sorry for being a moron, yeah, i did that and now its actually working :) 

P.S. yeah, the gestures and tap to click **dont** work, but I guess I can live with it haha.

---

### Post by pooya72 on 2010-06-09
Did you also try installing the touchpad preferences panel, and lowering the sensitivity?

---

### Post by oscargodson on 2010-06-09
oh no, is that in the app store or do i need some terminal code?

---

### Post by linuxopjemac on 2010-06-09
```
sudo apt-get install gsynaptics
gsynaptics
```

adjust sensitivity

---

### Post by alexmurray on 2010-06-09
There is no need to install gsynaptics - and besides I doubt it will work with the multitouch driver as it is for synaptics - linuxopjemac please stop posting unhelpful comments which are blatently wrong.

Instead you can simply go to Preferences -> Mouse and adjust the sensitivity there if needed.

---

### Post by oscargodson on 2010-06-10
so there is no way to get tap to click? :\ I don't want it to install and then break...

---

### Post by linuxopjemac on 2010-06-10
Sorry Alex, just trying to help.

---

