---
title: "How to get &quot;suspend&quot; in Xu 12.04 on PM 3,1 w/ATI Rage card???"
date: 2015-11-03
forum: Apple Hardware Users
---

### Post by este.el.paz on 2015-11-03
> The rage 128 has a section of its own in the FAQ, have you actually  looked at that?  Yes it doesn't say anything about suspend, but it'll  help you with what you need to google (but I've no idea if suspend is  possible, particularly on a desktop machine). 


Folks:

Other thread got cut off before it could resolve my issue I was having as the OP . . . so, yes, I looked at the FAQ . . . and, as mentioned, it doesn't say anything for or against "suspend" . . . for the ATI Rage card.  Although the word "radeon" seems to be showing up in the info section for that computer as well . . . .  I will continue to endeavor to persevere on the "suspend" issue . . . .  The ToriOS DE makes the "old" computer more or less "viable" on the modern web . . . only thing holding it back is the lack of "suspend" . . . .  Any insights on how to resolve that problem are welcomed here . . . .  : - )))

e.e.p.

---

### Post by este.el.paz on 2015-11-07
Bump-ah . . . I would also be interested in getting some direction on how to upgrade the 12.04 system with the trusty kernel stack . . . I have googled and looked through PPCFAQ and have not seen any detailed instructions on how to do that process.  I was able to use synaptic to install "linux headers" from trusty, but the "linux-image" for 3.13 does not show up . . . not sure if I need to add something via PPA or whether I can just download the image .deb and install it via GDebi???  Any thoughts, besides what are you doing in linux, would be appreciated . . . .

e.e.p.

[Edit:  Got my answer off-forum for how to upgrade kernel from J?rn  S . . . I'll test this out later . . . > ```
 sudo apt-get install linux-generic-lts-trusty
    >
    > If you want the complete graphics/driver stack including Xorg     and Mesa:
    >
      sudo apt-get install --install-recommends
      linux-generic-lts-trusty linux-image-generic-lts-trusty
      linux-headers-generic-lts-trusty xserver-xorg-lts-trusty
        libgl1-mesa-glx-lts-trusty libgles2-mesa-lts-trusty


```

[Edit:2]:  It's looking like this data will not work for PPC . . . .

---

