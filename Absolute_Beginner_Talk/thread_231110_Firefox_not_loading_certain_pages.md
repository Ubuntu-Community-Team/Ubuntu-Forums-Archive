---
title: "Firefox not loading certain pages"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by kircher on 2006-08-07
Hi, I installed ubuntu yesterday for the first time (first time use of linux), and I have gotten this far, but I installed the ubuntu updates, and firefox stopped loading certain webpages. It loads the ubuntu forums, and other basic web pages, but will not load gmail, or my university login. Now my assumption is that it is having trouble with encrypted (SSL) pages. I have no idea how to fix the problem. I don't know if it's an internal firefox problem associated with the update, or one associated with ubuntu itself. I have used firefox for a while with windows xp and haven't had any problems so I'm quite confused. Any help would be greatly appreciated. Thankyou

---

### Post by OU812 on 2006-08-07
Maybe this: do edit>prefs>advanced>security and make sure the ssl boxes are checked.

john

---

### Post by kircher on 2006-08-07
ok, I checked if the ssl boxes were checked, and they all were, then I screwed around with some proxy settings. All I did was choose edit>pref>general>connection settings then chose auto - detect proxy settings and that stopped browsing activity completely, so I changed it back to direct connection to internet and then everything worked again.... very strange. I'm not complaining, but I'd still like to know what the initial problem was. Oh well, perhaps it was just a bug.

---

### Post by kircher on 2006-08-07
alright, what the hell?? same problem again. I'm trying to resolve this issue, but if you have information for me it'd be muchly appreciated. Thankyou

---

### Post by kircher on 2006-08-07
well I've had to go back to windows because I need to be able to browse the internet. I wanted to use ubuntu, but an operating system (isolated to my particular installation, because noone here or by google search knows how to help, or seems to have experienced the problem) that by default doesn't allow firefox to load certain pages, without any form of support for my problem is not for me yet. I formatted 3 times, tried updating software, using automatix to update software, but no luck. Perhaps I'm just unlucky. I would like to use linux, but I would also like to be able to check my emails too. I'll try the next update of ubuntu, which I'm told is released in october.

---

### Post by calvinthomas on 2006-08-07
wow Kircher, I know it can be frustrating but you didn't give it much of a go looking at the time between your post and giving up and going back to windows, could it have been that the websites you were using were flash sites and flash wasn't set up properly or sites with video content and that wasn't set up properly? did you try a different web browser? Like Opera for instance or Swiftfox, were you using the 64bit version of Ubuntu or the 32bit?

Calv

---

### Post by kircher on 2006-08-07
I gave up because I needed to check my emails. I tried creating a dual boot (which I plan on still doing). I have found no real solution to this problem. I have no idea how to properly use linux (I installed it for the first time 2 days ago). Firefox doesn't have any documentation and I believe that through searching this problem in the forums, there is one other case of this happening (which happened 2 years ago), and that thread was never resolved either. I just don't understand why a fresh install would have problems loading pages using SSL. I am still going to use linux one way or another, because I promised myself xp is the last windows OS I ever use, and now with vista around the corner I do think it's time I use linux... but I am lost with this problem. I tried using epiphany browser, and it had the same problem (I know it's firefox underneath), so this tells me it must be an underlying problem with my ubuntu installation, but as I said, I am new to this, and I needed to check my emails, so windows seemed the easiest way to do that

---

### Post by kircher on 2006-08-07
I am using the correct install of ubuntu yes, the 32-bit version, and I updated flash with automatix. Gmail is not a flash website though anyway. I have not tried opera yet. Right now my priority is a dual boot though.

---

### Post by calvinthomas on 2006-08-07
Ah right I see, I'm a noob aswell, I started using Ubuntu on the 24th July! Evolution Email Client or Thunderbird will allow you to set up almost any email address within it so you can check your email, if you don't do this already i'd recommend doing it even in windows, especially if you have more than one email account or have a hotmail account (I hate the hotmail interface and i'm not convinced by the windows live one, although the live desktop mail beta seems to be quite decent!).

It can be frustrating when things don't work, I had problems with one application in particular (Maple 9.5) and a resolution took a few days but there is now a resolution out there. I dual boot Kubuntu & Windows, Windows for entertainment and Kubuntu for work type applications. Dual booting if you install windows first (or already have it installed) is straight forward (or at least it was the two times I did it)

Calv

---

### Post by kircher on 2006-08-07
Ultimately I want to get rid of windows for good. Use linux for everything.

---

### Post by kircher on 2006-08-07
ok, just did a bit more research and it turns out that secure sites won't work if your date is wrong (I'm fairly sure I set my date right, but I'll check that later) and if port 443 is not enabled. I doubt my router is blocking that port because this computer works fine with firefox in windows xp (and so do the other computers in this household). How do you check which ports are being blocked in ubuntu? I do not use a firewall, because my router has one. Also, how would I set up a static ip in ubuntu if I wanted to do that?

---

