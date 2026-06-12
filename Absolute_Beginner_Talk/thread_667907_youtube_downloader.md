---
title: "youtube downloader"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2008-01-14
i have installed youtube-dl and when i download it saves in a particular location. can anyone tell me how to change the download location?

---

### Post by benanzo on 2008-01-14
by default youtube-dl will save the video to the current working directory.  You can either change to the dir you want to save the video in before running:

```
cd /home/user/Videos
```
```
youtube-dl http://www.youtube.com/url-to-video
```

or you can use the **-o** switch to specify the location and filename

```
youtube-dl -o /home/user/Videos/YoutubeVideo.flv http://www.youtube.com/url-to-video
```

---

