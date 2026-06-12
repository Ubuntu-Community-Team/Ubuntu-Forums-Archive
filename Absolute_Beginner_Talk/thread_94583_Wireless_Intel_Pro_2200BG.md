---
title: "Wireless Intel Pro 2200BG"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by ninocass on 2005-11-24
Hi all

Im a total Linux virgin here and am having some problems with my wireless card.

I have searched the forum and found a linux driver for the Intel Pro 2200BG card i have downloaded it and tried to install it as per the readme file bundled with the files.  But ive hit a problem, i cant even get the first step of the installtion done:
"unpack the source code" - % tar xzvf ipw2200-1.0.0.tgz"

i get

bash: fg: %: nosuch job

Thanks for any help

Nino

---

### Post by odin on 2005-11-24
are following this howto? 

[http://ubuntuforums.org/showthread.php?t=26623&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=26623&page=1&pp=10)

It's really good(thank's Luca again).For the tar thing I would say is the right way to do  it....

---

### Post by ninocass on 2005-11-24
im working through it and im getting as far as

```

cd ..
cd ieee80211-1.0.3
make
sudo make install

```
i get the error when i try to "make"

saying that old references to iee80211 are found, ive tried the sh remove-old but its not working

---

### Post by danne on 2005-11-24
[QUOTE=ninocass]im working through it and im getting as far as

```

cd ..
cd ieee80211-1.0.3
make
sudo make install

```
i get the error when i try to "make"

saying that old references to iee80211 are found, ive tried the sh remove-old but its not working[/QUOTE]
why don't you try it with ndisgtk?
you only need the .inf file of the windows drivers....nice and graphically :cool:

---

### Post by ninocass on 2005-11-24
ill give ndisgtk a go, its gonna be another long night lol

---

### Post by danne on 2005-11-24
[QUOTE=ninocass]ill give ndisgtk a go, its gonna be another long night lol[/QUOTE]

no it'll be over in 2 minutes....
just acces it in the menu (windows wireless drivers)
put the .inf and .sys file from the windows drivers in a map(you'll have to leave the files where they are so put them somewhere they don't nag you) 
and then just load them in with ndisgtk
now you only have to configure your network to choose the connection and activate it.....your done!

bye!

---

### Post by ninocass on 2005-11-24
i just tried a tut on ntiswrapper and my wireless card has done a runner i dont think i used the correct drivers, i feel the ipw2200 drivers are the best method

i cant delete stuff from my lib folder as it says i dont own it any ideas?

---

### Post by danne on 2005-11-24
[QUOTE=ninocass]i just tried a tut on ntiswrapper and my wireless card has done a runner i dont think i used the correct drivers, i feel the ipw2200 drivers are the best method

i cant delete stuff from my lib folder as it says i dont own it any ideas?[/QUOTE]

remember to use "sudo" before you enter a command in the terminal....it provides you with root capabilities

btw..ndisgtk didn't work?

---

### Post by ninocass on 2005-11-24
no i think ive done something to my "/etc/network/interfaces" file thats not allowing the wireless card to show up :(

---

### Post by danne on 2005-11-24
[QUOTE=ninocass]no i think ive done something to my "/etc/network/interfaces" file thats not allowing the wireless card to show up :([/QUOTE]

hmm that's a bummer...I don't have that much experience myself to start messing in those files :rolleyes: 
but try removing the tools etc. you've used to configure your card and try again from scratch (my way:cool: ;) ) ...or you could ask it to someone with a little but more knowledge:rolleyes:

---

### Post by ninocass on 2005-11-24
and now i have a GCC error

```

gcc-3.4: command not found

```

---

### Post by ninocass on 2005-11-24
i think ive messed my interfaces file up does anyone have the default one?

also how do i install the GCC thing?

---

### Post by ninocass on 2005-11-24
anyone?

---

### Post by odin on 2005-11-25
Now I remember that when I did it I had a problem with gcc.It didnt work compiling with gcc4.0.Try installing gcc3.4 and do it again.

---

### Post by Dafydd on 2005-11-25
Hi Nino,

I'm a complete beginner too. 

But why do you need to pack/unpack and install etc? I could never work through such instructions...

I have a Sony Vaio with ... a Wireless Intel Pro 2200BG. Ubuntu worked out of the box with my wireless.

I assume it must be the network configuration you have to do...

Sorry, I'm an absolute beginner but maybe someone here can help out.

Generally I've found the wireless on my Vaio (with Wireless Intel Pro 2200BG) works with Ubuntu (5.04, 5.10), Knoppix 3, PcLinuxOs, Aurox 10.

Fedora 4 did not work straight out of the box, so I had to drop that.

Best
David

---

### Post by ninocass on 2005-11-25
i got the problem solved :D after 3 days of tryin!!!!

it turns out on my dell bios the internet is turned off until the unser activates it via keyboard.  all i did was turn it to always on and its working a treat :D

---

### Post by soonindallas on 2005-11-25
glad you got it working.

---

### Post by zoryn on 2005-12-01
well, im using an acer aspire 1694WLMi, and i seem to have exactly the same problem, except i have no bios option to 'always enable the wlan', and even if i keep pressing the button to enable it while booting, it doesnt work..

---

