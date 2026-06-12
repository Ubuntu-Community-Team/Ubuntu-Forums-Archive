---
title: "firefox youtube problem (can't find flash player)"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-09-30
The title is pretty much self explanatory. i get a message saying that i either have java scrpit disabled or i don't have the latest flah player installed. they give me a link to install the latest flash player, and i did...twice, with no luck.

---

### Post by easyease on 2006-09-30
check your other thread matie, hope it helps.

---

### Post by aysiu on 2006-09-30
The latest Flash player native to Ubuntu is Flash 7. YouTube might want Flash 9.

If you're not sure if you have even Flash 7, read this:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

If you are sure you have Flash 7 but want Flash 9, read this:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by easyease on 2006-09-30
actually i got my flash 7 working on youtube by just editing a file and cheating it, I'll look for the thread that showed me how to do it......

---

### Post by aysiu on 2006-09-30
> **easyease said:**
> actually i got my flash 7 working on youtube by just editing a file and cheating it, I'll look for the thread that showed me how to do it......
That thread is linked to in this HowTo:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Tobster on 2006-09-30
Java I got form Easy Ubuntu

go to the web page copy the code, paste it in the Terminal and press enter

WAIT UNTIL IT SAY SAVED

I think you press enter again... then it asks for your admin password, the one you use to log in (nothing will happen as you type but it is being inputted)

Type in your password, nothing will happen press enter

WAIT A MOMENT and Easy Ubuntu will come up install all the media codec you like.

**How to Install quick time**[

I found the easy way is to go to Sypathic Package Manager and down load Xine... It an amazing DVD player with Quick Time Codec installed in it which automaticly go onto your system.

**Flash**

With Flash I went to the flash web page (just type in Flash in google) web page download then open the files it say then type in the code that on the web page in the Terminal to install it and then closed  Fire Fox (or what ever brower your using) Press Y for Y to install and then N to not to re-install

To be honest I open all the downloaded files to get it to work because I could not work which one I should open so if you get stuck just open all of them then go to terminal and type in the code from the web page

---

### Post by easyease on 2006-09-30
aha here it is, to quote some chappy.....This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$


simple as that, its been working for me with no probs for a week or two.

---

### Post by raul_ on 2006-09-30
That didn't work either. i don't think that's the problem, because i watched videos on youtube perfectly until i removed my firefox directory and installed via apt-get...i didn't do nothing more

for those who aren't familiar with my other thread i'll explain:

i had firefox installed manually while i was using breezy, but since i upgraded to dapper and the version on the repositories was the same i had, i decided to remove my firefox directory and re-install firefox via apt-get to make things "cleaner". and since i did that, that error shows up :(

---

### Post by raul_ on 2006-10-01
oh well i got it...i just copied the plugin files to every mozilla or firefox directory in my computer and now it works...go figure =P thank u all for ur replies

---

### Post by podunk on 2006-10-01
I just wanted to say thank you to aysiu – you are the person that did the psychocats page, yes?

Your site has been very helpful several times!

Sorry for the off thread post.....

---

### Post by jesperw on 2006-10-06
> **raul_ said:**
> oh well i got it...i just copied the plugin files to every mozilla or firefox directory in my computer and now it works...go figure =P thank u all for ur replies

I have exactly the same problem, could you explain which file you copied where to get it to work?

---

### Post by raul_ on 2006-10-06
sure :)

so when u try to watch a video in youtube, it will give u a link to download the latest flash player installer right? It turns out that "installer " is just a fancy name, because everything it does is copy those 2 files that come with it to the folder u want. So first, i installed it in /usr/local/lib/firefox or something..i don't remember...but it didn't work...so i just copied those files to every folder that said Mozilla or firefox and had a "plugins" folder inside of it :p and it worked. Obviously this isn't very clean, but i just want to watch my videos

PS: of course that u have to copy the files to the Plugins folder

---

### Post by jesperw on 2006-10-10
Thanx. Got it to work now. :)
I now have libflashplayer.so in $HOME/.mozilla/plugins/  (nowhere else) which works great.

about:plugins in firefox reports "Shockwave Flash 7.0 r25", so there is no need to hack for flash 9.0 to get YouTube and Google video to work as sugested earlier in this thread.

---

### Post by kttrina on 2007-01-21
hi, i ' ve got some problems with youtube too and all swf applications..
i tried and read nearly  all the threads here about it, i installed and reinstalled it several times
following HOWTOs and also psychocat (it really helped me!)

but still nothing happens

 but i've discovered that in

 home/<mydirectory>/.mozilla/firefox/pluginreg.dat

there is

Shockwave Flash 9.0 **r31**

and not the release suggested in this 3d
--->should i change it? is this the error?


@ raul_ 
> .i just copied the plugin files to every mozilla or firefox directory in my computer and now it works
can you tell me what you did exactly?

i suppose you modified /usr/lib/firefox too but which plugin files did u copy?

thank u lots

---

### Post by kttrina on 2007-01-21
whoops sorry i didnt read the last messages of the thread...
i feel so sorry i will telll you if it works

---

### Post by Frank Golden on 2007-01-21
The latest version of Flash fixes the sound synch problem. With version 7 sound is very out of synch with video. Version 9 fixes that.

---

### Post by kttrina on 2007-01-21
i solved that error!!!:D 

it was not a macromedia flash player plugin problem with firefox (now i currently have version 9 on firefox 2.0):
i read about: plugins page again and again and discovered that the first plugin was a swf player with weird descripitons like "it will ride your motorbike and watch porns" related to this page:
[http://www.schleef.org/swfdec/]("http://www.schleef.org/swfdec/")

and it didn't work at all.

i hope it isn't some bad stuff, i think it's out to date because since 2005  it has't been updated :-\" 
i removed only the file 
```

$ cd usr/lib/mozilla/plugins
$ sudo  rm libswfdecmozilla.so 
```

so i've discovered that if u have several swf readers (e.g.  gnash)
 the first you read browsing in firefox's page
about: plugins

is the currently used plugin!!!

---

### Post by ricardovich on 2007-01-30
I screwed up youtube and firefox by going on a media player install rampage. I'm not sure which one uninstalled flashplugin-nonfree and installed flashplugin which I believe was the problem. Following [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) fixed it.

---

### Post by joN_jai on 2007-01-31
Im following the instruction here:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

And im on the step :
Quick Terminal Installation
wget -c [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb


So i have both of these files but when i enter:
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb

It shows this in my terminal:

sudo dpkg -i gsfont*.deb
(Reading database ... 88834 files and directories currently installed.)
Preparing to replace gsfonts-x11 0.17ubuntu4 (using gsfonts-x11_0.17ubuntu4_all.deb) ...
Unpacking replacement gsfonts-x11 ...
Setting up gsfonts-x11 (0.17ubuntu4) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory


sudo dpkg -i flash*.deb
dpkg: error processing flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb


Neeed help!

---

### Post by joN_jai on 2007-01-31
Here is a pic
[IMG]http://img.photobucket.com/albums/v396/jon_jai/Screenshot.png[/IMG]

---

