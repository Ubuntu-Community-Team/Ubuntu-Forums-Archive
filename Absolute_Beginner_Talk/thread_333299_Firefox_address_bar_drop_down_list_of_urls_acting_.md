---
title: "Firefox address bar drop down list of urls acting weird after update"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by amac777 on 2007-01-07
A few days ago I saw some updates go on for firefox. After that, at least I think this is when it started happening, I noticed that when I start typing a url in the Firefox address bar, it is refreshing the drop down list of urls twice after each keypress. Not really a big deal, but the problem is when I see the url I want on the list, if it's not at the top of the list, then when I press the down arrow, the drop down list refreshes using the top list url as the search again (so often only shows the url that was at the top of the list). So basically, the list is now useless. I can only select the one at the top because it refreshes each time and unselects the top one. So I need to press the down arrow again and then it happens again.

Anyone else having this problem? Should I just wait for another update and hope it gets fixed? Or is there a setting somewhere? 

Thanks for any help!

ps: In case it matters, "about firefox" reports Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.9) Gecko/20070102 Ubuntu/dapper-security Firefox/1.5.0.9

---

### Post by amac777 on 2007-01-11
finally found the problem. it was because i installed a newer version of GCIN (chinese input method). I went back to the old one available from apt-get and my firefox drop down menu problem went away.

---

### Post by tiwiniu on 2008-05-06
Hi, I have the same problem you described. I wonder which version of gcin you reverted back to solved that problem. Which version of ubuntu are you using?

Thanks.

---

### Post by tiwiniu on 2008-05-08
Apparently the gcin developers are aware of this problem. I have been taught a way to bypass that problem:
[http://hyperrate.com/topic-view-thread.php?tid=4589](http://hyperrate.com/topic-view-thread.php?tid=4589)

To use "popup" gcin window (I am not sure what that really means though), do the following:
1. open up the gcin-setup window
2. in &#22806;&#35264;&#35373;&#23450;, tick &#24392;&#20986;&#24335;&#36664;&#20837;&#35222;&#31383;
3. restart firefox to see if the problem has been fixed

---

