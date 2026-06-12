---
title: "gDesklets"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-20
I installed gDesklets via synaptic.  I am very new to linux and ubuntu and don't know anything about commands.  I went to applications > accessories > gDesklets, but the only thing that opens is a blank window called a gDesklet shell.  Ultimately, I want to install a dock on the bottom of my screen.  What haven't I done or what have I done wrong?  I don't have a good graphics card.  Ubuntu doesn't even let me enable desktop effects.  This is why I stayed away from programs like AWN.

---

### Post by billgoldberg on 2008-03-20
> **hikujk123 said:**
> I installed gDesklets via synaptic.  I am very new to linux and ubuntu and don't know anything about commands.  I went to applications > accessories > gDesklets, but the only thing that opens is a blank window called a gDesklet shell.  Ultimately, I want to install a dock on the bottom of my screen.  What haven't I done or what have I done wrong?  I don't have a good graphics card.  Ubuntu doesn't even let me enable desktop effects.  This is why I stayed away from programs like AWN.

If you want a dock, don't use gdesklets.

You want/need awn.

Follow instructions here.

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

If you want a curved dock:

Look here:

[http://linuxowns.wordpress.com/2007/12/07/curved-awn-dock/](http://linuxowns.wordpress.com/2007/12/07/curved-awn-dock/)

[B]You will need to use the command line.

You don't have to know anything about it, it's just copy/paste work.

(the terminal is located at: "applications -> accessories")[/B]

Why don't you give it a try, and post here if the copy/past thing should work.

---

### Post by hikujk123 on 2008-03-20
I am okay with a plain dock if I can use gDesklets.

I try what you said though. :)

---

### Post by billgoldberg on 2008-03-20
> **hikujk123 said:**
> I am okay with a plain dock if I can use gDesklets.

I try what you said though. :)

I've tried gdeklets before, it tends to crash, doesn't look very well, and is buggy.

I don't even think it's being developed anymore.

Could be wrong about that.

---

### Post by billgoldberg on 2008-03-20
I forgot to mention that will need compiz fusion running, or else you can't run awn.

The commands giving in the link are pretty easy to follow, but i'll try to simplify them even more:

Go to "applications -> accessories -> terminal".

Copy past this line:

```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list
```

If a password is asked, type it, you won't be able to see what you type or how many keys you already entered.

Then copy/past this:

```
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list
```

Press enter.

After that is finished copy/paste this:

```
sudo apt-get update
```

If you are asked to install anything, press "y" and then press enter.

Now copy past this:

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

It's installed.

You can now start it by going to "applications -> accessories -> avant windows navigator".

If you want awn to start when you boot up the pc:

Go to "system -> preferences -> sessions".

Press "add".

Enter these lines:

- AWN
- avant-window-navigator
- dock

---

### Post by hikujk123 on 2008-03-20
When I type:
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

I get:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by hikujk123 on 2008-03-20
Maybe I should just stick with gDesklets, even if it's buggy.
I mean if it is easier to use.

---

### Post by billgoldberg on 2008-03-20
> **hikujk123 said:**
> When I type:
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

I get:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This is because "synaptic package manager" or "add/remove" is open, close it and copy/paste the command again.

---

### Post by jeffhollon on 2008-03-20
what about kiba-dock?????

---

### Post by hikujk123 on 2008-03-20
Okay.  I'll give it another try.

---

### Post by billgoldberg on 2008-03-20
> **hikujk123 said:**
> Okay.  I'll give it another try.

You only need to enter the last two commands this time.

---

### Post by stchman on 2008-03-20
gDeskltes has an OS X style dock feature that can be placed anywhere on the screen.  It animates when you mouse over and jumps up and down when you select an application.

With that and the Mac4Lin you can really make your Gnome look like OS X if you want.

---

### Post by billgoldberg on 2008-03-20
> **stchman said:**
> gDeskltes has an OS X style dock feature that can be placed anywhere on the screen.  It animates when you mouse over and jumps up and down when you select an application.

With that and the Mac4Lin you can really make your Gnome look like OS X if you want.

The mac4lin package also has awn skins.

---

### Post by hikujk123 on 2008-03-20
> **billgoldberg said:**
> 

Go to "system -> preferences -> sessions".

Press "add".

Enter these lines:

- AWN
- avant-window-navigator
- dock

Thanks for the help.  I had synaptic open.  I have it installed.  I don't understand the above directions.  When I click add, I can type under name, command, and comment.

---

### Post by hikujk123 on 2008-03-20
I don't want ubuntu to look like OS X (or windows).  I am happy to be free to customize my desktop how I choose.  I just like the concept of a dock.

---

### Post by hikujk123 on 2008-03-20
When I open it, a blank window shows up, and then it disappears.:confused:

Edit:  I realized I was opening the wrong thing.  Still need help with  

Originally Posted by billgoldberg  View Post

Go to "system -> preferences -> sessions".

Press "add".

Enter these lines:

- AWN
- avant-window-navigator
- dock

---

### Post by hikujk123 on 2008-03-20
Awn has an option that you can just check to have it start at login.  However, i am still having a problem.  When I click something to activate it, it says it is activated but nothing shows up.

---

### Post by hikujk123 on 2008-03-20
bump

---

### Post by BLTicklemonster on 2008-03-20
I've messed with Awn a few times, and prefer gdesklets for ease of use except for one thing. How can I get the starterbar I like to load automatically and keep the launch items I chose. I want to do this in icewm. Anybody got any ideas?

---

### Post by hikujk123 on 2008-03-24
Nothing seems to work on my computer.  I just made a decent looking dock by editing my 2nd panel.  I like it a lot.:guitar:

---

### Post by karlo on 2008-03-24
What is **gDesklets**?

---

