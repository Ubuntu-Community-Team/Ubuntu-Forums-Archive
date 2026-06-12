---
title: "RSS feed reader for rtorrent"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-07
Hello i need an RSS feed reader that will be able to look at a list and pick out witch torrents i like and than download the .torrents to a dir
Then the program i uses for downloading torrents will look in the dir and start any new torrents
On the rtorrent web site there is this but i couldn't get it to work
[http://libtorrent.rakshasa.no/wiki/UtilsRSSDler](http://libtorrent.rakshasa.no/wiki/UtilsRSSDler)
so could i have help with this 
or could you sejest a new rss feed reader/parsser that will be able to do what i would like thanks

P.S. sorry if this is a dupplict thred i just tried to make one and i dont know what happend

---

### Post by cornel_me on 2007-10-09
If you are willing to switch to deluge instead of rtorrent your problem is solved. Deluge has a RSS plugin that will let you do what you want.

---

### Post by haze42 on 2007-10-13
> **<<joe>> said:**
> Hello i need an RSS feed reader that will be able to look at a list and pick out witch torrents i like and than download the .torrents to a dir
Then the program i uses for downloading torrents will look in the dir and start any new torrents
On the rtorrent web site there is this but i couldn't get it to work

I was looking for the same thing, but couldnt find a working solution either.. so i hacked up a small java app. tonight that does just this.

[RTrss]("http://wartyard.com/dev/RTrss.jar")

Create a filter file like: 
Robin.Hood.*HDTV.XviD-BiA.*
.*PORNOLATiON
Womens.Murder.Club.S01E[0-9]*.HR.HDTV.*

(one filter per line, use regular expressions)

Start it with:
java -jar RTrss.jar [http://url.to.tracker.rss.xml](http://url.to.tracker.rss.xml) /path/to/filter/file /path/to/.torrent/download/dir

I'll add some more features when i have time, (maybe like auto-refresh of the filters before reading rss, configurable update interval etc..)

Unless RTorrent dev's decides to add this feature natively.. that would be better..

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-14
cool however i dont like java i think its slow but i will give this a try any way :) and i will look at deluge also
i really like native cli clients becuses of there low overhead witch is why i was using rtorrent

---

### Post by haze42 on 2007-10-15
> **<<joe>> said:**
> cool however i dont like java i think its slow but i will give this a try any way :) and i will look at deluge also
i really like native cli clients becuses of there low overhead witch is why i was using rtorrent

Me neither actually, but it's way better than a perl or tcl script that requires you install this and that and whatnot.. so simple to have it all in a single executable instead.

Just put up a new version with the changes i mentioned, same link as before :)
BTW, I just found this: [PHPnotify]("http://sharethefiles.com/forum/viewtopic.php?t=76704") which seem to do the same thing (so typical to find it when it's too late..)

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-17
thanks

---

### Post by hyper_ch on 2007-10-17
what is the problem with the UtilsRSSDler?
If you could tell, maybe someone can help you. Author of it is "lostnihilist" and he's quite often in the official rtorrent irc channel (I see him almost every evening [CET] in there).

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-23
I dont think its a problem with his code it's just the torrent site i was useing sucks 
the links in the rss feed link you to a web page and not to the torrent download link
the download link is in the web page though if this is normal then i gess i have a problem with 
UtilsRSSDler.
How ever i dont think it is normal i think that the site is just mest up 
have a look at it if you would though [http://linuxmafia.net/](http://linuxmafia.net/)

---

### Post by airtonix on 2007-11-09
should mention that rtorstats will help you expose rtorrent information, (basically a printout of what you see on screen) to a text file.

its default setup is to output to stdout. so i have my drupal site reading the results of the python script.

also....rtorrent has an xmlrpc api. an da prog...nTorrent is in the works to gui'fy a remote frontend for rTorrent

---

