---
title: "some website can't display"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by ketoophat on 2008-04-05
Hi, using ubuntu i'm facing problem that certain website can't display. to acces the website i'm using firefox.

For example, i'm tried to access [www.oum.edu.my](www.oum.edu.my). The main page display, but after finished enter user name and password, the website did't display anything. I have tried to acces this website using firefox at other PC (windows),the website display well. Only at ubuntu this issued occured.

Please help me.

---

### Post by Google Spider on 2008-04-05
Do you have flash and java ?


> sudo apt-get update
> sudo apt-get install ubuntu-restricted-extras

---

### Post by spiderbatdad on 2008-04-05
Hi. displayed fine for me...have you disabled java in your browser?
Edit>>preferences>>content...check the boxes. Also you probably need to accept cookies.Edit>>preferences>>security...accept cookies.

---

### Post by colonel1 on 2008-04-05
sounds like youneed to enable java

---

### Post by ketoophat on 2008-04-07
I have tried to do all advice, but problem still occurred. The page will stuck at [http://lms.oum.edu.my/main/default-frame.php?](http://lms.oum.edu.my/main/default-frame.php?) , the web page only display white background

---

### Post by scramasax on 2008-04-07
> **ketoophat said:**
> I have tried to do all advice, but problem still occurred. The page will stuck at [http://lms.oum.edu.my/main/default-frame.php?](http://lms.oum.edu.my/main/default-frame.php?) , the web page only display white background

There's a link there on the bottom left entitled " Login Problems".  it links to this page:

[http://www.oum.edu.my/portal/index.php?op=view&m=11&page=67](http://www.oum.edu.my/portal/index.php?op=view&m=11&page=67)

Did you try everything suggested there?  It could be "step 2: check your typing" ...

I don't find it hopeful that it says:

> Try using the latest version of Internet Explorer or FireFox as a web browser instead as these browsers have consistently delivered superior results.

In this context, "X and Y" have "consistently delivered superior results" is dishonest and *really* means:

> We didn't take the trouble to code our website to the published W3C standards for web languages, but wrote it on a "suck it and see" basis.  It'll work in IE all right ... but we did try Firefox, too, and that seemed to be OK.

But if Firefox on one platform works, then Firefox on another *should* -- providing you have JavaScript enabled and are accepting cookies, and so forth.

---

### Post by aimpau on 2008-04-07
Try increasing your cache size, enabling cookies, enabling java, flash, javascript. Also, make sure you've installed the necessary plugins.

---

### Post by ketoophat on 2008-04-13
I have done all instruction given, but problem no solved. For firefox, javascript and java has be enable. Also accept cookies. i'm also install IE in ubuntu, the situation also same, after enter username and passwod, the page not display. 

Only this site can't display, other like youtube, gmail,yahoo not facing this situation.

what else should i do? i need to use this website for my online learning.

---

### Post by jsjrod on 2008-04-13
> **ketoophat said:**
> I have done all instruction given, but problem no solved. For firefox, javascript and java has be enable. Also accept cookies. i'm also install IE in ubuntu, the situation also same, after enter username and passwod, the page not display. 

Only this site can't display, other like youtube, gmail,yahoo not facing this situation.

what else should i do? i need to use this website for my online learning.

In another forum I read that the firefox that came with ubuntu only has javascript 1.4 where the firefox you download from mozilla.com comes with javascript 1.5.  I am having the same problem with my online school.  Go to my school's browser checker and see what version of javascript that you have... <[COLOR="Blue"][click here]("http://tychousa11.umuc.edu/sys/browserinfo.html")[/COLOR]>  I am currently trying to install the downloaded version, but cant get it to install.  I'm not sure which file to run.  I tried running the "run-mozilla.sh" script, but it didn't work.  Hope that helps shed some light on the subject, if not sorry for wasting your time.

---

### Post by scor76 on 2008-04-15
You can fix this problem by referring to this thread
[http://ubuntuforums.org/showthread.php?p=4132456]("http://ubuntuforums.org/showthread.php?p=4132456")

---

### Post by chrisdugdale on 2008-04-15
I found that the Quickstart utility by mdpalow works to get everything working ok. I did it on a 32bit install and on a 64bit install. It even works on Ubuntu 8.04 beta, although I haven't checked out all the details and it may have a glitch or two that I don't know about. Makes Flash, Java, Etc work nicely. You can find it at [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) The directions are very precise and easy to follow. The source code is not available to check, so I suggest you carefully backup your data first. I didn't get any problems, but it needed a reboot and this is not mentioned.

---

