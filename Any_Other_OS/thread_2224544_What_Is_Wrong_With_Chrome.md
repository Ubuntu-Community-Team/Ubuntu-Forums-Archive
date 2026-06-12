---
title: "What Is Wrong With Chrome?"
date: 2014-05-16
forum: Any Other OS
---

### Post by Smallwheels on 2014-05-16
I'm using a variant of Ubuntu 12.04 LTS with the Firefox and Chrome browsers. Chrome has the pepper Flash plug-in so I can watch videos. On Youtube many videos when loaded, especially embedded ones on other web sites, will give me error messages and won't play videos. To get them to play I have to play them in Firefox. Another problem is that I can't comment on videos at Youtube using Chrome. Even though I'm signed in it is impossible for me to post a comment. 

When I put the cursor on the comment box it is displaying the finger icon which means it is treating the comment box as a link. When I click inside the box to post a comment I get a pop-up window that takes me to this address:
[https://plus.google.com/u/0/wm/4/up/?type=st&client=7&gpsrc=gpfw0&parent=https%3A%2F%2Fapis.google.com&proxy=I1_1400276218760&wlbsl=1&rsz=1&hl=en_US](https://plus.google.com/u/0/wm/4/up/?type=st&client=7&gpsrc=gpfw0&parent=https%3A%2F%2Fapis.google.com&proxy=I1_1400276218760&wlbsl=1&rsz=1&hl=en_US)

This is a Google+ window that remains blank. It disappears very quickly but I still can't post a comment after it disappears. It took a while for me to capture that address before the pop-up page disappeared. 

Is anybody else experiencing this? Does anybody have a clue about why this would be happening? 

The Firefox browser being used is the latest version which I don't really like anymore. It won't play some videos on Yahoo so I switched to Chrome. *It* will play videos on Yahoo with the pepper Flash plug-in. Chrome on the other hand won't play certain videos on Youtube. This must be a GNU/Linux problem because I can't imagine the Chrome browser not having full functionality on a Google owned web site. Are these just the pitfalls of using GNU/Linux? The web is changing all of the time and it seems that GNU/Linux is getting the short end of the stick or perhaps no stick at all. I'm still annoyed that I can't use GoToMeeting.com as a viewer because Citrix won't support my operating system. Maybe I should just break down and buy some form of Android tablet. Those seem to be supported everywhere. What do you think?

---

### Post by monkeybrain20122 on 2014-05-16
Close Chrome. Open the file manager, press ctrl h or choose show hidden files in the menu. Locate the hidden folder .config, open it to find the sub-folder google-chrome. Rename it to something else like google-chrome-bak, then start Chrome and see if you still experience the same problems. If not then it is because your profile is corrupt, just delete .config/google-chrome-bak. This will delete all your settings and bookmarks, so you may want to save the bookmarks first.

---

### Post by vasa1 on 2014-05-16
> **Smallwheels said:**
> I'm using a **variant** of Ubuntu 12.04 LTS ... What do you think?
Maybe you should contact whoever made the variant. Who knows what the variation is.

---

### Post by Smallwheels on 2014-05-17
Monkeybrain20122 will Chrome create a new folder as soon as I rename the original Chrome folder?

---

### Post by monkeybrain20122 on 2014-05-17
> **Smallwheels said:**
> Monkeybrain20122 will Chrome create a new folder as soon as I rename the original Chrome folder?

Yes, that is the point.

---

### Post by Smallwheels on 2014-05-17
Vasa1 the version is Elementary. They aren't very communicative. In another post about finding a lighter distribution to better suit my 2009 computer it has been suggested to me to try LXLE. It looks good but the file size is gigantic at 1.3 GB to download. That doesn't sound very lightweight. Elementary is much smaller. Even so, I might try it on a USB thumb drive. Maybe it will work better. The menu controls look like Ubuntu 10.04 LTS. I really liked that one a. Since the 14.04 version of LXLE is yet to come I might have to wait a while. I don't think it would benefit me to spend a week switching to it and then in another couple of months have to start over.

---

### Post by Elfy on 2014-05-17
*Thread moved to **Other OS/Distro Support**.*

---

### Post by robbie 348 on 2014-05-17
I just tried lxle and while I didn't like it that much it is extremely light when installed, only around 90mbs.

---

