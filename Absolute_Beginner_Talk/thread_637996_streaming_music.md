---
title: "streaming music"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-12-11
I am not talking about amarok or whatever to stream music. My problem lies in more of a player. 

Basically, I want to stream the live music of [www.z100.com](www.z100.com). When I click on the listen live button I go to the page that has the player for me but the stream never loads from there. I just says stopped. 

how do i get it to stream for me,

thanks:guitar:

---

### Post by mcduck on 2007-12-11
I tried it, and it seems that there's something wrong with the flash applet on the first page.

Instead of that, use ZMusic/Listen Live from the menu. That seems to work, but I can't confirm it as I'm not living in US and it because of that the site refuses to let me any further than this.

edit: I just read your post again and understood that you actually got as far as the player. The site says that even on a mac they require you to use Windows Media Player so it could be that they are using some kind of DRM on their stream and because of that you can't play it on any other player.

---

### Post by Whiffle on 2007-12-11
Works fine over here, using slackware + kaffeine + konqueror 

I'm looking at the code of the page right now, i might be able to find a way to make it easy.  I'll post back if i do..

---

### Post by Whiffle on 2007-12-11
Well, I think your problem is that mplayerplugin or whatever your plugin you've got isn't setup correctly.  I don't know why.

But, i did find this little script on the interwebs that opens up the stream in mplayer:
```


#!/bin/sh
 ASX=$(wget -U "Mozilla/5.0" http://www.z100.com/cc-common/streaming_new/?refreshed=yes -qO - |sed -r '/.*<PARAM NAME="URL" VALUE="(.*?)">.*/!d;s//\1/')
 MMS=$(wget -U "Mozilla/5.0" $ASX -qO - |sed -r '/.*<REF HREF="([^&]+).*/!d;s//\1/' |head -1)
 gmplayer -user-agent "Windows-Media-Player/10.00.00.3646" $MMS

```

All it has to be done is saved to a file of your choice (like music.sh), and then chmod +x it, and then run it (./music.sh).  Or, you can make an icon for it somewhere with ". /path/to/music.sh" as the command.  Weeeee...

In fact, it seems to work with any clearchannel station, just change the url.

---

### Post by moose4204l on 2007-12-11
thanks man, i got it to work through the mplayer with the music.sh thing you said to do . I appreciate it alot.

---

