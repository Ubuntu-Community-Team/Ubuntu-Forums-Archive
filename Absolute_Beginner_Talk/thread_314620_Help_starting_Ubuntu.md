---
title: "Help starting Ubuntu"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by jdm bb6 on 2006-12-07
This doesnt make sense to me at all, i have tried the last few days in between finals and everything college like but i have still not been able to download a damn thing usiing ubuntu. I go to applications, then i go to add/remove, window pops up reading the list and uploading availible applications and i get a list fulled with goodies, i hit search and i put synaptic, how do i install it on to my desktop? I do know that synaptic allows me to upload many different applications but i guess i am very lost. i am sitting here with my laptop using XP and trying to figure out how to really use ubuntu thats installed as my main opterating system on my desktop. Can anyone walk me through this, i have done my homework not to mention have completed a research paper on this topic of outsourced OS's and also purchased the book, 'Ubuntu Hacks'... still not helping 

Thanks for looking guys,
Deric

---

### Post by igknighted on 2006-12-07
Synaptic is not for 'uploading', only downloading software from official repositories (so you know its not malicious) and installing it.  Basically you just click a software package, select 'mark for installation', and then click apply in the toolbar.  It does the rest.  Add/Remove programs is sometimes an easier place to start though, and it works in basically the same way.

Edit: Synaptic is already installed, its under System->Administration->Synaptic Package Manager.  If you are using KDE, Adept is roughly the same thing (in fact I like it better).  It's in K Menu -> System -> Adept I believe (dont have KDE in front of me at the moment)

---

### Post by nickburns on 2006-12-07
If the question is how to get to Synaptic:

System >> Administration >> Synaptic 

there you have hundreds of other choices of what packages you want to install.

---

### Post by jdm bb6 on 2006-12-07
alright, let me try

---

### Post by jdm bb6 on 2006-12-07
says i have problems to my system, and failed to upload..

i cannot copy and paste but i will put w/e i can:
[B]
W:Failed to fetch http:us.archive.ubuntu.com/ubuntu/pool/main/linux-kernal-headers/linux-kernal-headers_2.6.11.2[/B]


^^ is this because i did not hook it up to the internet, ha reading over it i think this is the proble, and if it is, i feel dumb

---

### Post by Daremo on 2006-12-07
You do need an active Internet connection for Synaptic or to access the repositories in general. Don't feel dumb, this is what learning is about...

---

### Post by nickburns on 2006-12-07
Yes you need to be hooked to the internet to get the package.

---

### Post by jdm bb6 on 2006-12-07
alright, internet connection setup via cat5 :)

hmm let me redo all them steps, thanks guys 

Deric

---

### Post by jdm bb6 on 2006-12-07
Alright, we have lift off, you guys rock, now what should i download. Should i just upload it all and get it over with and what i dont end up using i just un-install or is there a specific set of 'Goodies' i should upload as a startup launch?

Another thing, can someone tell me more about the bluetooth, can i sink this to my pda or something?

---

### Post by jdm bb6 on 2006-12-07
where would i place this command, i do not see a comand prompt

---

### Post by jdm bb6 on 2006-12-07
once installed where do they go?

---

### Post by lemonsCC on 2006-12-07
Congrats on getting syaptic working and welcome to thousands and thousands of free programs "on demand."

What exactly are you looking to do that Ubuntu can't do with the programs installed?  This will give us a better idea as to the packages you should be looking for.

---

### Post by lemonsCC on 2006-12-07
So many questions, take a breath....

Now most applications get installed in /usr/bin (please correct me if i am wrong here) but they should be added to your applications menu automatically.

Second there is no command line, you just check the package you want and click apply.

EDIT:
250 Beans!

If you want to install stuff from the command line...you:
[LIST=1]
[*]Need to know the exact package name
[*]Open Terminal via Applications Menu
[*]Enter this command ```
sudo aptitude install <name of package here>
```
[/LIST]

---

### Post by jdm bb6 on 2006-12-07
wow, this is fun hahaha 

your very sarcastic is a kick *** way lol, your pretty funny 

alright i opened up the terminal and i typed in exactly what you asked me to, instead i placed synaptic and it asked me for a password... 

instead of synaptic whats a good thing to open up? whats this thunderbird or mozilla fire fox email? how can i open that bad boy ?

Deric

---

### Post by jdm bb6 on 2006-12-07
also my font is way too big and its annoying the hell out of me, any special drivers i need to install or how would i go about changing this setting? 

Also, like in XP i can change the theme's whats that theme i read somewhere.. it started with an F like firecracker or something lol where i can change the whole theme of my ubuntu... theres many different ones out there but a popular one is the one i speak of, starts with an F though. Sorry if i am not too helpful and i know im doing an amazing job at whoring it up with my beginner posts :cool: :rolleyes: 

Deric

---

### Post by drr422 on 2006-12-07
you could consider getting automatix, that will make your initial experience a lot smoother since it will install more commonly used programs and flash, mp3, and dvd support.  you could check out the [unofficial ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") , this one is for EDGY 6.10, so if your not using edgy, you should google the dapper 6.06 one.  This guide will also tell you how to install automatix and most of the other programs that are commonly used.  I wouldn't recommend installing ALL of the available programs though, cause i think that would be sort of a waste of space.  
Have fun, i know i did :-)

---

### Post by pmasiar on 2006-12-07
> **drr422 said:**
> you could consider getting automatix, 

I just read on planet.ubuntu blogs, automatix screws ubuntu pretty bad and gurus advise *not* to use it. makes system less stable - inconsistent libraries.

You are really much better off reading up docs: [https://help.ubuntu.com/](https://help.ubuntu.com/). Search for flash or whatever  you need to install. Flash is here, it took me less than minute to find it: [https://help.ubuntu.com/community/FlashPlayerStandalone](https://help.ubuntu.com/community/FlashPlayerStandalone)

---

### Post by 3rdalbum on 2006-12-08
> **jdm bb6 said:**
> 
like in XP i can change the theme's whats that theme i read somewhere.. it started with an F like firecracker or something lol where i can change the whole theme of my ubuntu... theres many different ones out there but a popular one is the one i speak of, starts with an F though.
Deric

No idea which theme you're speaking of... but the website [www.gnome-look.org](www.gnome-look.org) has a massive array of themes. Just remember:

A GTK theme controls what tabs, buttons, scrollbars etc will look like.
A Metacity theme controls what your window headers and borders will look like.

When you've downloaded a theme, DON'T extract the archive. Go into System > Preferences > Theme, then Install Theme and show it where your theme archive file is.

---

### Post by xpod on 2006-12-08
> I just read on planet.ubuntu blogs, automatix screws ubuntu pretty bad and gurus advise *not* to use it. makes system less stable - inconsistent libraries.

Of course a "guru" will tell you not to use Automatix2 and that it`s much better to learn the "proper" ways to install stuff blah blah blah...Thats the nature of a lot of "guru`s" it seems..

Now if you ask most of the newcomers out there they will most likely tell you the same thing as me...

Automatix2 is great for getting yourself up and running with and theres all the time in the world to learn these "prioper" ways of doing things.
Just watching the trouble you were\are having with synaptic is more than enough reason to get AX in my opinion.

Especially now that it`s one click install.
You`ll probably find yourself re-installing and changing setups umpteen times in these first months,NOT always due to probs but simply because you`ll no doubt get the bug for it all and like many of us be trying all sorts of different methods at first.

By all means dont use AX but dont not use it because of what some "guru" spouted about it.....

Good luck regardless and remember....Ubuntu will take hold of your very existance..with or without AX:twisted:

---

