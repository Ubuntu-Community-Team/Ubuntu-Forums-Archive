---
title: "real or windows media player plugins for opera"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by rhb on 2006-12-31
Are there plugins for Opera that allow playing streaming realplayer or windows media player content?  If not, are there workarounds, such as for the xmms player?  The latter may not work in all cases, because of restrictions in the way streaming is done, I believe.

I can always use Firefox instead.  I usually assume that whatever works on FF will also work on Opera, but it might be easier to get something up on FF, which would be more standard ubuntu.

Thanks a lot for any suggestions.

---

### Post by itsjustarumour on 2007-01-02
Are you using Edgy 6.10? You should be able to stream Realplayer content OK in Opera by installing the Realplayer plugin from the Ubuntu non-OSS software repository.  Give this a try and let us know what happens... if you already have this version of Realplayer installed, what happens when you try and view content?  Which sites are you looking at?

---

### Post by cbahimsa on 2007-01-02
Check and install Automatix2 from getautomatix.com.

---

### Post by rhb on 2007-01-08
I am using ubuntu 6.06.

I tried the realplayer install, it mentions that it guides you through getting it from the real website.  I got the message:

realplayer:
 Depends: xlibs  but it is not installable

Maybe that solution works only on 6.10?

I tried installing the automatix2 script.  I had trouble downloading it, probably temporary.  Here's the message I got after waiting 30 sec or so and clicking cancel:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.4-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.4-6.06dapper_i386.deb)
 
On the third try, it gave me a message without waiting:

W: Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.4-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.4-6.06dapper_i386.deb)
  301 Moved Permanently

So I will wait for more information, or else move this to my 'to-do' list when I decide to upgrade to 6.10.

Thanks for the information.  I would like to be able to handle both real and windows media as a plugin, but I am not entirely thrilled about having their software on my machine.

---

### Post by crimesaucer on 2007-01-12
I have the same qusetion and would like to not use automatix2 for anything. I had everything working perfectly in Firefox 2.0 without automatix2, and I figure that there should be a way to play embedded media in Opera 9.10.

My Java and Falsh work fine so far, it's just windows media that I would like to play on my xine or any other media player (vlc, mplayer, gxine). In Firefox the media player plug-in used to do the trick.

---

### Post by obsidion on 2007-01-12
> **crimesaucer said:**
> I have the same qusetion and would like to not use automatix2 for anything. I had everything working perfectly in Firefox 2.0 without automatix2, and I figure that there should be a way to play embedded media in Opera 9.10.

My Java and Falsh work fine so far, it's just windows media that I would like to play on my xine or any other media player (vlc, mplayer, gxine). In Firefox the media player plug-in used to do the trick.


  If it is all working in firefox then it should work in opera as well, though it may open real player rather than embedded. Make sure the plugin directory in opera does point to firefox. I found that it works better with symlinks rather than hard links, so pointing it at the firefox/plugin directory is better than the mozilla one.

---

### Post by crimesaucer on 2007-01-12
Well the java and flash are working, and I didn't have the mplayer or vlc plugins for mozilla because I used xine with the media player connectivety plug-in, so I don't know it that would work, but I just installed mplayer with the mozilla plug in so I'll see if that works.

(I'm really missing the Firefox spellcheck right now)

---

### Post by obsidion on 2007-01-12
> **crimesaucer said:**
> Well the java and flash are working, and I didn't have the mplayer or vlc plugins for mozilla because I used xine with the media player connectivety plug-in, so I don't know it that would work, but I just installed mplayer with the mozilla plug in so I'll see if that works.

(I'm really missing the Firefox spellcheck right now)


  There are plenty of threads and answers on the ubuntu support page about getting plugins going. The thing to remember with opera is that it tends to point at both mozilla and firefox for plugins, this can cause some conflicts esp if these directories have different versions of the same plugins. I have removed the link to the mozilla one in my opera and just point to the firefoxplugins directory and found I have not had any plugin grizzles since.

---

### Post by crimesaucer on 2007-01-13
Just to help anyone with the same problem for Embedded media, this is what worked for me:

go to synaptic and install the mozilla plugger and mplayer.

I prefer xine and have it set for targeted media links, but for the actual embedded media, only mplayer works for me.

Then for java:

go to Opera's,

Preferences-->--Advanced-->--Content-->--Java Options 

and (for pc) make the path /usr/lib/j2re1.5-sun/lib/i386/

and then check validation.

also make sure you have everything that you want enabled in Tools-->--Quick Preferences.

---

