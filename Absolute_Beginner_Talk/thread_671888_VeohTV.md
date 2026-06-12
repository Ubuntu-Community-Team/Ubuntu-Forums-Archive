---
title: "VeohTV"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by lilBeat on 2008-01-19
Hi!


I like watching videos on [www.veoh.com](www.veoh.com). On Linux you have a problem, you can watch just a preview of videos and taht is 5 minutes. You need their program called VeohTV which is Windows based application. I tried to install it through Wine, but it gives me an error to check Internet Explorer and if it works correctly. I installed Firefox for Windows through Wine as I thought that second install of VeohTV for Windows after installing a browser will make it run. It shows the same error. This is a part and conclusion that I hate MANY WINDOWS APPS ARE BASED ON INETERNET EXPLORER.

For example Yahoo Messinger for Windows  can't run without Internet Explorer.


I am thinking if there is no way to make a petition to www,veoh.com to make an application for us. We always are forgotten somehow. I wrote an private message to CEO of Veoh company and hope to get any reply. 

As an example of good practice I metioned that Last.fm, has application for many Linux distros, and that it is very spread through-out Linux community.

I hope we are heard as we are getting bigger, there are more and more Linux users day by day.


If anyone knows how to watch full length videos on [www.veoh.com](www.veoh.com), please help.


All the best,
Ivan

---

### Post by Presto123 on 2008-01-19
I can actually watch whole episodes. Since it is running Flash player, maybe you should try reinstalling it. I would suggest doing it directly from the site and removing any flash plugins in add/remove.

---

### Post by Presto123 on 2008-01-19
Did this help? Or are you still having issues?

---

### Post by oni5115 on 2008-03-21
At least for me, with flash player installed I seem to be able to watch most videos.  It seems to be limited though, after about 10-15 minutes it usually exits full screen mode automatically.  (I can easily set it back to full screen, but it is annoying).  I've read in some video comments that this can be cured by using VeohTV [which gives me the same error as the OP].

Also, certain videos only show a 5 minute preview.  I'm not totally certain, but I am guessing that it's any video over 30 minutes.   e.g. most anime episodes are <25 minutes and work perfectly, but a double episode, does not work.  Not sure if you have to be a member logged in, or if you need to use VeohTV to get around this as well.

In either case, VeohTV doesn't work for me at all.  Only using the website to view videos does, and with the limitations noted above.

---

### Post by billgoldberg on 2008-03-21
I  never got veoh tv installed.

But did you know veoh can access your harddrive and delete the videos you downloaded at their will?

**They remove** copyrighted videos **from your harddrive** !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I gave them the finger and use other video sites now.

---

### Post by oni5115 on 2008-03-22
Not to be too off-topic, but since you mentioned other video sites I am curious what good ones there are?  I really only know of Veoh and Youtube, but youtube is annoying since all the shows seem to be cut into 4-8 parts.

---

### Post by billgoldberg on 2008-03-22
You might try megavideo or blip.tv. 

You mention tv shows.

You can just download those, no need for veoh.

---

### Post by SneakyBooBoo on 2008-03-24
there was a way to get VeohTV running on linux in Wine. I managed to do it, but the interface was pretty messed up. i couldnt see the buttons for all the functions so i was stuck with the library screen. i installed firefox for windows in Wine but i couldnt use it to open videos from sites because it said my VeohTV was outdated :( even worse, i could click the download to veohtv link, and the download would load into veohtv, but it wouldnt download. i think they might have worked out that method too. so i guess all hope is lost until they make veohtv for linux  ](*,)

theres a mac version, why not a linux one :confused:

---

### Post by petit_prince on 2008-04-07
There's a tool which supports the new protocol they appear to use, check out my post at
[http://ubuntuforums.org/showpost.php?p=4669727&postcount=9]("http://ubuntuforums.org/showpost.php?p=4669727&postcount=9")

---

### Post by Alpinist on 2008-04-08
OK, I tried to install the VeohDownloader.  Wine first told me I needed to install mono. Did that. Then I run 'wine VeohDownloader' and it comes up in a 9210 X 1619 sized window. I can't do a thing with it.  Any reason it would come up in a window so big it is impossible to do anything with it?

---

### Post by SneakyBooBoo on 2008-04-09
did u install firefox for windows with wine before installing VeohTV?

Also, configure your wine to run a desktop of at least 800x600 so your VeohTV doesnt do its own thing on your desktop. Thats what i did and it worked.

take a look at this post, it might help
[http://ubuntuforums.org/showthread.php?t=519189&highlight=VeohTV]("http://ubuntuforums.org/showthread.php?t=519189&highlight=VeohTV")

---

### Post by SunnyRabbiera on 2008-04-09
well there is supposed to be a open source version of veoh soon, veoh had no issues with people creating forks.

---

### Post by SneakyBooBoo on 2008-04-09
i think i do remember seeing something about an open source version. Another good one to have would be TVU. I think they actually do have an open source version already but its only for broadcasting and not watching online streams.

---

### Post by petit_prince on 2008-04-10
> **Alpinist said:**
> OK, I tried to install the VeohDownloader.  Wine first told me I needed to install mono. Did that. Then I run 'wine VeohDownloader' and it comes up in a 9210 X 1619 sized window. I can't do a thing with it.  Any reason it would come up in a window so big it is impossible to do anything with it?

Alpinist, you don't need wine to run the VeohDownloader from [http://www.assembla.com/spaces/files/bwEUBC9pCr3indabIlDkbG]("http://www.assembla.com/spaces/files/bwEUBC9pCr3indabIlDkbG").  I guess you need the mono-runtime package installed, which was already installed on my system (maybe by default). Just run
```
./VeohDownload
```
and it should work.

---

### Post by MasterJS on 2008-04-10
If episodes of your favorite shows exist on the Veoh website, they probably exist all over the internet. I would recommend trying to find another site instead of Veoh. It might take a while, but you usually end up find good sites. If its anime that you like watching, there are thousands of fan sites with the episodes on them.

---

### Post by hughesjr on 2008-05-04
As someone already stated, you do not need wine, just mono runtime.  I do not use Ubuntu but on CentOS once I have mono installed, I just do this to run the downloader:

mono VehoDownload

Then, I find the item I want and get the link to the play the five minute preview ... the link would contain a number on the end after the last slash) ... for example:

<rest_of_url>/v1244171MZXPX4SJ

If you paste in that number into the downloader, it will download a file that is the item (in most cases, it is a wmv file).

You would then open the file with mplayer or something else that can play wmv files and view the full item.

---

### Post by yssida on 2008-05-04
I would also suggest tvshack.com.

It searches multiple sites for tv episodes.

---

### Post by Zapotek on 2008-05-15
You can try this: [http://ubuntuforums.org/showthread.php?t=795255&highlight=veoh](http://ubuntuforums.org/showthread.php?t=795255&highlight=veoh)

I published it today and it has been working fine for me for the last 2 days.
Should anyone find a bug please inform me.

---

