---
title: "little help setting up dvd::rip"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-07-23
I just need to shrink a few dvds and burn them. I've been doing this with DVDshrink in Windows for the last couple months, but I still have a hard time understanding everything that is going on. I'm using Ubuntu Feisty with Gnome.

I looked at a howto on installing wine and dvdshrink, but I didn't understand all of it. So I tried using K9copy. I was able to begin my project, it began making an .iso, but it stopped after about 10 seconds and said it was finished. I looked at the .iso file and it was only about 1MB big. I figured it must be a conflict with Gnome(judging by the fact that most apps that start with k are designed for kde).

So, I moved on to dvd::rip and ran into a new set of problems. When it's started, it has you set up the preferences. The one that gave me trouble(and seems to give others trouble, though I can't seem to find a clear solution) is the rar command for vobsub compression. I'd found a thread where someone had the same problem, but they decided they didn't need subtitles and just said they would ignore it and everyone just left the thread at that.

However, in that thread, someone linked to this:
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)

I installed the medibuntu package before adding the "ubuntu restricted extras" package. Do I need to install the RAR archiver? I'd googled to this page and was following some of it, but I then found that it was intended for a latter version of Ubuntu:
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_033.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_033.html)

To simplify my questions:
1. Is there a conflict using k9copy with gnome? If not, why am I having problems?
2. If I can't use k9copy, does dvd::rip compress video to dvd format? I'm not looking to make avi's. I'm trying to compress dvd9s to dvd5s and burn them to disk so a standalone dvd player will recognize them.
3. If I'm better off using dvd::rip, how do I fix the rar command for vobsub compression?

---

### Post by ayenack on 2007-07-23
DVD Shrink is available for Ubuntu. Use [Automatix2]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2") to download and install it.

---

### Post by QwUo173Hy on 2007-07-23
You might want to search the forums about Automatix before you use it. Some have regretted it.

---

### Post by clinto on 2007-07-23
Thanks for the replies.

I tried k9copy again and encoded for about half an hour before it said it was finished. I looked at the .iso and it was 1.7GB this time.

I'm sure there is someone out there that uses k9copy with Ubuntu Feisty. If it's really just that buggy, then I'll need to try something else. I really wanted to get these burned today. Should I ask somewhere else other than in the beginners talk?

---

### Post by ayenack on 2007-07-23
If you don't want to use Automatix2 then you can go to this site and download [XDVDSHrink]("http://dvdshrink.sourceforge.net/").

Not sure if you know this but when setting up dvd::rip for the first time you should do it as root.

---

