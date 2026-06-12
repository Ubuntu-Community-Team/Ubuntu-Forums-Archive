---
title: "Has BNN purposefully stopped linux?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by rexregum on 2007-08-22
I usually watch BNN videos in MPlayer.  But, as of last week, I get the following message:

[B]Sorry, your OS is not supported!
We recommend Windows 2000, Windows XP, or Mac OS X.
[/B]

Try it for yourself: [http://www.bnn.ca/shows/past_archive.tv](http://www.bnn.ca/shows/past_archive.tv)

I must stress that the files used to run under Ubuntu.  This problem only appeared last Friday.

I haven't made any changes to my system recently.

Therefore, my question is: Why did BNN stop supporting linux?

---

### Post by Majorix on 2007-08-22
If you read carefully, you can see that they blocked Vista too. So I believe their main goal was to do that. No idea why they broke their Linux support though...

---

### Post by kidcharles on 2007-08-22
If they didn't actually change anything with their player but just decided to block certain operating systems, you may be able to fool them. I think firefox (if that's the browser you are using) may be reporting that you are running linux. You might be able to change it so that it tells the world that you are using a different operating system. I don't know how to do this, but I suspect it is possible.

---

### Post by lightstream on 2007-08-22
Yeah, the only way they can determine which OS you are running is because your browser tells them, in the USER AGENT info.

There's an extension for FF which lets you change this User Agent info to whatever you like, I believe this is it: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

You'll need to get a user agent string for Win 2K or similar (although the extension may include some common strings), then you should be good to go! Would be interesting to hear if it works and you are able to view.

---

