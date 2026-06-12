---
title: "Looking at movie over the internet with firefox?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-13
Hello i was looking at an webpage and their i can look at small clips not youtube but close to that ... but firefox couldnt open it or i couldnt look at it .. its a movie clip maybe 5mb big ... and then i also want to know if there is an program to linux for stramin video over the internet like winamp  ?

---

### Post by meng on 2006-09-13
What do you have installed already? I have mplayer and the firefox plugin for it:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by atrus123 on 2006-09-13
Hello,

Have you tried installing Mplayer, Mplayer Plugin, flash, and the w32codecs?

[This thread](http://www.ubuntuforums.org/showthread.php?t=117163&highlight=mplayerplug-in+w32codecs) has a lot of useful information on this topic.  I recommend checking out the links to the ubuntu wiki.

---

### Post by pravuil on 2006-09-13
Are you using a 64 bit processor? Otherwise, the other posts would fix your dilemma.

---

### Post by oedipuss on 2006-09-13
Try installing totem-mozilla through synaptic, or with the command : 
sudo aptitude install totem-mozilla

Also, for flash videos, you'll need flashplugin-nonfree, same method.

Or alternatively, you could use Automatix (search the forums, the how to will be the first thing you'll find ), which is a script that'll install everything you'll need with no / minimum fuss :)

---

### Post by Kilz on 2006-09-13
> **pravuil said:**
> Are you using a 64 bit processor? Otherwise, the other posts would fix your dilemma.

Even if they are using thew 64bit version the applications listed above will fix it. Its just they have to be installed slightly different. A lot of 64bit users follow my howto for that.

---

### Post by haxer on 2006-09-13
I dont know guys i have installed all of that but i cant do it :S

---

### Post by haxer on 2006-09-13
Ok now its working fine thanks ;)

---

### Post by haxer on 2006-09-13
Hmm.. looks like i had wrong again wont work f... i hate this things mplayer start up but all i hear is sound no video :S and a program to streaming video over the internet like winamp please i need it :)

---

### Post by haxer on 2006-09-13
the file seems to be an .wmv file or something like that could that be the problem? and a streaming video program

---

### Post by jolan_jj on 2006-09-13
Have you tried to install other apps to watch streaming media? In my case it helped to install gxine and codecs. Then I just switch to gxine in firefox with help of mediaplayerconnectivity plugin.

---

### Post by haxer on 2006-09-13
How do i do that?

---

### Post by haxer on 2006-09-13
Please help me :(

---

### Post by jolan_jj on 2006-09-13
Open terminal and type ```
sudo apt-get install gxine
```.
Then go to [https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/) and install the plugin. Restart firefox and go to Tools->MediaPlayerConnectivity->Configure. You can start a wizard that mekes it for you, or configure it manually...
J.

---

### Post by haxer on 2006-09-13
Thank you so much :)

---

### Post by haxer on 2006-09-13
Hmm.. all i need now is the damn codecs :) how to?

---

### Post by haxer on 2006-09-13
and Gxine seems to not work :S

---

### Post by xyz on 2006-09-13
As meng posted on page one:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
All the posts show or point you to what you need.

Could you just gimme a linky here so I could check if it works? Thanks.

---

### Post by haxer on 2006-09-13
it worked all i was in the need of doing was to install w32 codecs with 

wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

  

And now it works fine thank you all in this post really helpful to a newbie like me ;)=D> =D>

---

### Post by xyz on 2006-09-13
> **haxer said:**
> it worked all i was in the need of doing was to install w32 codecs with 

wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

  

And now it works fine thank you all in this post really helpful to a newbie like me ;)=D> =D>
> Could you just gimme a linky here so I could check if it works? Thanks.
Could you just post one of the links that didn't work? I'm interested. Thanks again.

---

### Post by haxer on 2006-09-13
hmm.. not sure what you mean with links that didnt work maybe becouse my english is bab :S the one i meantioned work perfectly fine and the plugin to firefox to really nice

---

### Post by xyz on 2006-09-13
No problem! Your first post:
> Hello i was looking at an webpage and their i can look at small clips not youtube but close to that ... but firefox couldnt open it or i couldnt look at it .. its a movie clip maybe 5mb big ... and then i also want to know if there is an program to linux for stramin video over the internet like winamp ?

What is the [http://.....site](http://.....site) you could not see small clips, movie clip 5mb?
I hope it is clearer now. Thx.

---

### Post by haxer on 2006-09-13
haha.. hmm.. ok the sites name is [www.bseller.com](www.bseller.com) are you swedish?

---

### Post by xyz on 2006-09-13
> **haxer said:**
> haha.. hmm.. ok the sites name is [www.bseller.com](www.bseller.com) are you swedish?
lol...:D  and no need to be Swedish!!!;) 
I'm not Swedish, just a mutt!

---

