---
title: "Firefox freezes"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-04-15
Hi All

Need a little help;  I am running Xubuntu 6:10 and FF keeps freezing from time to time;  I have my private data everytime I close FF but that doesn seem to help:  If this were windows, I would probably post a HJT log for you but I don know of a diagnostic program like that for Linux.

Here is something though.  I noticed that when it freezes, I take a look at the process manager and it is in stopped status as opposed to running status.  I try to make continue, but that doesnt seem to help either.

Any thoughts?:popcorn:

---

### Post by tchoklat on 2007-04-15
This is odd. Are you using the latest version? You could uninstall and reinstall it through apt-get and see if that fixes it or use Opera?

---

### Post by Xoanan on 2007-04-17
Thanx for the advice;  I have installed Opera (to make sure I have a browser before I attempt reinstalling FF).  How would I install flash on this?
I am running Xubuntu only(in other words, I have no other OS's on here) and the only options I see for opera is for Windows and Mac.

---

### Post by Xoanan on 2007-04-17
Nevermind;  I found a way to install the plugin through prefs;  I couldnt believe how easy it was!! LOL!

Thanx All!

---

### Post by Xoanan on 2007-04-25
Hi All

Same issue;  I have been able to make Opera work with flash; although it will not show some of the content of Nick Jr for some reason.  

As for FF, I cannot uninstall it without uninstalling the Xfce Desktop according to the Synaptic.  I was able to mark it for upgrade though.   We will see what happens:popcorn:

---

### Post by Xoanan on 2007-04-25
So far no luck;  FF still has tendency to freeze(I am not sure that freeze is the correct word).  A little more detail for you.  If I launch FF and I go to Ubuntu or Google etc, most of the time, its fine.  When I go to a gaming site such as mofunzone and play a few an online game, its fine.  If I try to navigate away from the gaming site, that is when FF freezes or hangs.  

I suppose that it might have something to do with Flash, but this is fresh install of Flash so....

---

### Post by vratnica on 2007-05-08
firefox freezes by me too, on feisty

sometimes I cannot save a picture from sites. and when I write "top" in the commandline, I cannot see firefox anywhere!, so I cannot kill the process through firefox, too

---

### Post by pospam on 2007-05-20
My firefox is also freezing from time to time in Ubuntu Feisty.
What I did was to disable all extensions and now it seems to be working quite well.
I will turn on one at a time and check which one is causing the trouble.
Maybe other people can try this and post their results.
Cheers
P.

---

### Post by redenex on 2007-06-02
I have the same issue, I am on Feisty Kubuntu. I do not go to gaming sites, but FireFox freezes even while I type in something on the browser address bar or when I open site where I have to login, say like my email site or some forums. Well...... :(

---

### Post by redenex on 2007-06-02
hmmmmm &#618; removed &#609;nome and kde and installed xfce, now &#618;am not facing this problem! Well, only time will tell though.

---

### Post by redenex on 2007-06-02
Sorry, I spoke too soon. For me is freezes, when I select saved information on forms - say like when I try to login to my email  or  even when I type in URL on the address bar, or type in something in google search.

---

### Post by Xoanan on 2007-06-08
I am still having the same issue as well;

It still happens with other browsers though. 
I loaded the cpu usage graph to check it while FF or Mozilla Suite were running.  I noticed pretty high CPU usage when I was loading the FF or Mozilla, although it leveled off abit afterworads. When switching to other sites, it tends to have a pretty heavy load.

The odd thing is, when it "hangs" the cpu usage is 0 which basically tells me that it is not actually running.  Its almost as if Xubuntu was shutting FF down for some reason.  Still looking into it

Incidently, this is not the only app. that has heavy load on the CPU; the GIMP will do that too when it loads.  

I will keep testing.  I am sure there is a work around for it

---

### Post by Xoanan on 2007-06-17
I am not sure, why, but FF is no longer freezing.  In another thread as well as this one, I mentioned that my CPU was being eaten up apparently by the panels.  Happy Man said that the panels have become memory sink, so what I have do is eliminated some of the stuff I placed on them(such as the cpu usage graph I was using to diagnose the FF issue).  

I am no traveling at warp speed on my machine.  I have left the pc and FF was open for several hours with no sign of freezing.  I even went to the gaming site I mentioned without experiencing a problem(except that I lost the game:p).  

Check your panels, see if the issue is actually there and not necessarily in the browser.

Of course, my issue may be different so....

---

### Post by Xoanan on 2007-06-17
Oops;  Spoke too soon.  I had the game site open while I was typing my last post.  After I finished posting, I attempted to close the tab and then FF froze.  Evidently, there is something about that site that FF doesn like.  I am not sure what. 

However, the whole FF experience has been better since I removed a few items from the panels.

---

### Post by emzo on 2007-06-19
Ok guys,

I think I finally resolved this issue by some kind of workaround.. 
Try **SwiftFox** ;)

SwiftFox is Firefox compiled according to CPU used, so I assume it better handles threading or whatever..

The easiest way how to install this is.. via **automatix2** package.. You can find the instructions [here..]("http://www.getautomatix.com/wiki/index.php?title=Installation")

If you are done with this.. simply run the automatix from Gnome menu (Applications/System Tools/Automatix).. and check the Swiftfox..

This resolved my Firefox freezing.. now it rocks.. ;)

GL

---

### Post by Xoanan on 2007-06-19
> **emzo said:**
> Ok guys,

I think I finally resolved this issue by some kind of workaround.. 
Try **SwiftFox** ;)

SwiftFox is Firefox compiled according to CPU used, so I assume it better handles threading or whatever..

The easiest way how to install this is.. via **automatix2** package.. You can find the instructions [here..]("http://www.getautomatix.com/wiki/index.php?title=Installation")

If you are done with this.. simply run the automatix from Gnome menu (Applications/System Tools/Automatix).. and check the Swiftfox..

This resolved my Firefox freezing.. now it rocks.. ;)

GL

Sounds good;  I will have to try that.  :popcorn:

---

### Post by Xoanan on 2007-06-20
I have Swiftfox now.  It does appear to load fast than Firefox, yet it keeps the same bookmarks and same themes so this made the transition a lot easier.  I will keep playing with it to see if I have any freezes.

Cheers!

Xoanan

---

### Post by Xoanan on 2007-06-22
Update, still having a few issues with browser hangs even with Swiftfox.  Part of it could be panel issues, though.  Will check later

---

### Post by emzo on 2007-06-25
Are you using any Tab extension? For example I use Tab Mix Plus and I experience no hangs.. This extension replaces the built-in session recovery feature.. Maybe it helps..

---

### Post by Crafty Kisses on 2007-06-25
> **Xoanan said:**
> Hi All

Need a little help;  I am running Xubuntu 6:10 and FF keeps freezing from time to time;  I have my private data everytime I close FF but that doesn seem to help:  If this were windows, I would probably post a HJT log for you but I don know of a diagnostic program like that for Linux.

Here is something though.  I noticed that when it freezes, I take a look at the process manager and it is in stopped status as opposed to running status.  I try to make continue, but that doesnt seem to help either.

Any thoughts?:popcorn:

It could be a resource issue, check how much CPU% is being used at the time of the crash.

---

### Post by Xoanan on 2007-06-25
Already done;  I checked free -m even before I started Swiftox.  I only have 138 MB of RAM and a lot of that is taken already.  I only have about 2 or MB free at the moment.  A lot of my issue is RAM based.  Unfortunately, I need Dell Compatible PC133s rather than generic PC133s.   It cost about $40.00 to 256 mem stick:popcorn:
Thanx for the reply though.

---

