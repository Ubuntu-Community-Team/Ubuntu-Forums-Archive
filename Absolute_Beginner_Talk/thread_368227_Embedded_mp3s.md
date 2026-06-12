---
title: "Embedded mp3s"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-02-23
:guitar: On my MySpace page I have a simple player console set up to play some of my original music when the page opens. It works fine with IE7, but when I open the page with Firefox I just have 2 little dots where the console should be and no sound. Is this a matter of needing plugins for Firefox or what? Helpful suggestions requested.

---

### Post by orb9220 on 2007-02-23
Do you have flash 9 for linux installed.
Is the imbedded player in my space flash based?

---

### Post by paydaydaddy on 2007-02-23
> **orb9220 said:**
> Do you have flash 9 for linux installed.
Is the imbedded player in my space flash based?

It is not flash based. It is a simple html code player set up to play a single song when the page opens. I just change the song ever so often. The page URL is:

[http://www.myspace.com/texanmccabe](http://www.myspace.com/texanmccabe)

Maybe somebody could chime in and say whether or not it works for them in Firefox. I use Dapper Drake.

---

### Post by orb9220 on 2007-02-23
I didn't hear it either. If you post what the code looks like here I might figure it out. I have a  blog so know a little of the html stuff.

And Hi ya from Portland,Or. Just south of Ya!

---

### Post by paydaydaddy on 2007-02-23
Here is the code for the player:

 <object type="application/x-mplayer2" classid="6BF52A52-394A-11d3-B153-00C04F79FAA6" height="45" width="280">
  <param name="fileName" value="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" />
  <param name="URL" value="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" />
  <param name="src" value="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" />
  <param name="allownetworking" value="internal" />
  <param name="allowScriptAccess" value="never" />
  <param name="enableJSURL" value="false" />
  <param name="enableHREF" value="false" />
  <param name="saveEmbedTags" value="true" />
</object>

Hello back to ya! How's the weather in Portland?

---

### Post by orb9220 on 2007-02-23
"application/x-mplayer2" 
is being used. In synaptic there is a mplayer for firefox that might work. Not sure maybe someone web guru like can Help. > Hint! Cough! Hint!

And it is a bit on coolish overcast just like I like it.

---

### Post by orb9220 on 2007-02-23
Googled application/x-mplayer2

[http://www.google.com/search?q=application%2Fx-mplayer2&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=application%2Fx-mplayer2&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by paydaydaddy on 2007-02-23
I took a look through the googled info but didn't find anything that really gave me an answer. I'm wondering if an alternate html code is needed to make it work in Firefox.

---

### Post by xyz on 2007-02-23
Wish I could help...but I don't get it...a bit off base this morning!
Should the song start automatically? If not, where should I click to hear it?
Thnx.

---

### Post by paydaydaddy on 2007-02-23
The song should start automatically when the page loads. When viewed with IE you get a small console where you can pause, rewind, control volume, or replay. I'm just guessing that there may be firefox plugins that make it work, but it make take a completely different html code to make it work. For all I know firefox may not stream audio the way that I have it set up for IE. I could post a link on the page for the non-IE people (very few I'm guessing) but consider that a last resort.

---

### Post by chewearn on 2007-02-23
To check your installed Firefox plugin, type this into the address bar:
```
about:plugins
```

Did you see an entry for mp3, or mplayer2?  In my system I have the following:

"application/x-mplayer2" under Windows Media Player Plug-in 10 (compatible; Totem), but which associate to avi
"audio/mpeg' under Totem Web Browser Plugin 2.16.2, which associate to mp3.

My guess is to then change to <object type="audio/mpeg" ..>
But, you must already be able to playback mp3 in totem (codec not installed by default).

Also, you might break IE instead; in which case, thing will get complicated, because you would then need to add browser detection codes.

---

### Post by paydaydaddy on 2007-02-23
I have mplayer listed as mp3 player. I'm off to bed. I'll work on this some more later. Thanks for the input.

---

### Post by paydaydaddy on 2007-02-24
I'm revisitng this thread and bumping it up looking for an answer. I know that in actual practice this subject is pretty much moot as 99.999% of people who visit my page will be using IE, but still, inquiring minds want to know. In firefox, I if I go to the site where the songfile is stored and click on the link, mplayer opens and plays which leads me to believe that the solution is in knowing the correct way to enter the tag so that when the page opens the browser will detect and open the correct player and play the file. At the risk of being flogged for cross-posting I also asked about this in the programming section of the forum, but traffic is quite low over there so I thought I would try here again. Any clues?

---

### Post by chewearn on 2007-02-24
Ok, I'll bite.

After some tinkering, I found this to work with my Firefox in ubuntu:
```
<embed src="song.mp3" height="32" width="280" />
```

I checked this code in my other machine with IE6/WinXP; seems to work as well.

An excellent reference here:
[http://www.w3schools.com/media/media_browsersounds.asp](http://www.w3schools.com/media/media_browsersounds.asp)

---

### Post by paydaydaddy on 2007-02-24
> **AstalaVista said:**
> Ok, I'll bite.

After some tinkering, I found this to work with my Firefox in ubuntu:
```
<embed src="song.mp3" height="32" width="280" />
```

I checked this code in my other machine with IE6/WinXP; seems to work as well.

An excellent reference here:
[http://www.w3schools.com/media/media_browsersounds.asp](http://www.w3schools.com/media/media_browsersounds.asp)

I'm curious how you used the code you posted. I did some tinkering with it and could not get it to display or load anything. Could you be more specific or provide an example that I could cut and paste into an editor to see how it works?

---

### Post by chewearn on 2007-02-25
To make sure it really works online, I used the w3schools website feature called "Tryit Editor" to test out the html code snippets.  Here is the html code I used (apologized for using your mp3, but I just want to make sure it really works):

```
<html>
<body>
<embed src="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" width="50%" height="10%" />
</body>
</html>
```

See the attached screenshot of my Firefox for the result.

---

