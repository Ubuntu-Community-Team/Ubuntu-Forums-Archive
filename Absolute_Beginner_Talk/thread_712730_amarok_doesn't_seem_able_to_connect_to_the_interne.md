---
title: "amarok doesn't seem able to connect to the internet"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-03-02
I tried using amarok recently and I find that i'm unable to connect to the internet through 
ie. 1.)I'm not able to play streaming media from last.fm  
     2.)I'm not able to download album covers 
     3.)I'm not able to get lyrics using the LyricWiki script 
I'm behind a HTTP proxy .I configured Amarok for the HTTP poxy . 
The rest of the internet apps work fine but amarok doesn't .
When i run the LyricWiki script this is what i get 
> 
/usr/lib/ruby/1.8/net/http.rb:560:in `initialize'
/usr/lib/ruby/1.8/net/http.rb:560:in `open'
/usr/lib/ruby/1.8/net/http.rb:560:in `connect'
/usr/lib/ruby/1.8/timeout.rb:48:in `timeout'
/usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
/usr/lib/ruby/1.8/net/http.rb:560:in `connect'
/usr/lib/ruby/1.8/net/http.rb:553:in `do_start'
/usr/lib/ruby/1.8/net/http.rb:542:in `start'
/usr/lib/ruby/1.8/net/http.rb:1032:in `request'
/usr/lib/ruby/1.8/net/http.rb:945:in `request_get'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/utils/http.rb:108:in `fetch_page_get'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/wiki_lyrics.rb:179:in `login'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/wikipluginadapter.rb:58:in `submit_check'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/wikipluginadapter.rb:101:in `read_config'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/pluginsmanager.rb:244:in `read_config'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/pluginsmanager.rb:244:in `each'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/pluginsmanager.rb:244:in `read_config'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/pluginsmanager.rb:80:in `on_start'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsscript.rb:221:in `exec'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsscript.rb:219:in `initialize'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsscript.rb:219:in `new'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/amaroklyricsscript.rb:219:in `exec'
/home/arjayes/.kde/share/apps/amarok/scripts/wiki_lyrics/amarok/pluginsmanager.rb:269


and 

> 
Can't connect to the Internet (check your proxy settings)


---

