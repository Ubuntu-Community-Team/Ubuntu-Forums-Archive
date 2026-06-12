---
title: "Where are the default wallpapers stored ?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-02
I've been trying to mod my desktop a bit, and in the process, have downloaded a bunch of wallpapers. I can't seem to find the folder where they're kept though, and I'd really like to have all my wallpapers in one, tidy place. 

I noticed however, that under /usr/shared  there's a wallpaper folder, which I believe stores ones that are native to the KDE desktop ? In any case, I did add those to my wallpaper list, but would also like to add my downloaded ones either to that folder (which I don't have access to, unless I'm root) or to the one which the default wallpapers are in. So, where are they kept, and will I have access to that folder ?  

Or do I have to creat a separate folder for all my wallpapers anyway ? I guess that wouldn't be such a big deal but, I'm just trying to understand why this method is seeming to be a bit archaic and difficult, since it should be really simple. In this regard, I much prefer the KDE desktop, since it has an automated install process for wallpapers. No muss, no fuss. 

On a related note (desktop modding) I've been using the gdesklette program launcher, which is really nice but I have one gripe with it. As an example, I have firefox open right now, in full screen. So if I need to access another application, I have to either minimize Firefox, or resize it in order to actually get to the gdesklette icons to launch another app.  

This seems pretty redundant to me, in that the extra effort/clicks it takes to resize FF, and then get to the desklette, I could just as easily keep my upper panel visible (I hide it, as I like screen real estate on my small 15" screen) and just go into the menu in order to launch an app from there. My question then is, how can I get the gDesklette app to automatically pop up when I drag my mouse accross the area where it's located ? Is that even possible ? 

TIA.

Doug

---

### Post by taurus on 2006-09-02
You can store them anywhere you want.  On my systems, I store them in ~/pictures and point the program to it...  That's why, I can modify whatever I want without becoming root first!

---

### Post by Sweet Spot on 2006-09-02
Yeah, I figured that. But I was just wondering where the default ones were stored, and also why the ones in /usr/shared/wallpapers     aren't also in that default folder, what purpose does it serve ?  I'm also just curious to know why it seems that there was no intention of putting all wallpapers in one location ?  

On the other topic (gdesklettes) Here's an example of my desktop, and how I have to resize FF (for example) in order to get to the launcher:

[[img]http://img1.putfile.com/thumb/9/24412021132.jpg[/img]](http://www.putfile.com/pic.php?img=3304298)

---

### Post by seedman on 2006-09-02
I'm just a newbie too but I think that I know your answer.
When I download new things I find they land in the directory
/home/seedman
And I am seedman.
your desktop is home/seedman(your user name)/desktop 
the filesystem organisation still slightly confuses me but you get the hang of it after some time.
I'm not %100 on this but, I think that you can't change much outside of the /home/(your user name) because the system permissions won't allow but an average user to change anything to drastic. 
The Ubuntu-users-guide.whatever also really helps. As a candle in darkness to light your way.
I tried attaching it but it's too big. If you can't find it then  you can e-mail me @ [email]shallowlydeep@yahoo.ca[/email]
I hope that I helped.
-M

---

### Post by Sweet Spot on 2006-09-02
Well, thanks for trying to help seedman, but it's not quite what I was asking I'm afraid. To be more specific:  Ya know when you right click on your desktop, and opt to "change desktop background" ?  Well, when you go into that, you're presented with a few wallpapers such as Ubuntu Dawn. I just wanted to know where those particular wallpapers are stored. 

Otherwise, I'm all good at this point. I just created my own wallpaper folder in my Home directory. I just wanted to know though, so that I could try and keep everything in that one. 

I'm still looking for an answer about how to get the gDesklette app to appear though...if anyone can help. 

Doug

---

### Post by skymt on 2006-09-02
The stock wallpapers are in /usr/share/backgrounds.

---

### Post by Sweet Spot on 2006-09-02
Wierd. I actually replied, but looks like it didn't go through. Anyway, thank you skymt, that's what I was looking for. Though I have to admit that I'm a bit confused as to why they chose that directory, since there's also another one named "wallpapers", and both are pretty much off limits unless you're toot, if you want to write to them etc..  Anyway, all's good, and I appreciate the answer.

Though I could still use help with the gdesklette thing ! :-\"

Doug

---

