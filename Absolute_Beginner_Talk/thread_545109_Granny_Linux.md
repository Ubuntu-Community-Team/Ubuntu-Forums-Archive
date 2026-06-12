---
title: "Granny Linux?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-09-07
Me and my mum are thinking about getting gran a computer + broadband for Christmas.  She's absolutely computer illiterate, as in never used a mouse.  We think she'd love messing around on the Internet if she just knew what it was.  

The question is, and only in theory there's no need to tell me how, would it be possible to configure Ubuntu to do the following: 

1)  On boot up start Firefox straight away.  That's all it does.  No password no nothing, just Firefox.

2)  ALL other options inaccessible without a password.  No way she can mess anything up.  It's locked down. 

3)  Updates are handled automatically, there's no pop up icon in the corner that asks her whether she wants them or not.  They just happen.  

4)  Be able to incrementally unlock different options/programs as she gets the hang of it (if she wants to).

5)  This computer starts Firefox, gets on the Internet (via cable, I know how much hassle with wireless... ), and that's it.  Nothing else.  A one-use machine. 

6)  All this being able to be done by a Linux newbie (me), preferably with typing as little as possible into CL. 

Thanks. 

I'm right in thinking this is impossible with XP, right?

---

### Post by rich.bradshaw on 2007-09-07
Probably can do it with Windows - try SteadyState...

Easier with Ubuntu no doubt though, as there is no risk of viruses/spyware.

---

### Post by BrendanM on 2007-09-07
All of these things are probably possible. #6 is going to be the sticking point, because doing these things will probably require writing some scripts to automate things. People here can help you, though. It sounds like an interesting project.

1) Pretty easy, just a shell script to start FF.
2) You could probably just remove all the other programs from the menus. There's no way your grandma is going to start hacking in the terminal.
3) I'm sure this is possible, but I'm not sure you'd want it. If Firefox works fine, and you don't want anything else running, why run the risk that an update might cause a glitch/unexpected behavior?
4) Do you want HER to be able to unlock features, or do YOU want to unlock them for her?
5) Assuming your network hardware is supported, it should be fine.

You might also check out this off-the-shelf solution called [Zonbu]("http://gizmodo.com/gadgets/exclusive-hands_on/22-things-to-know-about-the-99-zonbu-linux-pc-262952.php"). When I read about it, it sounded like a great granny PC.

---

### Post by stalker145 on 2007-09-07
aberadam,

> 1)  On boot up start Firefox straight away.  That's all it does.  No password no nothing, just Firefox.

In the Login Screen settings (System ~> Administration ~> Login Screen) you can set Ubuntu to log in automatically either with a timed wait or immediately... no password needed - just choose the user to log in. For starting FF, I believe you would just put firefox-bin into the Sessions settings (also under Administration, I believe) using the Startup tab.

> 2)  ALL other options inaccessible without a password.  No way she can mess anything up.  It's locked down. 

Also under Administration you will find Users and Groups. Using this, you can, in general, lock anyone out from making system-wide changes.

> 3)  Updates are handled automatically, there's no pop up icon in the corner that asks her whether she wants them or not.  They just happen.  

Though I've never tried this and, as mentioned it's probably not advisable, it is possible, I believe. Check under Synaptic (Administration menu) and find the Repositories settings in the menus. Toward the middle you should find a setting for automatic updates, auto download but not update, or manual. As for the notification... dunno. It will probably just pop up if a restart is required.

> 4)  Be able to incrementally unlock different options/programs as she gets the hang of it (if she wants to).

This is a bit more complicated. You'll have to do some research on this one as I'm not really sure how it's done.

> 5)  This computer starts Firefox, gets on the Internet (via cable, I know how much hassle with wireless... ), and that's it.  Nothing else.  A one-use machine. 

See #1. Also, you should be able to find some Kiosk software within the repositories. This will aid in making your machine more single-purpose.

