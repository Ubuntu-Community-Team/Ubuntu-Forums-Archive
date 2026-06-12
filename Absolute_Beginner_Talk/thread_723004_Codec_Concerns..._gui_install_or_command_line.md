---
title: "Codec Concerns... gui install or command line?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by jprophet420 on 2008-03-13
Hi. I'm not a nub to linux but this is my first ubuntu install and i've never run any form of debain that wasnt live. My ultimate goal is to get gaming but for starters i want to get my multimedia up and running. I had previously run fedora 7 on a 1ghz intel box and i had it playing all forms of media smoothly. the only thing i ddint have working was stage 6 divx plugins on the web.

I upgraded to this machine (amd sempron 3600+) and I tried Fedora8 x64 and it was my least favorite distro ever. I have been hearing a lot about ubuntu and had used the live version before once or twice. Anyway to make a short story long I had a lot of trouble getting anything to work that had to do with multimedia. Flash was bunked and i could not get any codec libraries installed.

So I installed this here ubuntu 7.10 i386. I was able to get flash working immeadiately with the tarball on adobes site in firefox, opera took some work. Found the answer here to that dilema tho, thanks already.

So flash and java are out of the way already and when I tried to play an mp3 totem ( I think it was totem) autodownloaded the codec with a few prompts. Im listening to a shoutcast right now.

All i want now is to be able to play .mpegs, .avis and all the popular spinoofs, i.e.divx, xvid etc. And finally i would like to be able to play dvd's.

Now, in earlier installs of fedora i was able to google this information and load up a few rpms and all it was all gravy. However with Fedora 8 the dependencies did not resolve properly and I had much trouble. Nothing would install beyond livna. I had posted on another forum and I was lead to believe that it was better to use yum from the command line than to install a precompiled rpm from the web (googled).

So what I want to know is what is the best way to reach my end goal? My favorite players are mplayer and xmms. Should I get the codecs and software i want from the command line only or doesent it matter? Can someone point me in the right direction? Thanks in advance.

---

### Post by hhhhhx on 2008-03-13
ubuntu restricted extras, in repo's,

---

### Post by oedha on 2008-03-13
> **xhhux said:**
> ubuntu restricted extras, in repo's,

open terminal
type :==> sudo apt-get install ubuntu-restricted-extras
:)

---

### Post by jprophet420 on 2008-03-13
Thanks a grip!
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install xmms
sudo apt-get install mplayer

got everything working well. The only problem is when i skip a chapter on a dvd i get...
> Error! gnome_screensaver_control()

otherwise it works great. I'm going to switch desktops soon so well see if that goes away. I havent tried it on any especially devious codecs yet but as soon as i either get my windows drive mounted (havent tried mounting/reading ntfs yet) or get som other media on here ill give that a whirl.

XMMS seems to jive rather nicely with ubuntu, i will try amarok if i have any issues but so far so good.

So i take it apt-get is the prefered method in ubuntu?

---

### Post by Oldsoldier2003 on 2008-03-13
> **jprophet420 said:**
> Thanks a grip!
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install xmms
sudo apt-get install mplayer

got everything working well. The only problem is when i skip a chapter on a dvd i get...


otherwise it works great. I'm going to switch desktops soon so well see if that goes away. I havent tried it on any especially devious codecs yet but as soon as i either get my windows drive mounted (havent tried mounting/reading ntfs yet) or get som other media on here ill give that a whirl.

XMMS seems to jive rather nicely with ubuntu, i will try amarok if i have any issues but so far so good.

So i take it apt-get is the prefered method in ubuntu?

apt-get is the easiest one to explain on the forums ("paste this in a terminal"), and as long as you know what packages you are looking for its way faster than loading synaptic.

---

### Post by forrestcupp on 2008-03-13
Personally, I usually use Synaptic, the GUI, unless I already know the exact name of the package I need or if I'm copying something in the forums.

About the mpg and avi thing, I think you could have automatically installed the codecs just by trying to double click on a file, just like you did with mp3's.  You still need to install the right packages to get DVD's working, but it looks like you took care of that.

---

### Post by oldos2er on 2008-03-13
> **jprophet420 said:**
> 
So i take it apt-get is the prefered method in ubuntu?

 Or aptitude.

 Amarok is of course a very good audio program, but if you're using Gnome, give Exaile a try.

 Also, you may need to install libdvdcss2 if you want to watch commercial DVDs. It's in the Medibuntu repository: [https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28medibuntu%29)

---

