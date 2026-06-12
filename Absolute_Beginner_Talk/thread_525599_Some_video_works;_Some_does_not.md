---
title: "Some video works; Some does not"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-08-14
Hello all,

I am pleased to announce that Ubuntu is a success at my house with both my wife and children. And the experience is getting better with the learning curve. But I do have a question I was hoping someone can help me with. I am able to watch most all video, including flash from youtube, but my wife likes to watch the video from one of our local television stations. Their URL is [www.wsmv.com](www.wsmv.com). Well, the commercial plays but it seems that the actual news story or weather story will not. Does anyone have any suggestions on how I can fix this for her?

Warm Regards,

Joe Hildreth

---

### Post by Alterax on 2007-08-14
In one word, codecs.  The station is using a proprietary codec that isn't (normally available outside of Windows).  Not to sweat, there is a workaround.

You need to install the codecs for what you are using.  Try searching for medibuntu and following the directions to add the codecs from it  (I think the site is [www.medibuntu.org](www.medibuntu.org) but if not, google medibuntu and you're bound to find it).  That's the quickest way, and it takes care of 95% of what you will need.

---

### Post by Hospadar on 2007-08-14
Well methinks the problem is that the videos are in wma and whatever mechanism they are using to make people watch the commercials doesn't play well with linux

If there is some way to get them sans commercials you might try that.  Also, you could look into other video viewers like [miro]("http://www.getmiro.com/").

I think since you can view the commercials, that you have the right codecs, but that might still be a problem, I'm not sure

---

### Post by philinux on 2007-08-14
> **wjhildreth said:**
> Hello all,

I am pleased to announce that Ubuntu is a success at my house with both my wife and children. And the experience is getting better with the learning curve. But I do have a question I was hoping someone can help me with. I am able to watch most all video, including flash from youtube, but my wife likes to watch the video from one of our local television stations. Their URL is [www.wsmv.com](www.wsmv.com). Well, the commercial plays but it seems that the actual news story or weather story will not. Does anyone have any suggestions on how I can fix this for her?

Warm Regards,

Joe Hildreth

Just watched the news story. I've got the mplayer plugin not totem. I had to get rid of totem plugin for it to work you need the win32 codecs.

---

### Post by wjhildreth on 2007-08-14
Hi folks,

Thanks for the suggestions. I already had the w32 codecs installed and if I added mplayer and removed the totem components but now it doesn't play anything. If I go back and add the totem-gstreamer and totem-mozilla all I see are the commercials before the actual clip. Does anyone have any other ideas that may help?

Best Regards,

Joe Hildreth

---

### Post by wjhildreth on 2007-08-14
Maybe I am a little slow. I installed the mplayer plugin for firefox and removed the totem-mozilla plugin. Now, the mplayer plugin tells me that it is connecting to where ever it needs to pull the video, shows the links and that it is connected then eventually tells me it is stopped, but no video. Is there something else I need to do?

Regards,

Joe

---

### Post by wjhildreth on 2007-08-14
OK, I am watching video now. I didn't realize that I had to configure the plugin.  Thanks for all your help.

Regards,

Joe

---

