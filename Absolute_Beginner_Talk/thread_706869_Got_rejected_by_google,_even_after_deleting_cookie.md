---
title: "Got rejected by google, even after deleting cookies"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-24
Hi,

it started about a week ago with google rejecting my search request with the following text,

    We're sorry...

    ... but your query looks similar to automated requests from a computer virus or spyware application. To protect our users, we can't process your request right now.

    We'll restore your access as quickly as possible, so try again soon. In the meantime, if you suspect that your computer or network has been infected, you might want to run a virus checker or spyware remover to make sure that your systems are free of viruses and other spurious software.

    If you're continually receiving this error, you may be able to resolve the problem by deleting your Google cookie and revisiting Google. For browser-specific instructions, please consult your browser's online support center.



I was still able to do a search once i confirmed my "human-ness" by entering a text.
 Now i actually deleted the google cookie and it rejects me totally, meaning i can't prove my human-ness any more.

I use fire fox.

So what do you think, do I have a virus or how did i come to be banned? How can i resolve this issue?

Thanks for your answers...
Andreas

---

### Post by jordanmthomas on 2008-02-24
Are you using tor or some sort of proxy perhaps?
Also, are you searching for things that may look fishy to google?

Try deleting all your cookies if they're not valuable (ie, do you remember your usernames and such?)

If you deleted your cookie, a new one should be made, so they've likely banned your IP if you don't get a chance to prove you aren't a robot.  (just a guess, don't freak out, I am most probably wrong)

---

### Post by JoshuaRL on 2008-02-24
Wow.  So are there any options for contacting them?  And if not, could you contact your ISP to see if anyone else is having the same problem?  It seems they're blocking you from the IP address if cleaning cookies didn't work.

---

### Post by ru7hl3ss on 2008-02-24
This exact same thing happened to me, and it stopped yesterday. Why? I don't know--I didn't do anything different except once I went to the main Google page instead of using the search bar in FF. Started happening to me about a week ago also... interesting.

---

