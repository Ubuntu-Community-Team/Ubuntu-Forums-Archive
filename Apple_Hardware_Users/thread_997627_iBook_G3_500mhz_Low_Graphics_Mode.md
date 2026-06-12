---
title: "iBook G3 500mhz Low Graphics Mode"
date: 2008-11-30
forum: Apple Hardware Users
---

### Post by kritstov on 2008-11-30
Hey,

I've been searching on Google for a long time now and maybe I'm looking right over the solution but I finally gave in and decided to make a thread. So I finally got xubuntu installed on my ibook (G3 500mhz dual USB) and I figured out that it kinda works if I boot with "video=ofonly" but when I boot it goes into low graphics mode and I can barely read anything. I've managed to mess around with xorg.conf file but that didn't seem to help (I made a backup, but I'm not totally sure how to revert back to it). I have a feeling this is some sort of driver issue. Oh yea and I don't know if this is related or not but when I go into the desktop whenever I open something (terminal, firefox, etc) it immediately closes or just never comes up. Any help would be greatly appreciated. =D

---

### Post by lemonbar on 2008-12-01
I'm having this problem too - nothing works in low graphics mode for me.  Any ideas out there?  If I magically get my xorg to work (using Intrepid), will I still have problems opening apps?

---

### Post by kritstov on 2008-12-02
Don't wanna be that guy but I'm afraid if I don't bump this it will get lost.

---

### Post by stream303 on 2008-12-02
> **kritstov said:**
> it kinda works if I boot with "video=ofonly" but when I boot it goes into low graphics mode and I can barely read anything.

You may want to try installing with Dapper 6.06x "alternate", with the idea of upgrading later to 8.04.  This way, you might gain some good xorg.conf config data that you can use with 8.04 should it not come up.

---

### Post by kritstov on 2008-12-03
> **stream303 said:**
> You may want to try installing with Dapper 6.06x "alternate", with the idea of upgrading later to 8.04.  This way, you might gain some good xorg.conf config data that you can use with 8.04 should it not come up.

I installed Dapper without any problems. Is there any reason to upgrade to 8.04? All I want to use this computer for is web browsing, programming, and word processing.

---

### Post by kritstov on 2008-12-04
Also, I've heard that there isn't flash for powerpc linux. But I've heard about this thing called gnash? Will I be able to use it to watch Hulu, or YouTube?

---

### Post by milkwood on 2008-12-05
I'm sure you can upgrade to Hardy safely,except one thing you have to define xorg.conf after upgrade(but I think it's very simple and easy).
But maybe you are not able to watch Youtube on Firefox.
I know how to watch Youtube without Flash on Firefox.
But still It's very doubtful if you content in that way.
It must be very slow...and there must be an advertisement on videos all the way!

---

### Post by milkwood on 2008-12-05
Sorry,you can watch youtube movies on firefox without flash player.
I've just confirmed right now.
You should just install greasemonkey and its script.
But watch out!I have not checked all files.
You should check files by yourself or other ways.
And you don't have to upgrade to hardy.
You try this in your current environment.
Good luck):P!

---

### Post by milkwood on 2008-12-05
> **lemonbar said:**
> I'm having this problem too - nothing works in low graphics mode for me.  Any ideas out there?  If I magically get my xorg to work (using Intrepid), will I still have problems opening apps?

Hi,lemonbar!

I heard things doesn't get well on g3 intrepid.
Why not you back up current your files as long as you can,and get back to the old version.
It must be very painful,but I recommend to do that.
Please take care;).

---

### Post by rjcalifornia on 2008-12-06
Hey Bumper guy! How much RAM do you have in your ibook g3? Have you considered Kubuntu or Ubuntu??

GNASH does not work for ibook G3, don't even try it, you'll be in facing a lot of issues when you use firefox.

I download my favorite youtube videos and watch them on Xine, it's not the best option but it works smoothly.

What version of xubuntu are u using?

---

### Post by kritstov on 2008-12-06
> **milkwood said:**
> Sorry,you can watch youtube movies on firefox without flash player.
I've just confirmed right now.
You should just install greasemonkey and its script.
But watch out!I have not checked all files.
You should check files by yourself or other ways.
And you don't have to upgrade to hardy.
You try this in your current environment.
Good luck):P!

Thanks for the help! I managed to get greasemonkey and the mplayer script for youtube. The only problem now is I've having trouble getting mplayer. I've tried different tutorials and always one thing or another has gone wrong. There is either a missing package or it just fails. Is it because I'm running dapper that I'm running into these issues?

---

### Post by milkwood on 2008-12-07
Sorry,I don't remember that Totem on Dapper can play .flv files.
If it can,try "Free Youtube!(userscripts)" using totem as mozilla plugin.
I'm using it on hardy and it's totally working!
I have youtube plugin on totem which is a bit choppy but "Free Youtube!" is very fine.
No!I've remembered Totem couldn't play .flv files!
And mplayer,can you play any .flv files with your installed mplayer?
I also don't remember that I can use mplayer as mozilla plugin.
But I think I could play .flv files with mplayer.
If you can't play any files with mplayer,you should try to change options,
for example,output drivers "xv" and "oss",or,"xv" and "esd" and so on.
It worked for me before.
And I've also remembered that only mplayer could play .flv on my Dapper.
Xine did not play each sound.
I think you should try "Free Youtube!" and mplayer-mozilla-plugin.
If it doesn't work,you should download files by using some methods or upgrade to hardy.
Take care.

I think smilies is very annoying.
I will not use it unless I need it. 

milkwood.

---

### Post by milkwood on 2008-12-11
I'm so sorry.
I've tried several scripts.
But what I can use is just mtube(not enough though).
Free youtube! can't be used unless you define it defaulted application.
But I don't know how to.
I'm so sorry.

---

### Post by rjcalifornia on 2008-12-11
Quick Question: are you guys talking about watching youtube videos on Firefox under Linux on Mac PowerPC???

---

### Post by kritstov on 2008-12-11
> **milkwood said:**
> Sorry,I don't remember that Totem on Dapper can play .flv files.
If it can,try "Free Youtube!(userscripts)" using totem as mozilla plugin.
I'm using it on hardy and it's totally working!
I have youtube plugin on totem which is a bit choppy but "Free Youtube!" is very fine.
No!I've remembered Totem couldn't play .flv files!
And mplayer,can you play any .flv files with your installed mplayer?
I also don't remember that I can use mplayer as mozilla plugin.
But I think I could play .flv files with mplayer.
If you can't play any files with mplayer,you should try to change options,
for example,output drivers "xv" and "oss",or,"xv" and "esd" and so on.
It worked for me before.
And I've also remembered that only mplayer could play .flv on my Dapper.
Xine did not play each sound.
I think you should try "Free Youtube!" and mplayer-mozilla-plugin.
If it doesn't work,you should download files by using some methods or upgrade to hardy.
Take care.

I think smilies is very annoying.
I will not use it unless I need it. 

milkwood.

That's ok, I think I'll just use it for programming. Thanks for all the help! I appreciate it.

---

