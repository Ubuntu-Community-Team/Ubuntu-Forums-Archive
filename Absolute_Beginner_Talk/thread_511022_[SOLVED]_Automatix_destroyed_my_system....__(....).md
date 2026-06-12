---
title: "[SOLVED] Automatix destroyed my system....  (....)"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-07-27
I just wanted to hear the 3gp files... 

I went to aoutomatix2.... Install codecs....

Now...
Everything sounds twice!!!!!!!!!!!!!!!!!!!!!!!!!

When I open any file, (mp3 for example) It starts playing really loud... (after a second starts a new sample of the same mp3 a bit less loud)  Then... after some seconds the first loud one stops and the second continue playing...

Wired, strange ugly.....!!

I installed, reinstalled, deleted all gstreamer and xine codecs...  Nothing works...

I don't want to format my system guys...   

Do I have some chance to fix this?????    

Help!!!!!!!  :-(

---

### Post by deadgobby on 2007-07-27
Automatix is a 3rd party software and ubie has no control over of any one installing Automatix. OK with that said. Do you use a on board sound card or a pci card. Like sound blaster for example? Are you using one media player at a time? What media player is the double looping accuring? Are you uising just ALSA or OSS. Have you check your ALSA settings? 
Gobby

---

### Post by Kosimo on 2007-07-27
> **deadgobby said:**
> Automatix is a 3rd party software and ubie has no control over of any one installing Automatix. OK with that said. Do you use a on board sound card or a pci card. Like sound blaster for example? Are you using one media player at a time? What media player is the double looping accuring? Are you uising just ALSA or OSS. Have you check your ALSA settings? 
Gobby

I'm using the onboard soundcard on my HP Laptop. Is a realtek.

This sound issue happens with any player, Rythmbox, Audacious MPlayer... 

I'm a quite new user in Linux, so, I don't know about ALSA... Sorry... Can I may write some command in console to find this information?   

About Automatix... I know is a 3d party software and I shouldn't use it... I always discourage the use even to my friends... But yesterday I really had to listen some 3GP file and I couldn't do it... So, I wanted to risk with automatix..... And no luck....  

I'll never never use Automatix again....

But now, I still have this problem and I really can't reinstall my system now...

Thank you in advance.

---

### Post by Kosimo on 2007-07-27
By the way... Audacious is configured to play using ALSA 1.3.2 and it have this problem.

Hope this may help.

---

### Post by Kosimo on 2007-07-27
More information:

Device settings:
Intel 82801DB-ICH4

---

### Post by Majorix on 2007-07-27
Is what you hear possibly just a preview?

---

### Post by Kosimo on 2007-07-27
> **Majorix said:**
> Is what you hear possibly just a preview?

I don't think so..

Because it happens with all audio players and It didn't happen before this issue...
Sounds really loud (about 3/4 seconds)...

---

### Post by Majorix on 2007-07-27
Still it sounds like a preview. Because preview does happen with all audio players and takes like 3-4 secs. You can look at
Edit > Preferences > Preview tab and see if you have preview open for audio files. It can't hurt :)

---

### Post by deadgobby on 2007-07-27
Automatix did not kill your system. You have a realtek sound card and if it has a intell chip set in. It is a known bug with it. Enter this in the termial and lets start debugging that sound card of yours. Please post back on the what the reply back on the command

lspci -v 

 and this too

lspnp -v

---

### Post by Foxmike on 2007-07-27
> **Kosimo said:**
> I'm using the onboard soundcard on my HP Laptop. Is a realtek.
 
This sound issue happens with any player, Rythmbox, Audacious MPlayer... 
 
I'm a quite new user in Linux, so, I don't know about ALSA... Sorry... Can I may write some command in console to find this information? 
 
About Automatix... I know is a 3d party software and I shouldn't use it... I always discourage the use even to my friends... But yesterday I really had to listen some 3GP file and I couldn't do it... So, I wanted to risk with automatix..... And no luck.... 
 
I'll never never use Automatix again....
 
But now, I still have this problem and I really can't reinstall my system now...
 
Thank you in advance.
It is not more a question that you shouldn't use it than if you use it, the support is a lot harder to provide when something breacks.
 
Maybe you should go and request support on the Automatix forums?  I know they encourage people getting support for their products there.

---

### Post by Kosimo on 2007-07-27
> **Majorix said:**
> Still it sounds like a preview. Because preview does happen with all audio players and takes like 3-4 secs. You can look at
Edit > Preferences > Preview tab and see if you have preview open for audio files. It can't hurt :)

Amazing!!! :-)

Is the preview!! You where 100% right!! :-)  I didn't realize but when I put my mouse just above some file it starts playing....   But this didn't happen before installing this codecs!   

Now everything is ok again :-)

Çok tesekkur ederim   !!!!

---

### Post by Kosimo on 2007-07-27
Thank you to everyone guys.

Problem is fixed.  

How can I change the title of this topic to add the (SOLVED) line?

---

### Post by Majorix on 2007-07-27
Hehe "rica ederim" (no problem)! Glad you got it working :)

---

### Post by deadgobby on 2007-07-27
When you reply to your post, just put solved on the tittle bar. Simple eh!

---

### Post by irish_flu on 2007-07-27
> **Kosimo said:**
> Thank you to everyone guys.

Problem is fixed.  

How can I change the title of this topic to add the (SOLVED) line?


If you edit your first post, you'll be able to mark the thread "resolved" (there's a checkbox, IIRC).

Congratulations on getting the problem solved!

---

### Post by Kosimo on 2007-07-27
Trying to mark it solved

---

### Post by Kosimo on 2007-07-27
Sorry for my ignorance guys...
But if I change the title it changes only the single post title, not the main title.
And I can't find the checkbox.... 

I will have to open a new post asking how to resolve a resolved post :P

---

### Post by richbarna on 2007-07-27
> **Kosimo said:**
> Trying to mark it solved

Molt be, m'agrada molt.

Fins ara ;)

---

### Post by Majorix on 2007-07-27
You can go to the first post and then click advanced while editing. There you can change the title of the whole THREAD. Well that was at least how I did it a few days ago.

---

### Post by Kosimo on 2007-07-27
> **richbarna said:**
> Molt be, m'agrada molt.

Fins ara ;)

A mi també ;)

Fins aviat!

---

### Post by Seisen on 2007-07-27
Go up to thread tools and click on mark as solved.

---

### Post by Kosimo on 2007-07-27
> **Seisen said:**
> Go up to thread tools and click on mark as solved.

;) Done

---

