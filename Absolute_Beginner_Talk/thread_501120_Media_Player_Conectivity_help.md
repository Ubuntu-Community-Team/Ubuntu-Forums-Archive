---
title: "Media Player Conectivity help"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by compennex on 2007-07-14
i installed Media Player Connectivity and then went to configure. Next i put the check mark for divX and typed in /usr/bin/gstreamer while not thinking instead of putting totem as the default player. I then tried to play a vid on stage 6. now i get an alert that says this

Unable to find the video player (check Tools menu, Media Player Connectivity...)
[CENTER]Alert[/CENTER]
Technical Informations
/usr/bin/gstreamer
[http://divx-350.vo.llnwd.net/stage6vid/1397910.divx](http://divx-350.vo.llnwd.net/stage6vid/1397910.divx)

%f


___________________
[Exception... "Component returned failure code:0x805200006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST) [nslLocalFile.lsFile]" nsresult:0x805200006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)" location: "JS frame::
chrome://mediaplayerconnectivity/content/mpc-overplay.js::mpc_executeApp::line873"
data: no]


So then i went to the configure and the line for DivX had disappeared. i tried unistalling and reinstalling MPC but it still isnt there. I have no idea where to go for the files i need to fix so if u can help me out that'd be great. Thanx in advance.

---

### Post by compennex on 2007-07-26
So i guess nobody has an idea about this. Can someone point me in the right direction on where to look for the MPC codes and whatnot?

---

### Post by marco123 on 2007-07-26
Make sure you have all the codecs installed first.  then install vlc player from the repos.

I've always used vlc with mediaplayerconnectivity and never had any problems.

---

