---
title: "Ubuntu Center - How do I find my music?"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2006-10-12
I got it working, and it's sweet, but how do I get it to point to where my music is stored?

When I go into the music category, nothings there, I want it to look for my music in /home/shared/Music/

How can I do this?

---

### Post by bruenig on 2006-10-12
Ok, more specifics are needed here. Are you using an app such as Rhythmbox and you are trying to get it to find and add your music to its library? That seems the most likely, so I will answer that.

When you get in rhythmbox go to Music>Import Folder and then navigate to that folder and click on it then click open and that should do it.

If this is not your question, please state the real question more clearly.

---

### Post by chris062689 on 2006-10-12
That's really weird, I said what appllication I was using, but it somehow got cut off.

I'm using Ubuntu Center.
What is it's default folder where it scans for music?

---

### Post by aysiu on 2006-10-13
According to [the Ubuntu Center website](https://hive.bountysource.com/wiki/Configuring_Ubuntu_Center): > **Music**
Put music in /home/Shared/Music. After putting your music in there goto the Ubuntu Center web interface and click Music from the Main Menu then from the Navbar goto Admin -> Catalog -> then add a new catalog in /home/Shared/Music and it will scan the specified directory for audio files. For more help with the music aspects of Ubuntu Center please see [http://www.ampache.org](http://www.ampache.org) The filesystem is case-sensitive

/home/Shared/Music is different from /home/shared/Music

---

