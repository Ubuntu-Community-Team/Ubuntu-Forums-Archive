---
title: "[SOLVED] Another thing I forget how to do with EVERY fresh install"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-22
With every install of ubuntu there are some things I forget to do, here is one
I downloaded compiz and everything, but I forget how to get this application, that lets you control the effects that you want, like the cube and stuff. anyone know what its called? 

also on an unrelated note, anyone know of some program from the repos that will give me a mac like dock?

---

### Post by jleaker01z on 2008-01-22
> **-gabe-noob- said:**
> ? 

also on an unrelated note, anyone know of some program from the repos that will give me a mac like dock?

gDesklets is simliar.

---

### Post by Paul820 on 2008-01-22
> I downloaded compiz and everything, but I forget how to get this application, that lets you control the effects that you want, like the cube and stuff. anyone know what its called?
**compizconfig-settings-manager**

---

### Post by A4006 on 2008-01-22
Search for "compiz" in Add/Remove Programs"

---

### Post by -gabe-noob- on 2008-01-22
I also mean somthing kinda like kiba dock-ish but in the repos if theres anything like that
Edit and thanks for the awnser

---

### Post by crjackson on 2008-01-22
> **-gabe-noob- said:**
> With every install of ubuntu there are some things I forget to do, here is one
I downloaded compiz and everything, but I forget how to get this application, that lets you control the effects that you want, like the cube and stuff. anyone know what its called? 

also on an unrelated note, anyone know of some program from the repos that will give me a mac like dock?


Compiz-Fusion is installed by default on Gutsy 7.10, you don't need to install it.  If you graphics card/driver support compositing (compiz) (you may need to enable a restriced driver or something), the first level of effects/animations should also be enabled by default (window fading and such).  This can be turned off/on going to system>preferences>appearence (or is that system>admin>appearence).

For more control over compiz you need to install compizconfig-settings-manager.  You can do this from the synaptic package manager.  After you install that you can control nearly every aspect of your compiz settings.

---

### Post by jleaker01z on 2008-01-22
> **-gabe-noob- said:**
> I also mean somthing kinda like kiba dock-ish but in the repos if theres anything like that
Edit and thanks for the awnser

Hmm its in my repositories.  You might need some repositories enabled.  Can you post your /etc/apt/sources.list?

---

### Post by -gabe-noob- on 2008-01-22
Oh I have gDesklets, but its not what I was looking for, I was thinkng of more of a dock/launcher type thing.

---

### Post by Paul820 on 2008-01-22
Avant window navigator? You can have a look at this to see if it's what you want [http://getdeb.net/search.php?keywords=avant]("http://getdeb.net/search.php?keywords=avant")

---

### Post by -gabe-noob- on 2008-01-22
Starter bar from Gdesklits is somthing like it, but I'm too stupid to know how to add apps to that

---

### Post by jleaker01z on 2008-01-22
I found a thing called kiba-dock.  Looks like what you are looking for [http://www.youtube.com/watch?v=BS4Z5VghfhE](http://www.youtube.com/watch?v=BS4Z5VghfhE)

---

### Post by -gabe-noob- on 2008-01-22
I searched up avant in the repos, but nothing came up for

Avant Window Navigator

---

### Post by jleaker01z on 2008-01-22
> **Paul820 said:**
> Avant window navigator? You can have a look at this to see if it's what you want [http://getdeb.net/search.php?keywords=avant]("http://getdeb.net/search.php?keywords=avant")

This one looks good...and its definiately easier to install then Kiba.  Try that.

---

### Post by -gabe-noob- on 2008-01-22
yea Kiba dock aint in repos hehe, and it takes a little work to get it working on 7.1

---

### Post by jleaker01z on 2008-01-22
Follow his link.  When you download it it is a .deb file.  Your computer will know what to do with it.  Open it with package manger and let it go.

---

### Post by -gabe-noob- on 2008-01-22
Oh didnt see you could DL from there, thanks, and nice site!

---

### Post by Paul820 on 2008-01-22
> **-gabe-noob- said:**
> Oh didnt see you could DL from there, thanks, and nice site!

Yes, the only way to get awn is by getdeb or building from source or adding the awn repos to your source.list. The .deb is the easiest.

---

### Post by -gabe-noob- on 2008-01-22
Sure is

---

### Post by -gabe-noob- on 2008-01-22
I know this is really stupid but I cant figeur out how to use avant


like how to launch it and stuff

thanks for your help


I'm an idiot

---

### Post by p_quarles on 2008-01-22
Glad this got resolved. Just wanted to throw in my 2 cents: one thing I've found enormously useful is to use a notetaking application (e.g., Tomboy, Basket Notes) to document what I've done after reinstalling. The note archive can easily be saved to a flash drive and reloaded after the initial installation, with precise instructions for getting everything back to the way it was.

---

### Post by -gabe-noob- on 2008-01-22
Hmm still cant launch avant and thanks for the tip eyeball dude


I;m out for like an hour will post when back

---

### Post by Paul820 on 2008-01-22
Go to Applications->Accessories->Avant Window Navigator, all the preferences are available from System->Preferences->Awn Manager and to have it run when you boot-up, just make an entry for it in System->Preferences->Sessions, choose Add and then enter this:
Name: whatever you want
Command: avant-window-navigator

---

### Post by -gabe-noob- on 2008-01-22
How can I make avant launch programs? I go to add program to launcher but I cant navigate to my applications, and is there a way to make it turn on on startup? 

Thanks for all the help

Nvm got the startup part :D but how about adding apps?

I added pidgin by typing in pidgin but other aps is a no go, the launchers not showing

---

