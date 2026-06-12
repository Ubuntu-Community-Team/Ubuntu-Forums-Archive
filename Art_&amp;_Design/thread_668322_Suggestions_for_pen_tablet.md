---
title: "Suggestions for pen tablet?"
date: 2008-01-15
forum: Art &amp; Design
---

### Post by FriedChips on 2008-01-15
Hello fellow forum folk,
Looking for a good reasonably priced pen tablet, verified to work with Fedora and GIMP. I'm new to all this and to be quite honest I am not very artistically talented, but looking to change that. I am looking for a something probably low to mid-range I guess. Something that will last, I have read reviews on cheaper pen tablets that say the pens wear out and blah blah blah. This is a big investment for someone who doesn't do much in graphics. Let me know if you have any suggestions. Just to name a price, I'd like to spend under 100 USD. Thanks for any and all input, have a wonderful day.

---

### Post by nikoPSK on 2008-01-15
I have a wacom, it's nice. :)

---

### Post by exile on 2008-01-15
I second the Wacom tablet. Never had a problem with it and it's well supported in linux land.

---

### Post by nikoPSK on 2008-01-15
> **exile said:**
> I second the Wacom tablet. Never had a problem with it and it's well supported in linux land.

exactly. It's nice too :) (but larger ones are pricey...)

---

### Post by FriedChips on 2008-01-15
thanks guys, any downfall to getting a lower end bamboo wacom? The better ones are quite pricy

---

### Post by nikoPSK on 2008-01-15
not really. although I am happy with my size. I had to shell out an extra 80 for it though. don't get too small. :)

---

### Post by FriedChips on 2008-01-16
[This](http://www.compuplus.com/i-Wacom-MTE450-Bamboo-Black-Digitizing-Tablet-For-Digital-Inking-Applications-1010992~.html?sid=o5ahw6tsu3pr3y7) is the one I'm thinking about getting. The price is definetely right :)

---

### Post by sloggerkhan on 2008-01-16
i've got a wacom CTE-440, it works okay for me. 5x3.5" working area. Was like $70ish on newegg a while back, but I don't think they sell them anymore.

I think you can get the bamboo ones working, but I am not sure it's as straightforward as they are newer. Anybody else have info on this?

---

### Post by digitalis_vulgaris on 2008-01-16
I use Wacom Graphire 2 tablet. Graphire tablets work like a dream on Ubuntu. Just plug tablet on USB port and everything works. I try Wacom Volito, but it wasn't working OK. Everything under 1cm from table's plate Ubuntu detected like click. But, with Volito, costumer get a new ArtRage, which works great under Wine. So, if you can make Volito to work fine under Ubuntu, it's a good trade.

---

### Post by FriedChips on 2008-01-16
> Here comes the promised 0.7.8. Enjoy!

It has the following new features: Provides prebuilt Wacom X driver and its utility programs for x86_32 and x86_64 systems. Supports new tablet, Bamboo. Adds many new xsetwacom options: Keystroke, Modifier, DebugLevel, CommonDBG, TVResolution0/1, Screen_No, TwinView, RawSample, etc. Refer to ChangeLog for details. 

looks like the newest stable code supports bamboo tablets, and as always the development branch is ahead of that so that would be worth a shot to if I need to.

---

### Post by Hmarroqu on 2008-02-23
> **FriedChips said:**
> [This]("http://www.compuplus.com/i-Wacom-MTE450-Bamboo-Black-Digitizing-Tablet-For-Digital-Inking-Applications-1010992%7E.html?sid=o5ahw6tsu3pr3y7") is the one I'm thinking about getting. The price is definetely right :)

I got this one and have no clue where to begin to get it to work...HELP PWEEEZ

Much appreciated...

---

### Post by red_Marvin on 2008-02-24
I have an A6 size wacom bamboo (I couldn't see the size in the link), which work perfectly in Gutsy. Installation instructions [[here]]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133").
However I haven't got the wacomcpl program to detect my pad buttons (except for one) but I can configure everything with the xsetwacom command.
Like this:
```
xsetwacom set pad Button1 "core key CTRL ALT Left"
xsetwacom set pad Button2 "core key SUPER e"
xsetwacom set pad Button3 "core key CTRL ALT Right"
xsetwacom set pad Button4 "core key CTRL z"
```

---

### Post by littlemog on 2008-02-24
haven't tried the bamboo yet... let us know how it is! (i'm on graphire atm)

---

### Post by SpiderGorilla on 2008-02-24
I have a Wacom Bamboo and I've followed neko18's instructions on getting it to work properly with my system. I had to use  a development version of the wacom drivers, but they're very stable. I can confirm my tablet works properly (pressure and all) in the following applications:

The GIMP
Krita
Inkscape*
Xara Xtreme*
KToon*
Synfig*

*These programs take the tablet as mouse input, ignoring pressure sensitivity. This is due to program functionality, I believe, not tablet malfunction.

---

### Post by backinthecity on 2008-02-26
The Bambo Fun is the one i have... priced around $100 (starting) its a very good tablet. If your familiar with "nicer" tablets it may be a step back. But if not it is a REALLY good tablet to start off with. The pressure sensitivity isn't as sensitive as higher end models but it is definitely  not noticeable. Size that is all preference. I draw with my wrist more than anything so the smaller size actually fits me very well. Now if you draw "properly" (with your entire arm/shoulder)  you may want to get a bigger size. 

all in all the bambo is worth every penny you'll pay on it.

---

### Post by Linuxratty on 2008-02-26
I had no idea you could make these work in Linux...Excellent news!

---

### Post by Creative2 on 2008-02-26
:) my wacom it's so nice...with video "how to"
[http://www.youtube.com/watch?v=738kyim12G0](http://www.youtube.com/watch?v=738kyim12G0)

---

### Post by Zeotronic on 2008-02-26
I've wanted to get such a tablet, but I have worries about getting something that doesn't have the display on it... something I cant see the lines I have made on... and while I know that Wacom makes graphics tablets that *do* have their own display, I am not rich. Should I be worried about such things?

---

### Post by backinthecity on 2008-02-27
Honstly you shouldn't be worried you kind of get use to it. The only downfall i have with the tablet is you can't rotate it to get a better angle...its extremely difficult to get use to. You kind of have to get use to drawing at angles your not use to drawing. I know this is hard to understand sorry. but plain and simple the displays are nice to be able to rotate the tablet so your more comfortable. But don't think i'm putting down the "non-display" tablets (i have one myself "Wacom Bamboo Fun") but its just things you have to get use to. 

I'm confusing myself. 
-drake

---

