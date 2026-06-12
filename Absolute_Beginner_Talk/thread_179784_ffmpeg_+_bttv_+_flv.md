---
title: "ffmpeg + bttv + flv"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-05-20
I'm trying to get ffmpeg to convert live TV from a Hauppauge TV card to Macromedia Flash video FLV format for inclusion into a web page, but I cannot seem to get ffmpeg to convert it to _any_ form of video. I've compiled ffmpeg with all the codecs but ffserver cannot seem to do anything.

I'm tearing my hair out on this one, been a week so far so I'm in desperate need of help!!

---

### Post by Mustard on 2006-05-20
I use the lavrec command to make an avi recording of live TV on my Hauppauge card.  Would this help? Or have you already recorded stuff in some type of video format already?

---

### Post by adamkane on 2006-05-20
Use ffmpeg from the Takis repository:
[http://issaris.be/breezy/]("http://issaris.be/breezy/")

Are you using Dapper?

EDIT:
Due to unstability of the server that previously hosted the repository, Takis has moved the Ubuntu Breezy repository. The new line to add to your /etc/apt/sources.list would be:
deb [http://alpha.uhasselt.be/takis.issaris/breezy/]("http://alpha.uhasselt.be/takis.issaris/breezy/") ./

---

### Post by My-dial-up on 2006-05-21
What I'm after is displaying LIVE TV in a macromedia flash web page by using streaming FLV. But I need to convert the output 'on-the-fly' from the Hauupauge card from raw video to FLV format. ffmpeg is suppose to do this but I cannot get it to do anything other than jpegs.

---

### Post by adamkane on 2006-05-21
Hopefully you're not using the ffmpeg in the official repositories.

---

### Post by My-dial-up on 2006-05-22
No, I've tried compiling my own and using the one from [http://issaris.be/breezy/](http://issaris.be/breezy/). Both still don't work, the second asks for faac which isn't available as a package for Ubuntu.

---

### Post by adamkane on 2006-05-22
faac should be available. See:[U]
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)
[/U]

---

### Post by My-dial-up on 2006-05-23
Thankyou!!


It's amazing how one piece of information opens up a whole new area.

---

