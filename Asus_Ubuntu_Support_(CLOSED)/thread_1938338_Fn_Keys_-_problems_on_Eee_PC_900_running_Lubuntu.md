---
title: "Fn Keys - problems on Eee PC 900 running Lubuntu"
date: 2012-03-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by stginger on 2012-03-09
I bought this little netbook a few weeks ago and have had fun trying out a bunch of different distros on it. Lubuntu is by far the fastest i have tried (it pains me to use chromium instead of firefox, but its just so much faster).

The problem that i have come across is that the fn keys aren't working properly and it is really starting to wind me up. I thought i'd get used to it, but i'm just not.

The screen brightness keys under f4 and f5 (i think, i'll check in a minute) work correctly, adjusting the brightness up and down and bring up a graphic showing the brightness bar filling and emptying like it should. 

None of the other keys do this properly. some do it, but not correctly.
sleep= broken
wireless= turns the wireless on and off but gives no indication other than the LED going on/off.
mute= broken 
volume up/down= change the volume, but again give no indication and seem to change the volume very slowly.

I have spent hours trying to find an answer, looking at loads of different bits of coding and applications and things, but nothing has worked properly. I am now completely confused and have no idea what to do.

So if you think you can help me out, please tell me what to do. Just assume that i am completely new to all this (because i am :D). 

...also, so if this has been covered before, but please tell me where the answer is, because i haven't been able to find it. 

thanks in advance

stginger

---

### Post by Paddy Landau on 2012-03-10
It may help for you to post the make and model of your computer (and keyboard, if you are using a stand-alone one).

Open your Keyboard Preferences (it may have a different name in Lubuntu). Check that the layout and, in particular, the model have been correctly chosen.

Having done that, open your Additional Drivers to see if there is any driver that you may need to enable. Reboot if you change anything on that screen.

Another thing to check is Keyboard Shortcuts. There, you can specify the keys to use for volume control and some others.

Regarding the control being slow, you may have to live with that. Lubuntu is made for slower computers, so if there is such a difference for you, it may be that your netbook specifications are low.

By the way, nothing stops you from installing Firefox (just open the Ubuntu Software Centre and install it). You can judge whether or not the compromise on speed is worth it for you.

---

### Post by stginger on 2012-03-10
it is an Asus Eee PC 900, with just the standard UK internal keyboard.

i've had a look through all of the keyboard settings i can find and nothing worked. its set to the English standard keyboard, which is correct and there aren't any other options to change.

 I can't find any kind of keyboard shortcut dialogue any where in the system. would i need to install that separately?

as far as i can tell i have looked at every GUI that deals with the keyboard and can't find the right setting.

In my digging i came accross ACPIs quite a lot. what are they and would that be the right thing to look at? 

i installed have been playing with firefox for a few weeks and spent a lot of time trying to use it, but the hardware on the netbook isn't great so its pretty slow, chromium is just much more efficient. 

thanks very much for your advice.

---

### Post by Paddy Landau on 2012-03-10
> **stginger said:**
> I can't find any kind of keyboard shortcut dialogue any where in the system.
Unfortunately, I no longer have a Lubuntu machine. Here is a screen shot of the Ubuntu GUI. I hope that helps.
[attach]214060[/attach]
> **stginger said:**
> In my digging i came accross ACPIs quite a lot. what are they and would that be the right thing to look at?Sorry, I don't know the answer to that.

---

