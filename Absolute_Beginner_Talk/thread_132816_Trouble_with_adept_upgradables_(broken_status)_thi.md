---
title: "Trouble with adept upgradables (broken status) this is going to be long, sorry."
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by 56Kmodem on 2006-02-19
Hi, this is a second posting attempt. I probably already forgot some of the sequence of events from my original post  but here goes.

I am very confused. I was using Adept for the first time to check for upgrades and have run into many unknowns.  First off, is there a help manual for adept? When I click on the help manager handbook I get nothing - I guess it's not installed - just keeps trying to open then times out. I would love a tutorial that is extensive and detailed - truly step-by-step - it would save a lot of questions here. I found the kde help on installing packages but it was more like an overview and didn't explain things well. It tells you how to install but nothing about if it doesn't work right.

The problems: When I went to "fetch upgrades" in Adept, it fetched 23 upgradables, downloading them with 2 errors and 1 [COLOR="Sienna"]broken[/COLOR].  I went to "preview changes" and was trying to figure out what a broken application is and somehow 'remove' showed up on most of my kde applications. Luckily I didn't hit the 'commit changes' button. It took a lot of searching before I found the correction in the "Installing packages" help to remove the "remove" by hitting the "install package "button. That was what I was hitting when I was first trying to upgrade the downloads and it kept switching between keep and install  - I think, it's been hours now since it happened .  I still have adept open because I do not want to loose the downloads which took literally hours to download with dial-up. 

Right now the bottom line in adept says "changes: 0 install, upgrade 6, remove 0, 6 upgradable.  In the application lines is has "status - upgradable, action -upgrade. What happened to the other 17 upgradable downloads? And what is a "broken - installed application". The "broken" is KDElibs4c2.  Each time I try to upgrade the "upgradables" I seem to go in circles, except of course, for the "remove" scare. 

I should tell you that I have Kubuntu Breezy 5.10 and have never installed a Linux ANYTHING on my computer. In fact I recently changed from windows to linux and VERY recently was changed from debian kde sarge to debian kde kubuntu. I've also managed to screw things up in synaptic manager before the kubuntu switch, trying to upgrade and wiping out my desktop for a week, couldn't even go online - but I won't get into that here.

Anyway, I would just like to upgrade the 23 apps without destroying any in the process. Is there online help manuals for kubuntu (to maybe even download) so I won't become a pest here? It's all new to me - linux, firefox, thunderbird, kde, debian, kubuntu, gnome etc. I don't know what works what yet - they are all intertwined somehow, or so it seems. I'm learning baptism by fire and being constantly frustrated, manely because I can't seem to find that much easy-to-understand, common problems help. 

I hope this make some kind of sense. Sorry for the long post.

Thanks.

---

### Post by claydoh on 2006-02-19
oops didn't read that very well
 
ignore me

---

### Post by nalmeth on 2006-02-19
Like I mentioned before, try the terminal route. If you have broken packages/dependencies, then the command to use is:

sudo apt-get -f install

for regular update then upgrade

sudo apt-get update
sudo apt-get upgrade _or_ sudo apt-get dist-upgrade

I don't know what is wrong with adept, and I never use it so I can't tell you much about that... synaptic is good indeed. to install in terminal:

sudo apt-get install synaptic
sudo synaptic

Judging by your experiences with the front-ends, i'd suggest sticking with the terminal so you can see how it all works. The frontends are just pictures with buttons you push that spit out these commands.

EDIT:
> so I won't become a pest here?
Asking for help is what forums are for. People that find you to be a pest can ignore you, and if not, you can ignore them

Here is a guide I found from asiyu, might help, might not --> page 22 APT and adept
[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

