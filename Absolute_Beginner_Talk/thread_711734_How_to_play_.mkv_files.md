---
title: "How to play .mkv files?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-02-29
It worked fine when using VLC on windows, but now only one of my 214 .mkv videos work. Any help?

---

### Post by iSplicer on 2008-03-01
I too, would like an answer to this question. Especially when there is HD x264 content inside

PLease help, thanks

---

### Post by kbless7 on 2008-03-01
What are the other videos doing? sound, video, anything? Doing a quick google you find many things about this. Just look around

---

### Post by crf on 2008-03-01
use a search engine.
click the links.
read the words.
then try what you've learned. :D
[http://www.matroska.org/technical/guides/playback/linux/index.html](http://www.matroska.org/technical/guides/playback/linux/index.html)

---

### Post by yamfox on 2008-03-01
Some of the other videos have sound but no video, some just give me a bright green screen. I really don't know what is wrong here. And, by the way crf, that was not very helpful.

---

### Post by herbster on 2008-03-01
Try Xine and Mplayer, see if they play the videos.

```
sudo apt-get install xine-ui mplayer
```

Launch VLC from console and paste output, as well as with these two if they don't cooperate either.

---

### Post by rfurman24 on 2008-03-01
Xine, Vlc, and Mplayer all work for me.

---

### Post by crf on 2008-03-02
> **yamfox said:**
> Some of the other videos have sound but no video, some just give me a bright green screen. I really don't know what is wrong here. And, by the way crf, that was not very helpful.


Then post everything you've read and tried already. I'm not a mindshrink, and I'm not looking over your shoulder.

---

### Post by uberlube on 2008-03-02
Did you install the restricted file format codecs? I believe they can be installed through the synaptic.

---

### Post by Mud.Knee.Havoc on 2008-03-06
> **crf said:**
> Then post everything you've read and tried already. I'm not a mindshrink, and I'm not looking over your shoulder.

Wow, two snide comments in one thread.  Honestly, the reply "use a search engine" and the related remarks are not at all helpful and are definitely not needed here.  I've been noticing that more and more people have attitudes like this lately at Ubuntu Forums... all it will do is drive people away.

---

### Post by Nythain on 2008-03-06
Ok, so back to trying to be a helpfull friendly community...
im not really sure what you've tried and havent tried but i did find this thread
[http://ubuntuforums.org/showthread.php?t=127563](http://ubuntuforums.org/showthread.php?t=127563)
and this thread
[http://ubuntuforums.org/showthread.php?p=4445997](http://ubuntuforums.org/showthread.php?p=4445997)
wich might contain some helpfull information

hope ya get it goin

---

### Post by crf on 2008-03-08
{Sarcasm Honestly Off} Click here and read ===> [matroska green screen search]("http://www.google.ca/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=uok&q=matroska+green+screen&btnG=Search&meta=");
{Sarcasm Honestly On} but, of course, do not click on any link from the domain matroska.org;
 
===
> **Mud.Knee.Havoc said:**
> Wow, two snide comments in one thread.  Honestly, the reply "use a search engine" and the related remarks are not at all helpful and are definitely not needed here.  I've been noticing that more and more people have attitudes like this lately at Ubuntu Forums... all it will do is drive people away.

The first comment wasn't snide at all, to my mind. I wasn't meaning to be sarcastic. Perhaps it is hard to adequately capture emotional nuance, but yamfox honestly misread whatever nuance was there. There is an entire site dedicated to Matroska. Why the heck shouldn't anyone try there first? I thought it might be honestly helpful.

I was being a little sarcastic in my second comment though, with good reason. I didn't think it was that big a deal, but I'm sorry anyway.

But the literal claim was that absolutely nothing at the Matroska site, or any other top links in a search about the problem, did anything to help. That claim is of course unlikely meant to be taken literally. But if it is honestly claimed that nothing helps after trying with other entries that might pop up in a search about the problem, how is it really snide to ask what has actually been done to attempt to solve the problem? It would be ironic if the problem were understood and solved in this thread, after much effort on behalf of many, and the solution were also in fact there on that Matroska site, or in some other top rated link. 

Mud.Knee.Havoc, fight your own battles. You are not helping. You don't speak for Yamfox. You shouldn't take his misreading of my attitude and tone and elevate that into an example of a truth that fits into some theory of yours. This post of yours is just a petty insult.  He doesn't need and hasn't asked for the kind of nauseating world-weary advocacy you're offering. Nobody does. Don't you worry that Yamfox, and others, will now either feel embarrassed or stupid about providing information about what they've done in attempting to solve problems, because  the people asking for that information are publicly penalized by being slotted into your "snide attitude" box?

---

### Post by crjackson on 2008-03-08
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