> 6)  All this being able to be done by a Linux newbie (me), preferably with typing as little as possible into CL. 

You might need to delve into the CLI a bit. Don't worry too much about it. Mostly, things can be done by copy-and-paste, so it should be *relatively* simple.

Check back if you have any other questions.

---

### Post by aberadam on 2007-09-07
rich.bradshaw, 

SteadyState reverts back at boot up, I don't want her to get confused if she starts clicking on stuff.  

Yeah, good point about the virus/spyware/malware thing.  One big thing not to worry about. 


BrendanM, 

Thanks a lot, no real need to have it updating at all, true, just remove stuff from the menu!  Easy, I can do that. 

Preferably I want to be able to unlock features so as to be able to introduce them to her in a simple way.  Using OpenOffice may be easy but if you've got no concept of what a word processor is... She's most likely just to want to mess about on the Internet. 

I checked Zonbu and it's only available in the US, there must be something similar available in the UK though.

---

### Post by aberadam on 2007-09-07
stalker, 

Thanks, come to think of it as long as she can't click on it then she can't mess things up/get confused, so simply removing the options from the screen will do.  Password protection is overkill.  I'm sure there's a way to disable any keyboard shortcuts to features that may be set at default as well. 


Glad to know it shouldn't be a problem! 

Just gotta find her a nice neat little computer now.

---

### Post by philinux on 2007-09-07
Just been reading Linux Format mag.

eSys ePC Basic. £140 inc vat.

[www.esysglobal.co.uk](www.esysglobal.co.uk)

Verdict features 6/10
Performance 7/10
Ease of use 5/10 [edit] the ease of use thing is just that when you boot up you get ubuntu log in. Not great for first timers thats all.
Value for money 10/10

Overall 8/10 you get a keyboard and mouse.

It comes preloaded with ubuntu !!

---

### Post by aberadam on 2007-09-07
The link doesn't work!  :)

Will probably just go for the cheapest Dell box.

---

### Post by Shin_Gouki2501 on 2007-09-07
apparently i thought about a similar szenario.
3) and 4) , however i considerd to solve via remote login from me using free NX. Which means : now and then i login to do updates.
also when she wants i unlock for her the "system-configs".

---

### Post by carloslosgrande on 2007-09-07
[FONT="Comic Sans MS"]Hi. I have a friend who is basically computer illiterate.

I thought I was until I started helping him.

I setup Feisty for him and told him what not to touch. I setup a couple of folders, some themes, a few basic apps like amarok, vlc, etc.
Other than that I didn't really change anything. He doesn't have any real problems. Sometimes he drags the panels around by accident. Or opens 15 firefoxes.

He's very happy with it.

I would say (heading, myself, toward advanced years), that your Granny can probably learn to handle it fairly well without getting into the nuts and bolts.
Especially good to be able to play around with non-essential stuff, like themes and such.

If she hasn't been infected with windows thinking she'll probably catch on quite well.

Worth a try?[/FONT]

---

### Post by philinux on 2007-09-07
> **aberadam said:**
> The link doesn't work!  :)

Will probably just go for the cheapest Dell box.

Yeah it looks like their uk site got problem.

I did read somewhere that they give 3 year warranties on there desktops. Not sure if that would apply to the basic model.

Interesting in linux format they say they are going to compare it to Dell's preinstalled machine in a forthcoming issue.

---

### Post by aberadam on 2007-09-07
Shin_Gouki, 

Brilliant!  Remote control would be ideal because I live hundreds of miles from her (and maybe thousands next year).  Sort out any problems she has and keep Firefox up to date. I'll look into it. 

carloslosgrande, 

Glad it worked out for him.  My gran's 85 and as far as I know never used a computer, but she could turn out to be the next Linus Torvalds who knows! :)

---

### Post by BrendanM on 2007-09-07
For a remote control solution you should check out VNC. There's also the option of just using SSH, which is easier on bandwidth/faster, but that's really once you're more comfortable with the command line.