### Post by alanhaggai on 2008-02-24
Have you edited the User Agent in Firefox? Check if it is correct or not. You can check it by entering: ```
about:config
``` in the location bar. Then enter a search query for `agent'.

Is it any addon that is changing the User Agent? Try disabling addons and try again. Hope this helps.

---

### Post by Djalmahal on 2008-02-24
All right, after one hour i already got 4-5 answers, love ubuntuforums...

The about:config didin't show any agent when i searched it, i gues that's good (?)

And yes i did try out some proxy server (JAP) as i was interested after having read articles about it, but after one day of trying it out i reset the settings back to direct connection. I believe that was a while before problems started.

I'm not putting anything fishy in the searches...

Yes, I am Deluge, does that matter to Google?

I would prefer not to delete all the cookies, as it would make the whole surfing on the Internet a bit more complicated, for now I just use another search engine.

OK, BUT WHAT ABOUT THE VIRUS/ADWARE issue that google mentions, nobody of you mentioned any of that, i know they generally say that there is no real virus threat on linux, but if i understand correctly they can be programmed. Any thoughts?

Thanks guys
Andreas

---

### Post by JoshuaRL on 2008-02-24
Okay, for viruses I think that we all discarded that right away.  There are much less than 100 Linux viruses/worms in total existence.  And all of those are either no longer relevant, patched out of existence years ago, or never made it out in the wild anyway.  It really just says that for Windows machines.  You really don't need to worry about it.

---

### Post by seventhc on 2008-02-24
I think if it was a virus/adware issue then there would be a lot more people posting about the same problem, so while that isn't a guarantee I think it is highly unlikely that it is the issue. I think it would be something different, finding out might be difficult, but worth finding out. I've never been blocked before.
Have you tried using a different browser? Probably won't matter but just to be certain, I would probably try it in another browser.

---

### Post by seventhc on 2008-02-24
from wikipedia
> 
**Error messages**

 Some searches will give a 403 Forbidden error with the text[INDENT] "We're sorry... ... but your query looks similar to automated requests from a computer virus or spyware application. To protect our users, we can't process your request right now. We'll restore your access as quickly as possible, so try again soon. In the meantime, if you suspect that your computer or network has been infected, you might want to run a virus checker or spyware remover to make sure that your systems are free of viruses and other spurious software. We apologize for the inconvenience, and hope we'll see you again on Google."
 [/INDENT]followed by a [CAPTCHA]("http://en.wikipedia.org/wiki/CAPTCHA") prompt.[[5]]("http://en.wikipedia.org/wiki/Google_search#_note-3")
 The screen was first reported in 2005, and was a response to the heavy use of Google by [search engine optimisation]("http://en.wikipedia.org/wiki/Search_engine_optimisation") companies to check on ranks of sites they were optimising. The message may also be triggered by high volumes of different searches from a single IP address. The block is removed after a day.[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*]
 
 **[[edit]("http://en.wikipedia.org/w/index.php?title=Google_Search&action=edit&section=11")]**If your getting the captcha you should be able to type in the text and it would allow you to use it again.
You should post a screenshot.

---

### Post by Djalmahal on 2008-02-24
So, same thing with Opera browser.

Ok, i now learned that it is called a CAPTCHA, as i said before, initially it did give me his CAPTCHA message, then it didn't, now it sometimes does.

Interesting that it should get removed after a day, sometimes i am not being asked, sometimes i am being asked the CAPTCHA text, even though i am not seaching more than 20-30 items a day.

---

### Post by seventhc on 2008-02-24
the only info I've found so far has already been mentioned here. I don't think 20-30 searches would cause it...I do that and more.
heres what I've seen so far though, quoted from 2 different peple.
> Hm... It appears that I was getting the message because my useragent 
 was set to the googlebot useragent. (I was testing out a system on my 
 website where it displays a crawl-optimized page if the google crawler 
 visits). It still seems sort of silly for you to use the user agent as 
 a criterion for determining if the traffic is legitimate, as I'm sure 
 that most illegitimate software uses fake user agents.
> I  have this same problem sometimes.  It's because I use an anonymous 
 proxy server.  This might also be a problem if you use a non-anonymous 
 proxy server, but I have no experience with that.  If I connect 
 directly to the internet, I stop getting the messages.  Most of the 
 time I don't have a problem even with the proxy server.  I'm not sure 
 what triggers google to start delivering these messages.  But they are 
 totally annoying and pointless. 

---

### Post by seventhc on 2008-02-24
I would clear everything, cookies, cache, etc. close firefox, restart it and try again.

---

### Post by steveneddy on 2008-02-24
Where are you accessing the internet from?

It may look at IP addresses from certain countries more than others.

Just a thought.

---

### Post by Djalmahal on 2008-02-24
Ok, i'm accessing it from Oregon. One more thng, i actually use a wireless range extender, but that could hardly cause it..

Anyway, i think we can leave it here after multiple people told me it wouldn't be a virus/adware issue, that was the main point of starting this thread, i just use another search engine for a while and try google out in a week or so, it's really not such a big deal.

Thanks for taking your time
Andreas

---

### Post by Crafty Kisses on 2008-02-24
I'm thinking it must be a proxy issue, but this has never happened to me before. Werid. Post a screenshot maybe.

---

### Post by Djalmahal on 2008-02-24
So, now also the Yahoo search engine is blocking me, i checked, firefox is connecting direct to the internet, so does that rule out the proxy possibility?

Anyway, tomorrow is Monday, i'll call my ISP and see what he can say about this. There is also some unusual fluctuations in the bandwidth, sometimes the connection just goes down to B/s instead of the usual 40 something KB/s

You know, why I also asked about Viruss before, as I am typing this the computer is lagging behind, it takes about 1 sec for the text to appear  on the screen, and I am not running many programs at this point, just like a windows computer after a year.  But I goes that's a different story. 

Andreas

---

### Post by JoshuaRL on 2008-02-25
Not to be insulting or anything, but I just want to be sure of the basics.

Are you running Ubuntu?

---

### Post by Djalmahal on 2008-02-25
Yes, I am running Ubuntu 7.10, just 2 days ago I got the last update

---

### Post by JoshuaRL on 2008-02-25
Okay, are you running wireless, especially unsecured?

---

### Post by Djalmahal on 2008-02-25
No, its WEP encrypted, living in a  rural area where there is 3 houses in sight.

---

### Post by sloggerkhan on 2008-02-25
do you host remote access for an ssh account or anything like that?

---

### Post by Djalmahal on 2008-02-25
I don't know what you're talking about, so if it takes extra measure to do this "ssh acount" i'll say definitly no

---

