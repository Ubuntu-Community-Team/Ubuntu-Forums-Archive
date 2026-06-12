---
title: "Can't get signed on to dsl account"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by flash on 2005-10-12
I recently installed ubuntu on a spare computer and I want to use it on my dsl connection. So far I created a sub acct. on my windows computer(I have 2 windows connected so far) but when I go to log on to sbcglobal acct., it takes me to sbc.prodigy and says I can't log on. The network connection seems to be working OK and of course sbc was of no help when I told them I had a linux machine I wanted to use. Is there some kind of internet connection wizard that I should be going through? Anybody got any ideas?

---

### Post by SilentCacophony on 2005-10-12
Hi. That's a bit unclear, but I'll have a go at it.

I gather that you have SBC Yahoo! DSL.

You have one computer with Windows installed, set up for two accounts with SBC, and you wish to network another computer with Linux installed?

Sounds like you have the networking ok.

If you're using the SBC internet software package that came with the service, it kind of abstracts how things really work by having you log in before you can connect to the internet, then sending you straight to Yahoo!

If you do use that, you cannot use it in linux (and you really don't need to use it in Windows either.) Your modem should already have the pppoe user : password set up, so ubuntu should simply autodetect the connection through DHCP. Then, you just use the internet 'normally', rather than through SBC's specialized browser. You can still log in to Yahoo through thier normal web login.

BTW - I use SBC Yahoo! DSL, and that's how I connected. No problem with autodetection.

---

### Post by flash on 2005-10-12
So your saying that all I have to do is open the browser on the linix machine and I'm all signed in on my acct.? That's probably what's already happened. When I tried it, I could go to sbc, ubuntu help, and a coulpe of other things, but I couldn't understand how I could be on the internet without signing in.  So on the email program, when I open that up and set up the acct., that will all work also? Am I going to be able to log on on the linux as a different user like I can on the 2 windows machines?

---

### Post by SilentCacophony on 2005-10-12
Yes, it should work just fine if you set up another user in linux, as well. The logging in part of sbcyahoo's software isn't really necessary; it's just the way *they* made it. Without that software installed, when you want to access your sbcyahoo account online, just go to [http://sbc.yahoo.com/](http://sbc.yahoo.com/) and log in, but you can still go anywhere else on the WWW with or without doing that.

For email, you can either use the web-based email on the sbcyahoo site through your browser, or you can look up the correct pop and smtp addresses in the sbcyahoo FAQs, and set up Evolution to use it. You can use either method or both. Try [this]("http://help.sbcglobal.net/article.php?item=287") link, if you want to look up the pop and smtp servers to set up an Email Client with.

If you hadn't installed thier software on Windows, you still could have used the internet in quite the same way as you will in linux, but it would have been more difficult to set up initially. In fact, I have thier service, and have never used thier software suite.

---

### Post by flash on 2005-10-12
OK, things are clearing up now. Yes I have been online since I last posted and indeed I was on the internet. I realize that the sbc software is just a bunch of flash. But I understand that if you don't use it, a bunch of the features they have don't work. ie. parential controls (which I need). I should just start posting from the other machine instead of running back and forth. Well thanks for your help, getting that machine on the internet was the first big hurdle in the land of ubuntu.

---

### Post by SilentCacophony on 2005-10-12
Ah. I don't know much about Parental Controls on linux, but I think it's possible. I ran a site-specific google search on this site, and saw a lot of topics. You may want to check them out:

[Link]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+parental+controls&btnG=Google+Search")

Good luck, and have fun. :)

---

### Post by Qrk on 2005-10-12
You can still have parental controls in Ubuntu. Make a user for your kids (without giving them "wheel" status). To do this got to System-->Administration-->Users and Groups
Now your kids will have their own "account" like on Windows XP. 

From there you can install firefox extensions (like BlockXXX) to safeguard against adult content. But like any controls they will probably be able to break through them, lets face it, Kids are smarter than adults and have a lot more time on their hands.

---

