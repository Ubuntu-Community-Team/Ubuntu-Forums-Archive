---
title: "what happens when you update to feisty fawn?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-17
i'm planning on upgrading to feisty fawn the minute it comes out, but what will happen when i do?  when i've upgraded windows machines in the past, it erased everything and i had to re-install all my programs.  does that happen in ubuntu?  and if not, what happens instead?

---

### Post by insane_alien on 2007-04-17
well, if you do an online upgrade(not a fresh install from a CD) you'll have everything the way you left it along with all the extras that come along with feisty. you may have some slight problems(unlikely but we'll help you fix them if you get some) and everything will be shiny.

if you have a seperate /home partition then you'll still have all your files but it will be the equivalent of a fresh install.

if you want to do a fresh install(no /home partition) then you'll need to back up your data. 

personally, i would just upgrade through the upgrade manager. its never gone wrong for me.

you could even upgrade just now. feisty is rocksolid (apart from a little burp the other day for people with binary drivers). i'm on feisty and loving it.

---

### Post by Chappy7777 on 2007-04-17
Alien, Are you saying that I can put my 6.10 CD in the CDROM and install it on top of 6.06? Upon loading the CD does it ask if this is to be a clean install or and upgrade, or something to that effect? It sure would be nice to not have to wipe my HDD clean (reformat) before installing a newer version. Are you saying I can do that? And if so, will my dialup modem still be detected, ready to connect, and Firefox up to 1.5.0.11 ?

Thnx,
Chappy

---

### Post by Happy_Man on 2007-04-17
No, what he means is that if you do an upgrade by using the upgrade manager to download and install feisty, it would be like you have feisty, but all your stuff is still there.

---

### Post by Sef on 2007-04-17
If you do an upgrade, be sure to have a install disk handy and back up your data first.   They often go well, but sometimes they do cause mess up, and a clean install is needed.

---

### Post by Quillz on 2007-04-17
What version are you going to be updating from? If it's 6.06, you'll probably want to do a fresh install, but if it's 6.10, then ```
sudo apt-get dist-upgrade
``` should work.

---

### Post by locke.dragon on 2007-04-17
i'm not positive which i'm using.  let me get this straight.  i can just use the download manager once feisty comes out, it'll give me hundreds of upgrades like it did the first time i upgraded after installing the version i had on cd, and i'll still have all my files?

and can i just upgrade now, get the beta version, use it 'til thursday, and then get the stable one?

---

### Post by Ender Black on 2007-04-17
Lock. in a word...Yep.

I upgraded via apt-get to test Feisty and I had everything I had before but running on 7.04 instead of 6.10.  You won't notice a whole lot of wow that's different unless you are using a laptop then hopefully like me you will notice that the webcam works out of the box and Nvidia drivers are super easy.  Oh and of course the network-manager just rocks!  But other than that is reliable ol' brown ubuntu.

---

### Post by locke.dragon on 2007-04-17
sweet!  and it's locke.  l-o-c-k-e.  with a k.  :P  just messing with you.  is your name like ender from ender's game?  i love that book!

---

### Post by locke.dragon on 2007-04-17
ok.  problem...  uh...  here...  take a look.

```

link@Ubuntu:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
link@Ubuntu:~$ 

```

that's what i get when i try to upgrade using apt-get.  is there any way to tell which version i'm using currently?  i remember attempting something along these lines a while back, but i wasn't sure if it worked or not.

---

### Post by kpkeerthi on 2007-04-17
You should upgrade like [this]("http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html")

More info [here]("https://help.ubuntu.com/community/FeistyUpgrades")

---

### Post by caffienefree on 2007-04-17
cat /etc/lsb-release

---

### Post by locke.dragon on 2007-04-17
ok.  it's working on upgrading.  but how long should it take?  it says it's gonna take something like 14 hours!

---

### Post by j_dog on 2007-04-17
Yeah, I just tried that and got the same result .:neutral:

---

### Post by locke.dragon on 2007-04-17
try the link in the post above.  it's working for me.  it's just gonna take a few hours to download the updates.

---

### Post by j_dog on 2007-04-17
Oh.....here we go.....this works !       

Thanks !\\:D/

---

### Post by Chappy7777 on 2007-04-17
That does me no good since I have no way to download the thing. Why can't/don't the "Distro Dudes" put whatever is to be done w/the download manager on a CD, and let it be installed from there instead of downloaded. I know that the whole distro will be available for free on CD or DVD, but I'm talking about just what one would have to download being placed on a CD to be mailed to folks like me who are not able to do a huge (at 49.6Kbps) download. 

Thanx for the reply,
Chappy

---

### Post by igknighted on 2007-04-17
> **Chappy7777 said:**
> That does me no good since I have no way to download the thing. Why can't/don't the "Distro Dudes" put whatever is to be done w/the download manager on a CD, and let it be installed from there instead of downloaded. I know that the whole distro will be available for free on CD or DVD, but I'm talking about just what one would have to download being placed on a CD to be mailed to folks like me who are not able to do a huge (at 49.6Kbps) download. 

Thanx for the reply,
Chappy

You can do that.  If you download the alternate CD you can add it to synaptic as a repo, then dist-upgrde.  If you have anything else installed that isn't on the default though, it could break.  Again, there are repo CD/DVDs available that have some of the other stuff, but I don't know where, you might have to explore for that.  The reason an upgrade option isn't on the CD is likely due partly to what I just mentioned, and partially because the Ubuntu installer sacrifices a lot of functionality in order to (a) include more software on the disk and (b) be as unconfusing to new users as possible.

---

