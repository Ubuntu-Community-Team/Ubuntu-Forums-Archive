---
title: "Game + VMWare"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by d0ct0r on 2007-08-04
I just got VMWare running on my windows box, so I have it running Ubuntu fiesty.. now, how would I go about setting up a game ( Diablo II + Expansion LoD ) on here.

there are 3 cds for regular game and an expansion CD.

---

### Post by Brunellus on 2007-08-04
what is "on here"?

---

### Post by d0ct0r on 2007-08-04
onto the virtual box.

---

### Post by adrianelliott on 2007-08-04
When you are running an operating system as a VMware guest, it does not have direct access to your PC's hardware.  VMware creates virtual devices representing your graphics cards, hard disks etc.

This is a problem for gamers. The virtual video card which vmware creates for you in your guest environment is not up to much - it is unlikely that any game which requires 3d hardware acceleration will run.   There is no way around this, although I do believe that the newest version of WMware workstation (costs money) is capable of limited direct x acceleration.

---

### Post by AndyCooll on 2007-08-04
You'll probably need to start by installing Wine. However playing games on a VirtualBox image isn't going to be pretty. The VirtualBox image doesn't use your graphics card, but a a bog standard "virtual" graphics card. Even if you assign the graphics card plenty of memory it will still struggle.

If you're going to try playing games on Ubuntu, you're probably best dual-booting.

There's a Diablo howto [here]("http://ubuntuforums.org/showthread.php?t=443821"). There are plenty of others, I just typed "diablo" and "howto" in the search box at the top.

:cool:

---

### Post by Acglaphotis on 2007-08-04
Dont! Wine runs Diablo perfectly! In my ubuntu box is even faster than in windows.

---

### Post by d0ct0r on 2007-08-04
no one gets it, i wan't to be able to use things that i can't get working in wine, so i want to use windows.. but at same time use diablo 2 on linux ( also so i can load up more then one.. ;o )

but what ever ;\

---

### Post by Brunellus on 2007-08-04
> **d0ct0r said:**
> no one gets it, i wan't to be able to use things that i can't get working in wine, so i want to use windows.. but at same time use diablo 2 on linux ( also so i can load up more then one.. ;o )

but what ever ;\
No, I don't get it.  What is it, exactly, that you are trying to accomplish here?

---

### Post by anewguy on 2007-08-04
Try posting some detailed answers to these questions, and we'll see if anyone can help:

(1) Is your PC booted to Linux or to Windows?

(2) The virtual machine you created and are running - is it Linux or Windows?

(3) You want to be able to run a Windows game in Linux, and that game doesn't run in WINE, correct?

