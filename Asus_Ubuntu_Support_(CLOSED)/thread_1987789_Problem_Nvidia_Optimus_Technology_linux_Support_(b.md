---
title: "Problem Nvidia Optimus Technology linux Support (bumblebee apps)"
date: 2012-05-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jao_madn on 2012-05-26
Hi,

I had a asus u30jc laptop with dual video NVIDIA OPTIMUS features (Built-in Intel and Nvidia geforce 310M), I just wondering if someone already figure out how the official nvidia driver works,  or any tweaks inorder to use the nvidia card, Ive been using this laptop for more than a year now, and i cant figure out or find a tutorials that work  (when i try installed any nvidia driver it render a black screen when boot-up, no success in xorg tweaks)..Correct me if im wrong, Basically if no nvidia driver installed on my laptop then my system will resort to use the nouveau driver right, so my question would be,"1.) what video card(Intel or Nvidia) is the system using? 2.) If no nvidia driver installed my geforce 310M cuda is useless right?" 

Upon researching this nvidia optimus technology i stumble "Bumblebee" it suppose to switch you between intel and nvidia based on application you want to run. 
Does anyone using this Bumblebee and notice some HW effects on application using it, i tried it and see no difference from running in normal and using bumblebee "optirun <application>"
[]("https://www.google.com/search?hl=en&client=ubuntu&hs=RHe&pwst=1&channel=fs&sa=X&ei=We_AT5mVDcvwmAWI14DXCg&ved=0CAYQvwUoAA&q=nouveau+linux+driver&spell=1")

---

### Post by jao_madn on 2012-05-26
Ive solve temporary my objective which is " How to used my nvidia card in my laptop with optimus technology switching" I found this on the internet bumblebee and ironhide application, basically a program in which it will enable us to use our nvidia card on certain application i desired, I've tried bumblebee but not ironhide. the clue for solving optimus technology would be "bumblebee & ironhide" so its up to you to search and read in the internet,

Some referrence:
BumbleBee(support ubuntu. arch) and Ironhide (only ubuntu) are thesame
    "https://launchpad.net/~hybrid-graphics-linux" gruops working in hybrid card

Bumblebee Project Site 
    "http://bumblebee-project.org/index.html"

Bumblebee Wiki
    [https://github.com/Bumblebee-Project/Bumblebee/wiki/](https://github.com/Bumblebee-Project/Bumblebee/wiki/)

Bumblebee test site virtualgl
    [http://webglsamples.googlecode.com/hg/aquarium/aquarium.html](http://webglsamples.googlecode.com/hg/aquarium/aquarium.html)
    [http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/](http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/)

---

