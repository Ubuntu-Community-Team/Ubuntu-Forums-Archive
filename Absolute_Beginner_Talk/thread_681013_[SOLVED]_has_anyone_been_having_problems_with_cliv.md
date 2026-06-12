---
title: "[SOLVED] has anyone been having problems with clive (the youtube/googlevideo) extract"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2008-01-28
hello, i was wondering if anyone has been having this problem with the flash video extractor clive used for youtube and google videos. the extractor is working for google, but when  i use it to extract a youtube video, i get an error. i have included a snapshot of the terminal output if this helps.

---

### Post by forrestcupp on 2008-01-28
I haven't tried that, but if you can't get it to work, check out [this](http://vixy.net/) web site.  You just enter the url of the video and it converts it to a lot different kinds of formats, then downloads the video to your computer.  It's all web based.

---

### Post by thebestofall007 on 2008-01-30
i have tried vixy and it works somewhat, but it takes TWICE as long as what the command line option CLIVE does because you arent downloading the file directly off of the youtube server.

---

### Post by CupofDice on 2008-01-30
Just use [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") (also works for epiphany and opera) and download one of loads of youtube/google video scripts from userscripts.org. Don't worry, they will automatically install (except for epiphany and opera). When you view videos at youtube, there will be a link to download on the page. Just save as name.flv. There is also keepvid.com (I think they still have a firefox extension too).

---

### Post by thebestofall007 on 2008-02-02
> **CupofDice said:**
> Just use [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") (also works for epiphany and opera) and download one of loads of youtube/google video scripts from userscripts.org. Don't worry, they will automatically install (except for epiphany and opera). When you view videos at youtube, there will be a link to download on the page. Just save as name.flv. There is also keepvid.com (I think they still have a firefox extension too).

just got through trying that too, it works SOMEWHAT but i have a problem with some videos becoming very dark and pixellated to the point where i cant see it. maybe a snapshot will help. the snapshot shows a blank black screen, but when shown in real life it has the problem i mentioned.  I tried using different players, no go.

I WANT CLIVE BACK :mad:

---

### Post by thebestofall007 on 2008-02-10
i found the fix: first download the source file at 

[https://launchpad.net/ubuntu/hardy/+source/clive/0.4.3-1/+files/clive_0.4.3.orig.tar.gz](https://launchpad.net/ubuntu/hardy/+source/clive/0.4.3-1/+files/clive_0.4.3.orig.tar.gz)

input in the terminal sudo apt-get remove clive to uninstall the clive from the synaptics before doing anything else, the terminal may say to use "sudo apt-get autoremove to remove unused packages after "sudo apt-get removing" clive, but dont use the autoremove, you'll still need those packages.

once you have downloaded the file move it to the home folder (or whatever directory you would install from). next you right click on it and extract the file. next, in the terminal type cd then drag the extracted file into the terminal (leave the quotes). press enter, then type sudo python setup.py install.  the files from the "python setup.py" install and configure. next, go to the synaptic package manager and search for "url grabber". install the "python-urlgrabber"  package. you then should be able to download youtube and google videos. the Ubuntu 8.04 release will have this fix in itself (i have the alpha 4 version in virtualbox), but as of now i am using gutsy and oddly enough, this worked. i have included shapshots  of the terminal and the synaptic package manager if this helps. PLEASE FEEL FREE TO CLARIFY ANYTHING OR IF I HAVE MISSED SOMETHING (IM ALSO TALKING TO YOU FORUM STAFF)!

---

### Post by thebestofall007 on 2008-04-24
i also found another way. while the youtube or googlevideo site is loaded and playing a video, you can open the /tmp folder and get the cached file there. the video automatically loads there indicated by the red progress bar. when the video is completely loaded, the clock icon in the /tmp folder turns into a picture of the vid and drag it onto the desktop, or any other folder; the vid is in an flv format (despite the funky name :)). this also works with those "not suitable for minors" flagged videos that normally are not downloadable by clive, vixy.net, or greasemonkey. this method also works with googlevideo, myspace, metacafe, and any other site that loads audio/video into this folder!  just dont mess with anything else UNLESS you know what you are doing.  i have included an attachment if it helps. the picture in this snapshot is the video, for example, that you drag to the desktop, or wherever you want it to be.

---

### Post by steveking on 2008-06-10
YouTubeRobot.com today announces YouTube Robot 2.0, a tool that enables you to download video from YouTube.com onto your PC, convert it to various formats to watch it when you are on the road on mobile devices like mobile phone, iPod, iPhone, Pocket PC, PSP, or Zune.

YouTube Robot allows you to search for videos using keywords or browse video by category, author, channel, language, tags, etc. When you find something noteworthy, you can preview the video right in YouTube Robot and then download it onto the hard disk drive. The speed, at which you will be downloading, is very high: up to 5 times faster than other software when you download a single file and up to 4 times faster when you download multiple files at a time.

Manual download is not the only option with YouTube Robot. You may as well schedule the download and conversion tasks to be executed automatically, even when you are not around. Downloading is followed by conversion to the format of your choice and uploading videos to a mobile device (if needed). For example, you can plug in iPod, select the video, go to bed, and when you wake up next morning, your iPod will be ready to play new YouTube videos.

Product page: [http://www.youtuberobot.com](http://www.youtuberobot.com)
Direct download link: [http://www.youtuberobot.com/download/utuberobot.exe](http://www.youtuberobot.com/download/utuberobot.exe)
Company web-site: [http://www.youtuberobot.com](http://www.youtuberobot.com)

---

