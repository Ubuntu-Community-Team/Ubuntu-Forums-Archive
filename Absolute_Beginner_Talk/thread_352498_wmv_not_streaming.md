---
title: "wmv not streaming"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Mystere on 2007-02-03
okay so firefox just doesn't pick up some embedded wmv files. but others which I was told were identical format work fine. the output for a correctly opened file is as such:

jared@kjaredc:~$ firefox
checking to see if we need to make a button
n->url=http://animecrave.net/site/_content/multimedia/anime_episodes/hack_sign/hack%201.asx?ac555666sphr&code=4rxecKZNSFrFMeaZaRwq9Svi&nowcode=Z83iF0a81uAPKC4GDJIAHCUkJAQ
url=http://animecrave.net/site/_content/multimedia/anime_episodes/hack_sign/hack 1.asx?ac555666sphr&code=4rxecKZNSFrFMeaZaRwq9Svi&nowcode=Z83iF0a81uAPKC4GDJIAHCUkJAQ
href=(null)
checking to see if we need to make a button
n->url=http://animecrave.net/site/ac.wmv?url=ac555666sphr&code=4rxecKZNSFrFMeaZaRwq9Svi&nowcode=Z83iF0a81uAPKC4GDJIAHCUkJAQ
url=http://animecrave.net/site/_content/multimedia/anime_episodes/hack_sign/hack 1.asx?ac555666sphr&code=4rxecKZNSFrFMeaZaRwq9Svi&nowcode=Z83iF0a81uAPKC4GDJIAHCUkJAQ
href=(null)

but on other ones I don't get anything. any ideas?
(I'm using mplayer)

---

### Post by Mystere on 2007-02-03
*bump* no ideas?

---

### Post by Mystere on 2007-02-03
*bump* so just to make sure nobody has anything, right?

---

### Post by Mystere on 2007-02-15
This is really starting to drive me crazy. they should be the same thing, the files that work are all roughly 180 mb files, and the ones that don't work are varied sizes, most smaller some larger. that's the only difference I can think of...

---

### Post by Mystere on 2007-02-18
Okay I think I've got something. The files that work look like this:

<script type="text/javascript"><!--
function song(){
document.getElementById('music1').innerHTML="<embed type='application/x-mplayer2' id='music2' pluginspage='http://www.microsoft.com/Windows/MediaPlayer/' src='"+document.getElementById('cancion').value+"' name='MediaPlayer1' width='300' height='75' controltype='2' showcontrols='1' showstatusbar='1' AutoStart='true'></embed>";
}
//-->
</script>
<div id="jukebox"> 
<span id="music1">
  <embed type="application/x-mplayer2" id="music1" pluginspage="http://www.microsoft.com/Windows/MediaPlayer/" src="blah_blah.asx" name="MediaPlayer1" controltype="2" showcontrols="1" showstatusbar="1" autostart="1" height="500" width="690">
</span>
</div>

and the ones that don't look like this:

<object id="Player" classid="CLSID:6BF52A52-394A-11d3-B153-00C04F79FAA6" align="middle" height="500" width="690">
  <param name="autoStart" value="True">
  <param name="URL" value="blah_blah.asx?blahsphr&amp;code=F6AYmD3zQFkoEF2Py6Bqvw&amp;nowcode=hQXegOCfAsOGNraayBl6                  "></object>

I'm not good with html anymore but could anybody help me on why the first type might work and the second wouldn't be detected by Mplayer?

---