If this is what you are attempting to do, and if there is no native Linux version of the game, then you will probably need to use a virtual machine WITHIN Linux to run Windows and therefore the game (if it will run - graphics aren't made for games yet in the virtual machine software I have tried).  I would seriously doubt you would have much luck booting Windows, running Linux in a virtual machine just so you could run a virtual machine (a virtual machine within a virtual machine) of Windows so you could run your game in "Linux".

You say you want 2 copies of the game running - apparently that means you can't have 2 running in Windows.  I would seriously doubt you can get 2 working with 1 in Windows and 1 in Linux (with Linux running in a virtual machine in Windows).

---

### Post by Linendail on 2007-08-08
> **d0ct0r said:**
> no one gets it, i wan't to be able to use things that i can't get working in wine, so i want to use windows.. but at same time use diablo 2 on linux ( also so i can load up more then one.. ;o )

but what ever ;\

Sorry for digging, but...

Let's not be stupid. As it is clear you only need this virtual machine for running a copy of the game that only works on Windows, why not just do that? Instead of making it all complicated and asking about it on a linux forum, why not just get a virtual machine for your original windows, running a WINDOWS VIRTUAL MACHINE instead of Ubuntu, for your 2nd copy of the game? Problem solved.

And if you ask me, doing that in Diablo - that's just lame.

---

### Post by gn2 on 2007-08-08
To put it in plain and simple terms, 3d games just don't work in virtual PC's.

3d support for virtual PC's is currently being worked on by VMWare, but it's a long way off yet.

---

### Post by Bohlio on 2007-08-20
So do 2D games work?

Im having problems getting Tiberian Sun to work in Virtualbox, all i get is a black screen... Is there a way to get old games like this to work easily or is *all *gaming in VM's still a long way off?

---

### Post by mysticmatrix on 2007-08-20
> **Bohlio said:**
> So do 2D games work?

Im having problems getting Tiberian Sun to work in Virtualbox, all i get is a black screen... Is there a way to get old games like this to work easily or is *all *gaming in VM's still a long way off?

Might not be answer to your question, but I was able to get Age of Empires 2 successfully running under VirtualBox.

---

### Post by AndyCooll on 2007-08-21
> **Bohlio said:**
> So do 2D games work?

Im having problems getting Tiberian Sun to work in Virtualbox, all i get is a black screen... Is there a way to get old games like this to work easily or is *all *gaming in VM's still a long way off?

It really depends on how much graphics power your game needs, the more graphics required the less likely the game will run properly.

:cool:

---

### Post by Mogurijin on 2007-08-21
Might I recommend d2 loader for running multiple diablo games? It would be much simpler and d2 loader works fine. Or is there something I'm missing here?

---

### Post by Bohlio on 2007-08-22
> **mysticmatrix said:**
> Might not be answer to your question, but I was able to get Age of Empires 2 successfully running under VirtualBox.


Good enough, AOE2 has probably close to the same graphics as Tiberian Sun, so it should work, I just need to figure out why it isnt... off to VirtualBox forums!!! :D

---

### Post by splintercellguy on 2007-08-22
Forget about gaming inside a VM, Wine is the best shot, or dual-booting XP.

---

### Post by Bohlio on 2007-08-22
I had crazy problems with Wine... detailed here... [http://ubuntuforums.org/showthread.php?t=530524](http://ubuntuforums.org/showthread.php?t=530524)
I suppose it is the intro video that is causing the problems... Can virtual XP's run videos? or is that to advanced?

---

### Post by rowdog on 2007-09-28
I've been running D2 in vmware for quite a while now. In fact, I'm just helping a friend set it up on his slackware box at this very moment. 

The problem he just ran into was that he needed to install the vmware tools before D2 would pass the video test.

So...

install vmware
install windows guest (XP here)
install vmware tools
install d2
install LOD

Yes, vmware doesn't support 3d but diablo 2 is really a 2d program. You won't be able to use the 3d mode but I don't miss it.

For those who think wine is fine, I agree, unless you want to do other things too. I often program while helping a friend mule not to mention using the web, irc, etc. For me, vmware is the way to handle diablo.

--rowdog

PS: Sorry for the necro post but I (hope) I have the solution.

---

### Post by Kilz on 2007-09-28
> **Mogurijin said:**
> Might I recommend d2 loader for running multiple diablo games? It would be much simpler and d2 loader works fine. Or is there something I'm missing here?

Have you been playing Diablo 2 long? If you havent you may want to [look up Warden]("http://www.trap17.com/index.php/diablo-2-anti-hack-stuff_t28397.html"). Its an anti cheat/hack/exploit software that was put into Diablo with version 1.10. Using any hack like loader can cost you your ability to play on battle.net if caught.

---

### Post by Kilz on 2007-09-28
> **rowdog said:**
> I've been running D2 in vmware for quite a while now. In fact, I'm just helping a friend set it up on his slackware box at this very moment. 

The problem he just ran into was that he needed to install the vmware tools before D2 would pass the video test.

So...

install vmware
install windows guest (XP here)
install vmware tools
install d2
install LOD

Yes, vmware doesn't support 3d but diablo 2 is really a 2d program. You won't be able to use the 3d mode but I don't miss it.

For those who think wine is fine, I agree, unless you want to do other things too. I often program while helping a friend mule not to mention using the web, irc, etc. For me, vmware is the way to handle diablo.

--rowdog

PS: Sorry for the necro post but I (hope) I have the solution.

Why install all that when wine runs D2 flawlessly? I used to use Cedega, but stoped paying and use wine now. wine even has 3d mode working since 9.39

---

### Post by rowdog on 2007-09-30
> **Kilz said:**
> Why install all that when wine runs D2 flawlessly? I used to use Cedega, but stoped paying and use wine now. wine even has 3d mode working since 9.39

I used wine for a number of years and I really have no major complaints about how it runs diablo beyond the occasional breakage associated with Gentoo. Well, except having to spin the CD all the time (vmware will use an ISO) and the font issues. Of course, the fonts could have been a Gentoo issue but maybe you'll test /fps some time and see what happens.

Really, the reasons I like running D2 in vmware is because I'm pretty hardcore about diablo. I can run both two copies at once and mule by myself without throwing things on then ground. I can also run all the MPQ extractors and etc associated with moding.

But really, the reason I posted was not that wine is bad, it's not, it's really good and the graphics are generally better, it was more the whole "vmware is hard and sucks, use wine" kneejerk response when in fact, vmware is a perfectly viable solution and it's rather trivial to accomplish assuming you have a fair set of computer skills.

I mean really, "install vmware tools before you install diablo" is no big deal if you've managed to install the broken vmware distro that comes with Ubuntu.

I'm sorry if this feels like a personal attack, I really don't mean it to be but these issues are near and dear to my heart.

--rowdog

---

### Post by MozartlovesUbun2 on 2007-09-30
[http://ubuntuforums.org/showthread.php?t=552088](http://ubuntuforums.org/showthread.php?t=552088)

---

