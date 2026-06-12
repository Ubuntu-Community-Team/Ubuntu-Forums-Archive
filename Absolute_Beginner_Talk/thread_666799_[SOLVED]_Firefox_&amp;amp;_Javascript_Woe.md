---
title: "[SOLVED] Firefox &amp;amp; Javascript Woe"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2008-01-13
Hello All,

Hopefully this is not a major problem, but whenever I click a Javascript pop-up or similar Firefox just shuts down. For example selecting to watch a video, instead of a pop-up screen the browser just dies, here is what I am trying to look at: [http://www.buell.com/en_uk/mania/videos.asp](http://www.buell.com/en_uk/mania/videos.asp)

Any advice would be great and I can give you any more detail on request (just tell me what you need)

Best regards

P.S. I realise that this may not be an Ubuntu problem and apologise if inappropriate!

---

### Post by nikoPSK on 2008-01-13
> **victor9098 said:**
> P.S. I realise that this may not be an Ubuntu problem and apologise if inappropriate!

It's a related ubuntu problem, it's fine, the forums here incorporate more than just the ubuntu OS! :)

nikoPSK

---

### Post by kostkon on 2008-01-13
> **victor9098 said:**
> Hello All,

Hopefully this is not a major problem, but whenever I click a Javascript pop-up or similar Firefox just shuts down. For example selecting to watch a video, instead of a pop-up screen the browser just dies, here is what I am trying to look at: [http://www.buell.com/en_uk/mania/videos.asp](http://www.buell.com/en_uk/mania/videos.asp)

Any advice would be great and I can give you any more detail on request (just tell me what you need)

Best regards

P.S. I realise that this may not be an Ubuntu problem and apologise if inappropriate!

The first thing you could do is to run *Firefox* from the terminal, visit the site in question and then post here any output that will be generated before (if any) and after the crash.

---

### Post by victor9098 on 2008-01-13
Hi,

Thank you for the replies!

I did what you asked and opened firefox via the terminal. Navigated to the page, clicked the link and the video opened first time!

Then I closed firefox. Started by clicking the icon, went to the page and it crashed again!

Does this mean I need to open firefox via terminal for it to be stable? I repeated opening via terminal and it worked perfect again.

This was the output while running in terminal:
loaded md5.js
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception

Any thoughts?

Thanks again!

---

### Post by victor9098 on 2008-01-13
OK, finally got it to crash with terminal open, I know I should not sound so happy but at least it gives you guys something to work with!

Here is the output from terminal:

keith@keith-vaio:~$ firefox
loaded md5.js
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
Segmentation fault (core dumped)

It means nothing to me, but hopefully it does to you.

Thanks again.

---

### Post by victor9098 on 2008-01-14
I don't know but the problem is really getting annoying.

I was just on [http://news.bbc.co.uk/2/hi/middle_east/7188121.stm](http://news.bbc.co.uk/2/hi/middle_east/7188121.stm) I clicked the 'add to facebook' link at the bottom of the article and firefox crashed again.

I ran firefox via terminal. Repeated what I did and the same happened. Here is the output:

keith@keith-vaio:~$ firefox
loaded md5.js
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
Segmentation fault (core dumped)

Any suggestions would be great. I guess the first obvious one is to uninstall Firefox then reinstall. 

Thanks again

---

### Post by jmclaug on 2008-01-14
My first stab at an answer - so ....
Do you have the right software loaded . ie 32 bit verses 64 bit?

---

### Post by victor9098 on 2008-01-15
Truth be told I am not sure!!!

But I have reinstalled. Did what I did in the previous post and it worked first time!

This has only started happening over the last 2 weeks. I have not installed any new add-ons or similar. Unless an update has affected it, but I am sure there would have been many more similar posts.

After 6 months of using Ubuntu and Firefox nothing like this has happened!!

Thank you for the reply

---

### Post by victor9098 on 2008-01-24
Right, been almost a week now.

I completely removed Firefox (purged) then rebooted. The installed Firefox again and the problem does not seem to have returned.

Wish I knew what started it originally as I have not heard of or seen this before. Hopefully this is solved then.

---

