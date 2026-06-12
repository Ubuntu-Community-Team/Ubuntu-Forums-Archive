---
title: "exceedingly stupid n00b help needed...."
date: 2005-01-10
forum: Apple PPC Users
---

### Post by redneckr1 on 2005-01-10
Hi ive just installed warty (ubuntu) on my tray loading imac ive got a few niggles which i was reccomended to come here to ask (seeing as its the place to go)

firstly how the hell do i get mplayer to play my mp3's. apparently theres a few packages which i need to mess about with. how the heck do i get this to work. also on this i would like to use the standard cd ripper as well to extract mp3's. (as im a musician it would be helpful if i could send my work to people) 

secondly when i go into synaptic none of the packages are visable but the status of them are displayed in the "status bar" on the bottom of synaptic but i cant see any. i.e it says "813 are visable etc..." 

i hate being lost, im usually quite good with setting stuff up, its my first linux install. be kind. 

Thanks for your Time

Red

---

### Post by kleeman on 2005-01-10
On the mplayer issue search around the ubuntu site a bit there are tons of howtos for mulitmedia.

On the ripping issue, use grip (sudo apt-get install grip) and also install lame to encode
mp3s (sudo apt-get install lame).

The synaptic issue sounds wierd try hitting the reload button...

---

### Post by redneckr1 on 2005-01-10
i have many times.

ive also looked around the ubuntu webby and i havent the foggiest what to do. 
ill again and ill try your advice, what else do i need to grab as ive got two gstreamer.debs which i think are needed. gstreamer-lame0.8 etc....

eek. what a mess.


also my apple keyboard wont work properly, the space bar is knackered. i think its not a hardware problem as well. damn thing

---

### Post by jdodson on 2005-01-10
[QUOTE=redneckr1]i have many times.

ive also looked around the ubuntu webby and i havent the foggiest what to do. 
ill again and ill try your advice, what else do i need to grab as ive got two gstreamer.debs which i think are needed. gstreamer-lame0.8 etc....

eek. what a mess.


also my apple keyboard wont work properly, the space bar is knackered. i think its not a hardware problem as well. damn thing[/QUOTE]

ok so what do you want to do?  i could not glean from your post what you are trying to accomplish.

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) is a good resource, you could check there, the help is great.

---

### Post by mistic on 2005-01-11
i have the same problem with the synaptics-packet-manager

i see teh status but not the packages itself....

luckily i prefer using the terminal for stuff like this anyways :-)


redneckr1 maybe this can help you out for a short while:

if you want to search for a program:

```
sudo apt-cache search nameOfPackage
```

this will give you a list of possibilities, then choose one and do

```
sudo apt-get install nameOfSelectedPackage
```

I know it might be a bit scary at first but its really not that hard this way, should you get too mutch results, you can use grep to filter through them like this ('I'll use 'java' as an example)
```

sudo apt-cache search java | grep x11
```

this makes sure that only the lines containing x11 are outputted, so the general command would be:

```
sudo apt-cache search Package | grep extraSearchWords
```

hope this can help you out a bit

---

### Post by redneckr1 on 2005-01-12
ok i tried a lot of stuff yesturday, i was away (college) and seeing as i need to connect my ixmac up to the internet i saw the biggest problem. however i have managed to grab the universe package from the webby so would i be able to edit the command to get the universe repository off my pendrive. wait i think i might be able to do it. 

ive also got a major probelem as well. my space bar wont work in terminal or open office. dammit. 


oh i wouldnt be asking if i didnt understand what the guide said really. thanks for the help ill report back

---

### Post by redneckr1 on 2005-01-13
didnt work. ive realised how stupid i sound. i cannot enable the universe repository. ho hum.

---

