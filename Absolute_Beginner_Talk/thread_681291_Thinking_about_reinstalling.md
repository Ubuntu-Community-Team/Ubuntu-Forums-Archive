---
title: "Thinking about reinstalling"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by JBrehm on 2008-01-28
I've had ubuntu feisty since august of '07 and overall i love it. But, I keep having problems such as dvds not playing, ubuntu not recognizing my creative zen touch even being connected to the computer, much less being able to synch with my library, not being able to play certain videos online, and seeming to have some kind of problem with the repositories to which i've yet to find an answer to on here when I ask for help.

I'm thinking that if I save all of my info and reinstall ubuntu feisty that things will start working again. Thoughts?

---

### Post by pieisgood4589 on 2008-01-28
Unless you were installing/uninstalling software or/and changing system files, then re-installing won't help one bit. Try gOS- thinkgos.com- It's Ubuntu but with E17, not GNOME, and runs faster, looks better, and crashes less. :popcorn:

---

### Post by drowner on 2008-01-28
I find the e17 desktop very buggy still - although it is very lightweight and pretty.

Why do you think this will solve problems with the recognition of devices?

---

### Post by JBrehm on 2008-01-28
Perhaps because I'm still thinking as if I'm a windows user :roll:

I think I have put on a lot of crap that I don't need and that may be interfering with each other and making it so stuff simply won't work. I simply want to be able to have what ought to be working to work. 

Would it be beneficial to perhaps upgrade (via a clean install, not through update manager) to 7.10? I've heard some positive remarks on it. If not, does anyone know where I should look to figure out what's wrong with my repositories, why I can't watch DVDs, and why I can't get ubuntu to recognize my mp3 player?

---

### Post by drowner on 2008-01-28
oh - that wasn't directed at you, sorry!

I'm not particularly good at solving these issues (but I can help a bit) - i don't think installing an entirely new desktop will make a difference, and I agree that reinstalling may not be the best thing.

We should tackle the issues one at a time.... (although I may not be much help!).

Whats the problem with your repositories? Show me the link?

What happens with your mp3 player? Is it ever recognised?

Can you play any DVDs at all?

---

### Post by nowshining on 2008-01-28
since ur reinstallling u might as well install Gutsy - if u want try out Kubuntu :)

i think u'll like it. :)

what exactly are the error messages u are having 

totem has a problem as to u can't from the menu select play dvd, :( but if u have dvd to autostart it will work and play.

Did u install all the codecs like libdvdcss?

Do u use wine?

---

### Post by drowner on 2008-01-28
I really think we should stop recommending the installation of new desktops, and just focus on the issues at hand.

---

### Post by frigaut on 2008-01-28
Gutsy definitely is more polished than feisty, and gets better hardware recognition, better stability, etc.. If you re-installed, you should definitely install gutsy, not feisty. But likely, you will get similar, or other issues. As said above, you should try to attack the problems you have. Unless you really messed up your config, re-installing will not be of great help and will involve some work.

some DVD not playing? yes, it happens to me also, once in a while (one out of 10 or 20?).

problems with repos: this should definitely not happen. What kind of problems? If you haven't messed up your config, the package manager should be stable (it is for me).

certain video online: what plugin are you using. the mozilla-vlc or mozilla-mplayer should help you there (on top of flash of course).

---

### Post by seventhc on 2008-01-28
> **JBrehm said:**
> Perhaps because I'm still thinking as if I'm a windows user :roll:

I think I have put on a lot of crap that I don't need and that may be interfering with each other and making it so stuff simply won't work. I simply want to be able to have what ought to be working to work. 

Would it be beneficial to perhaps upgrade (via a clean install, not through update manager) to 7.10? I've heard some positive remarks on it. If not, does anyone know where I should look to figure out what's wrong with my repositories, why I can't watch DVDs, and why I can't get ubuntu to recognize my mp3 player?
I had mine set up to watch dvd's before, different computer. I will try to remember what I installed to make that work. It wasn't anything difficult, it's just a matter of having the correct program. I can picture it in my head, but i can't think of the name. I'll try to remember and post back.
I have an ipod and that works with a few different apps, I use gtkpod but you didn't say what mp3 you have.
this isn't what I did originally, but look at it.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)
you can search "dvd" in the forums, or 'dvd player ubuntu' in google to get some ideas.

---

### Post by seventhc on 2008-01-28
After following the steps from the link above, I just played a DVD using xine, but I couldn't play an older DVD. I'm not sure if thats a region setting ot not but that can be set by
```
sudo regionset
```

---

### Post by JBrehm on 2008-01-28
Ok, here's a list of the repositories (at least, I think this is the list y'all need in order to figure out if anything is wrong?)

[[IMG]http://img253.imageshack.us/img253/5567/screenshotsoftwaresourcqx1.th.png[/IMG]](http://img253.imageshack.us/my.php?image=screenshotsoftwaresourcqx1.png)

As for the mp3 player, it used to be recognized and would sync with no problems at all. But all of a sudden it just wouldn't get recognized, I have no idea why. Perhaps it's due to something I installed. I don't know. 

As for the movies... I just tried it out again, and gxine will come up automatically if everything works right and will go straight to the dvd menu and will play fine. But that's only for some dvds, not all. Sometimes the disc is recognized but then I get a message like this when I try to watch it via totem:

[[IMG]http://img166.imageshack.us/img166/1452/screenshottotemzr7.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshottotemzr7.png)

Ok, edit... the movies i've tried to watch all seem to work on gxine, which is fine with me, but I'd like to be able to use totem and vlc to watch them too. 

Is there a way to make sure I've downloaded all of the correct codecs and to make sure that there aren't some that are conflicting?

Also... not expecting much from this, but is it possible to download veoh TV and to be able to watch stage 6 divx videos online?

---

### Post by nowshining on 2008-01-29
are u using gutsy or feisty - i think i have the same list - if ur using gutsy change all feisty to gutsy and edgy to gutsy 

i don't think some will connect anyway 

as for the other

in synaptic

libdvdcss2

install that - and re-start the apps and try playing the dvd again.

---

