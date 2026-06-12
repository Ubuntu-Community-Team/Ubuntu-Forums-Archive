---
title: "How to change date format?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by pemimpin on 2008-03-24
My problem is really simple. Yet i did'nt find the answer.

The default ubuntu date format is mm/dd/yy. but it confuse me since i live in malaysia and my country use dd/mm/yy.

Can someone help me....pleeeeaaaseee..

---

### Post by Joeb454 on 2008-03-24
Check System>Administration>Time and Date :)

Your date format is set to the US version :)

---

### Post by Barrucadu on 2008-03-24
Silly US date format... That's always the first thing I change, if not done so already.

---

### Post by Joeb454 on 2008-03-24
Usually it will do it for you on install, I find it quite odd that it didn't do it...

---

### Post by Dr Small on 2008-03-24
> **Barrucadu said:**
> Silly US date format... That's always the first thing I change, if not done so already.
And I can't read nothing but mm/dd/YY :D

---

### Post by Joeb454 on 2008-03-24
Which means Dr Small == Silly ;)

---

### Post by Golem XIV on 2008-03-24
Assuming you' re using Gutsy...

Open the configuration editor by running gconf-editor in a terminal (it's also in the Applications -> System Tools menu but disabled by default; you can use the menu editor to enable it and then run it from the menu).

Expand apps -> panel -> applets and find the clock applet, expand it and click on "Prefs" on the left hand panel.  Now on the right-hand panel, under custom_format enter the format string in strftime() format (you can find [more information on that format here]("http://www.opengroup.org/onlinepubs/007908799/xsh/strftime.html")).

For example, **%d-%m-%Y %H:%M:%S** would give you **24-03-2008 12:28:33**.  there are many other options, so feel free to experiment.

Note that sometimes you have to right-click on the clock, choose "Preferences" and select the custom format from there for the new format to take over.

---

### Post by LowSky on 2008-03-24
Here's a funny story

I got a check from a European bank, with a date of 24/3/07 the date was dd/mm/yy format..I live in america (mm/dd/yy). so i go to the bank and the teller tells me she cant cash it because the check  is  dated incorectly... what a idiot..and a mess I had to get the check reissued because my bank wouldn't cash it.

---

### Post by Cubby on 2008-03-24
Ah, much better.  Thanks, House of Golem!

In clock_screen0>prefs>custom format value I added the following:

%A %d/%m/%Y %H:%M

I tried the lower case letter a for the abbreviated day of the week, but I prefer it in its full glory, including the year.

Make sure to edit the format key and add the value: 
custom

Thank you!

---

### Post by pemimpin on 2008-03-26
thanks golem! :D

---

