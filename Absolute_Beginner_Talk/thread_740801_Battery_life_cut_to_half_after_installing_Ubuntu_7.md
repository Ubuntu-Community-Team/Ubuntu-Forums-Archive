---
title: "Battery life cut to half after installing Ubuntu 7.10"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Saardox on 2008-03-31
Before I post my problem, I  want to thank the admirable efforts made by the Ubuntu community. 

I used to have windows a week back but was seduced by the free-software/open-source ideas. This led me to impulsively format my hard drive and install Ubuntu :lolflag: The downfall of  this is that now my battery lifetime is reduce from 3 hours to 1:45m :( which is a significant problem considering I'm a university student.  

Computer: Dell XPS 1210
Battery: DELL YF0815

Thanks for your time. By the way, I'm thinking of getting highly involved in the Ubuntu community.

---

### Post by abhiroopb on 2008-03-31
To start with have you actually timed both windows and ubuntu usage? Because in Windows I have noticed that when it tells you that there is x amount of time remaining it is invariably incorrect. However, although the time remaining on the battery is less in ubuntu it is usually very accurate.

Next there are a few powersaving things that you could try, which have at times worked for me.

1. Install an application called powertop:
Go to Applications>Accessories>Terminal
Type in the following:
```

 sudo apt-get install powertop

```

This will then give you a few options as to what you can do to conserve battery. Unfortunately you have to run this every time you start ubuntu (haven't figured out a way to make the changes recommended stick). Anyway this usually adds about 15mins to 30mins.

2. There is a power management option.
Go To: System>Preferences>Power Management

3. You can try installing laptop mode (which spins down the hard drive in the background to save power:
Again in the terminal:
```

sudo apt-get install laptop-mode-tools

```

Then type in:
```

sudo gedit /etc/default/acpi-support

```
And edit: ENABLE_LAPTOP_MODE=true.
[B][COLOR="Red"]
NB: Do this at your own risk as it is known to cause some problems.[/COLOR][/B]

4. Some more info: [http://www.lynchconsulting.com.au/blog/index.cfm/2008/3/10/Power-saving-tips-for-Ubuntu-on-laptops](http://www.lynchconsulting.com.au/blog/index.cfm/2008/3/10/Power-saving-tips-for-Ubuntu-on-laptops)

Again at your own risk.

5. Trying lowering the brightness of your screen.

Let me know if any of this helps!


If you CPU supports it you can install powernow or cpufreq to control your CPU speed.

---

### Post by stefangr1 on 2008-03-31
You're not the only one with this issue. Have you already tried to disable all desktop effects?

---

### Post by Saardox on 2008-03-31
Hello again: I want to thank everyone that took the time to review my problem and gave me a possible solution. For starters I ran powertop and this is what showed up:


First, I actually compared the windows vs Ubuntu battery life because when using windows in the past, I could spend my whole biology class without plugging my PC and still remain with 30-45 mins left of battery life. This is with 10/10 brightness.Today in Ubuntu, PC only made it to half of the class :(. 

Second: What are the chances of having hardware irreversible damage by doing the suggestions that have a "Use by your own risk" warning? :oops: I'm a noob and to be honest my intentions aren't to ruin my PC permanently. Lol, I can afford software damage though. 

Third: After tryings the suggestions of powertop, the battery lifetime seemed to have improved a little, but still, in the battery characteristics(device information), its still shows that lifetime is 42%(poor).

Forth: Forgive my english, I do not have time to proofread this cause I have an essay due tomorrow jejeje, English is my second language and I just realized that in this post, I repeated too much the word "I" lol. If you find any horrible English mistakes, please tell me jejeje. 

Sixth: Once again thank you all,

-Saardox

---

### Post by abhiroopb on 2008-04-01
hey, no problem you are certainly more polite than a large number of users! And English is more fluent as well.

I personally don't see any huge risks in huging powertop, but perhaps more experienced users can fill you in a little bit better on this one.

I guess its just one of those things. Generally acpi support is bad in linux, stuff like hibernate/suspend give problems. My battery is about the same though so don't really know what else to suggest.

---

### Post by Xiong Chiamiov on 2008-04-01
Turning off all the fancy eyecandy should definitely help.  I don't have much experience with gnome, but my roommate experienced double the battery life on his laptop when he switched from vista to Kubuntu, so I guess it depends a lot on what you come from, as well as what desktop manager and such you use.

---

### Post by justleen on 2008-04-01
there is no hardware risk, all your changing is settings for the OS (an OS cannot damage the hardware easily, only things line BIOS flashing, and overclocking )

Did you make sure the desktop effects are enabled?  ( System > Preferences > Appearance > Visual Effects (Tab)  )
I could take my laptop from work in the train to my house, and back without problems. With desktop effects on, i have to plug in at home. so the desktop effects eat more then half of my battery power.

---

### Post by Saardox on 2008-04-01
Ok, I already deactivated all Desktop effects :(:( which suxs cause they rocked. I'm gonna put it to test in the university.

Now, I seem to have a bigger problem. Yesterday, battery lifetime was 42%, and now , it has dropped to 39% (cry). Is it possible for Ubuntu to be ruining my battery? (see attachmen)

---

### Post by justleen on 2008-04-01
> **Saardox said:**
>  Is it possible for Ubuntu to be ruining my battery? (see attachmen)

No. Batteries degrade overtime, thats is normal. I agree its a bit much at once.....

What might be, is due to the quicker discharges you experienced recently, the battery has been "stressed" a bit, causing a poorer capacity. 
This stil doenst mean its ubuntu's fault, if you, for example, where playing games under windows you would have had the same effect.
Is you laptop/battery an older one, by any chance? there are some trick to "revitalize" the battery, that might be worth a try.

edit: [some interresting reading on the topic ]("http://batteryuniversity.com")

---

### Post by Boyohazard on 2008-04-01
Judging by the screenshot your battery is not holding the charge anymore. How old is it?

I suggest running it flat (use a discharger if you have access to one), recharge it then discharge again before giving it another charge

---

### Post by mjwhitfield on 2008-04-01
> **Saardox said:**
> Is it possible for Ubuntu to be ruining my battery? (see attachmen)My Magic 8-Ball says "no".

If your battery is dying however, that's not a good thing.  I always let mine run down to 0% before charging it again to 100%, it's been very healthy.

---

### Post by Eddi3 on 2008-04-26
> **mjwhitfield said:**
> My Magic 8-Ball says "no".

If your battery is dying however, that's not a good thing.  I always let mine run down to 0% before charging it again to 100%, it's been very healthy.

I hate to burst your bubble, but this is completely untrue of modern batteries. Lithium batteries work in a way such that discharging damages them.

In fact, letting them run down to 0 like that can accelerate your batteries degradation rate by up to 40%

I know this thread is old, I just thought you should have a chance to know.

---

### Post by cindylivengood on 2008-04-26
> **Eddi3 said:**
> I hate to burst your bubble, but this is completely untrue of modern batteries. Lithium batteries work in a way such that discharging damages them.

In fact, letting them run down to 0 like that can accelerate your batteries degradation rate by up to 40%

I know this thread is old, I just thought you should have a chance to know.

The thread might be old, but this noob found it because you posted, and now I know something I didn't know before.  Thanks!  Your diligence is appreciated.

---

### Post by abhiroopb on 2008-04-26
There are so many conflicting things I hear about the batteries!

---