---

### Post by aberadam on 2007-09-07
Is there no remote control option with a GUI, one where I can say open a window and it's the other computer's desktop?

What about XP remote control?  Is there anything simple for it?

I know it's a bit off topic, but the more I think about it remote control could be very useful.

---

### Post by BrendanM on 2007-09-07
Sorry, you misunderstood me. VNC is a GUI remote control very much like Windows Remote Desktop. It works great. VNC is also cross-platform, so you could even remote control your grandma's computer from your Windows computer.

SSH is a comand line solution. I was just saying that SSH would be faster if you had a lousy connection.

[http://en.wikipedia.org/wiki/VNC](http://en.wikipedia.org/wiki/VNC)

---

### Post by zach12 on 2007-09-07
>  Sometimes he drags the panels around by accident.  my mom does that all the time

---

### Post by aberadam on 2007-09-07
Great thanks, I hate touching the command line, and if it's multi-platform that's even better.

---

### Post by aberadam on 2007-09-07
She'd be on broadband, I'd be on broadband, there'd be no hurry, so I don't think speed matters.

---

### Post by Daz1969 on 2007-09-07
How about this one:

[http://www.ebuyer.com/UK/product/128595](http://www.ebuyer.com/UK/product/128595)

I bought a similar one with Ubuntu (Dapper) pre-installed.
Bargain!

---

### Post by rich.bradshaw on 2007-09-07
VNC is even built in to Ubuntu...

---

### Post by skirkpatrick on 2007-09-07
To be honest, I wouldn't configure it to have updates installed automatically.  There's been too many times in  the last year where a premature update broke X-Windows for everybody who updated as soon as it hit the repositories.  If everything is working, she shouldn't need updates very often and it would be better to doe them for her whenever you visit or remotely through VNC.

---

### Post by erfahren on 2007-09-07
you might want to go with AbiWord instead of OpenOffice to start off. It's more basic.

---

### Post by Shin_Gouki2501 on 2007-09-07
@aberadam
IMO
u should still use free nx!it uses MCUH less bandwidth and IMO easy to install!
If u need  soem setup instructions i can tell u , its quite simple :)

---

### Post by crjackson on 2007-09-07
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi. I have a friend who is basically computer illiterate.

I thought I was until I started helping him.

I setup Feisty for him and told him what not to touch. I setup a couple of folders, some themes, a few basic apps like amarok, vlc, etc.
Other than that I didn't really change anything. He doesn't have any real problems. Sometimes he drags the panels around by accident. Or opens 15 firefoxes.

He's very happy with it.

I would say (heading, myself, toward advanced years), that your Granny can probably learn to handle it fairly well without getting into the nuts and bolts.
Especially good to be able to play around with non-essential stuff, like themes and such.

If she hasn't been infected with windows thinking she'll probably catch on quite well.

Worth a try?[/FONT]

[SIZE="3"][FONT="Comic Sans MS"]I'm with you on this too.  Since she isn't already used to using a computer in a particular way, it should be no trouble.  She will just be using the installed software most likely. Things you set her up with.  There's no reason to think she needs special childproof locks to keep her safe.  Give her a chance, she might just make you feel silly.  Some of us old folks actually do rather well.[/FONT][/SIZE]

---

### Post by vanden12 on 2007-09-07
I think the best thing will be get a PC then remove the HDD from it.....THen download a [olpc live cd]("http://wiki.laptop.org/go/LiveCd")Lock the cd dive and set it for auto boot it the best Os for old people....

---

### Post by BrendanM on 2007-09-07
Eww. I tried an OLPC VMware image a few months ago and it was lousy. Slow, glitchy, counterintuitive. I think the plan to give his grandma a web terminal and then ease her into other features is a good one. Also, I second AbiWord over OO.

---

### Post by vanden12 on 2007-09-08
It ran on on my Pc....

---

