---
title: "Mythspeech - mythtv for blind/visually impaired"
date: 2012-12-22
forum: Assistive Technology &amp; Accessibility
---

### Post by faginbagin on 2012-12-22
I'd like to announce Mythspeech, which makes it easier for the blind and/or visually impaired to use MythTV, an open source DVR (digital video recorder).

Information about MythTV can be found here: [http://www.mythtv.org/]("http://www.mythtv.org/")
It is supported by Ubuntu and there is a Ubuntu based distribution customized specifically for MythTV, Mythbuntu: [URL="http://www.mythbuntu.org/"]http://www.mythbuntu.org/
[/URL]
More details about Mythspeech can be found here: [http://www.mythtv.org/wiki/MythSpeech]("http://www.mythtv.org/wiki/MythSpeech")

Mythspeech is not a perfect solution, but I'm told by one user:
"Maria is VERY happy with her talking MythTV, and it has made her life so much easier!"

How imperfect is the current implementation of mythspeech? One glaring example is that it cannot help with the initial setup and configuration of MythTV. I think you will need some vision or a friend or family member who can help with this step.

I would very much like to talk to developers with experience in accessibility. The current implementation of Mythspeech builds on MythTV's support for LCD displays and uses speech-dispatcher's API, but I'm thinking a better long term approach might be to implement Qt's accessibility classes. MythTV is a Qt application, but it does not use Qt widgets.

I would also like to know if there are interested users whose first language is not English. MythTV has been translated into many languages, and mythspeech should be able to speak in those languages, if they are supported by speech-dispatcher. But there are some things that could be improved if there is interest.

Of course, I welcome any and all feedback, bug reports, etc.

Regards,
Helen

---

